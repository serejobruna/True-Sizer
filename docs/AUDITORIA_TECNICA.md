# TrueSizer — Auditoria Técnica e Backlog

## Escopo e método

Auditoria estática do ZIP `truesizer_codebase.zip` enviado para revisão, com 105 entradas de arquivo e aproximadamente 761 KB descompactados. Foram inspecionados manifestos, README, documentação de banco e algoritmo, componentes de câmera, processamento de pose, calculadora de tamanhos, rotas e camada de armazenamento.

Esta etapa **não executou a aplicação**, não validou a conexão com serviços externos e não mediu a precisão do algoritmo com um conjunto de dados. Portanto, os achados abaixo descrevem o que o código declara ou implementa, não uma validação de funcionamento em produção.

## Distinção de escopo

### Proposta acadêmica
A documentação anterior descreve uma arquitetura pretendida mais ampla, incluindo diferentes serviços e ferramentas de dados. Essa proposta deve continuar identificada como arquitetura conceitual/acadêmica, salvo comprovação independente de implementação.

### Código-fonte recebido
O ZIP contém uma aplicação web com React 18, TypeScript, Vite, Tailwind/shadcn, servidor Node.js/Express e uma camada de processamento de pose com TensorFlow.js e MoveNet. Também há código de persistência Oracle e artefatos de Drizzle/PostgreSQL.

A presença de dependências ou arquivos de integração não comprova que todos os serviços estejam configurados ou operacionais.

## Achados técnicos da inspeção estática

### 1. Frontend e jornada
O código contém páginas para home, permissão de câmera, instruções, medição por câmera, medição manual, resultados e recomendações de roupas. O estado de medidas é mantido com Zustand; chamadas HTTP são feitas por React Query.

### 2. Visão computacional
`client/src/lib/pose-detection.ts` inicializa TensorFlow.js com MoveNet SinglePose Lightning e estima pontos-chave corporais. O processamento de pose ocorre no navegador, a partir do elemento de vídeo.

**Limitação crítica:** a detecção de pose não equivale a uma medição antropométrica validada. O código usa relações geométricas e multiplicadores aproximados para inferir circunferências a partir de larguras em pixels. Há referência a uma altura presumida de 170 cm e calibrações fixas; parte dos cálculos usa conversões fixas de 100 pixels para 40 cm. Não há evidência no ZIP de calibração individual, profundidade 3D, validação com fita métrica ou estudo de erro. Assim, as medidas devem ser descritas como estimativas experimentais, não como medidas exatas.

### 3. Fluxo de captura e confiabilidade
Em `camera-feed.tsx`, a rotina de captura chama `estimatePoses` e, em seguida, chama `estimateMeasurements`, que executa outra inferência de pose para o mesmo ciclo. O intervalo assíncrono pode iniciar uma nova execução antes da anterior terminar. O fluxo também contém um encerramento temporizado e registra `detectionConfidence: 0.85` e `scanDuration: 5000` como valores fixos no payload de persistência. Esses campos não representam, portanto, métricas efetivamente calculadas no código inspecionado.

A rotina de salvamento usa o estado `measurements` capturado pelo componente, que pode não refletir a atualização mais recente do ciclo de medição. O progresso, a conclusão e a persistência precisam de testes e correções antes de qualquer alegação de confiabilidade.

### 4. Recomendação de tamanhos
`shared/size-calculator.ts` contém tabelas de faixas e regras determinísticas para tamanhos e dicas de caimento. Não foi encontrada evidência de um modelo de IA generativa ou de recomendação treinado. A descrição correta é algoritmo baseado em regras/tabelas, sujeito à validação das tabelas e das regras por marca.

### 5. Persistência e configuração de banco
O ZIP contém `server/oracle-db.ts`, `server/oracle-storage.ts` e uma exportação de `OracleStorage` em `server/storage.ts`. Também contém `server/db.ts` e `drizzle.config.ts` configurados para PostgreSQL via `DATABASE_URL`. Essa coexistência exige esclarecer qual backend de banco é realmente usado e remover a configuração não utilizada ou documentar sua função.

### 6. Segurança — bloqueador P0
Foi encontrada credencial Oracle hardcoded em `server/oracle-db.ts` e repetida em `ORACLE_DATABASE.md`. Não publicar esses valores. Antes de qualquer publicação do código:
- revogar/rotacionar a credencial no serviço Oracle, caso ainda esteja ativa;
- substituir valores literais por variáveis de ambiente;
- revisar todo o histórico Git, pois remover do arquivo atual não apaga o segredo de commits anteriores;
- verificar outros arquivos e artefatos por credenciais, dados pessoais e arquivos de configuração;
- adicionar `.gitignore` e um `.env.example` sem valores reais.

### 7. Privacidade e analytics
O frontend inicializa Google Analytics 4 e envia eventos de navegação e eventos relacionados ao fluxo de medição. O código inspecionado envia faixas de medidas nos eventos de analytics e envia medidas corporais, informações do navegador e do dispositivo às rotas de persistência. Não foi identificada, nessa inspeção específica, uma chamada que envie a imagem/vídeo bruto da câmera ao servidor; a inferência de pose é feita no cliente. Isso não basta para afirmar que o produto é integralmente “seguro e privado”: é necessário documentar retenção, finalidade, consentimento, acesso, exclusão e configuração de analytics, além de testar a aplicação implantada.

### 8. Qualidade e reprodutibilidade
Não foi encontrado `.gitignore` no ZIP. O README atual descreve algumas integrações como fatos, mas a coexistência de Oracle e PostgreSQL e as limitações do estimador pedem uma descrição mais precisa. Os scripts incluem `dev`, `build`, `start` e `check`; a execução e o build ainda precisam ser testados em ambiente limpo com dependências e variáveis adequadas.

## Backlog atualizado

### P0 — antes de publicar o código
- [ ] Revogar/rotacionar a credencial Oracle exposta.
- [ ] Remover a credencial de `server/oracle-db.ts` e `ORACLE_DATABASE.md`; usar variáveis de ambiente.
- [ ] Inspecionar o histórico Git para segredos já commitados.
- [ ] Adicionar `.gitignore` e `.env.example`.
- [ ] Decidir e documentar se o protótipo usa Oracle ou PostgreSQL; alinhar a inicialização e a camada de armazenamento.
- [ ] Executar auditoria de dados pessoais, imagens, logs e configurações.

### P1 — antes de apresentar como protótipo técnico
- [ ] Rodar instalação, `npm run check` e `npm run build` em ambiente limpo.
- [ ] Corrigir o fluxo de captura: evitar inferências duplicadas e intervalos concorrentes.
- [ ] Corrigir persistência para usar as medidas mais recentes.
- [ ] Não apresentar confiança e duração fixas como métricas reais.
- [ ] Validar as estimativas contra medidas de referência e documentar erro; até lá, rotular como experimentais.
- [ ] Testar permissões, recusa/indisponibilidade da câmera e alternativa manual.
- [ ] Validar faixas de tamanho e recomendações por marca.
- [ ] Rever consentimento, analytics, retenção e exclusão de dados.

### P2 — fortalecimento do case de produto
- [ ] Incluir evidências do problema e público-alvo, sem inventar pesquisa que não foi realizada.
- [ ] Explicar jornada, decisões de UX e trade-offs.
- [ ] Registrar prompts representativos e iterações reais no Replit.
- [ ] Separar claramente contribuição individual em UX/produto, contribuição coletiva de UX e geração de código assistida por IA.
- [ ] Definir hipótese e métricas para um experimento futuro (por exemplo, taxa de acerto de tamanho, confiança na recomendação e intenção de troca/devolução).

## Como descrever o projeto no portfólio neste momento

**TrueSizer — protótipo experimental de experiência de recomendação de tamanhos.** Projeto acadêmico desenvolvido com apoio de ferramentas de IA e prototipação no Replit. A experiência explora uma jornada de medição corporal por câmera, alternativa de entrada manual e recomendações baseadas em tabelas e regras. A estimativa por visão computacional ainda não tem precisão antropométrica validada e não deve ser apresentada como medição exata ou solução pronta para produção.

## Critério de pronto para portfólio

É possível apresentar o case como **projeto acadêmico de UX e produto com protótipo experimental**, desde que autoria, escopo e limitações estejam explícitos. A publicação do código deve aguardar a resolução dos bloqueadores P0. Para apresentá-lo como implementação técnica funcional, ainda são necessários testes reproduzíveis, correções do fluxo de captura, configuração segura e validação das estimativas.
