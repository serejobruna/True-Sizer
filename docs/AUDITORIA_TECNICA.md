# TrueSizer — Auditoria Técnica e Backlog

## Escopo da auditoria

A revisão inicial do repositório encontrou um README com descrição de uma arquitetura acadêmica ampla. O repositório consultado tem tamanho muito pequeno e, nesta etapa, ainda não contém evidência suficiente para afirmar que o código do protótipo está publicado de forma completa e reproduzível.

A demonstração em vídeo e as telas do protótipo são evidências da experiência visual e dos fluxos apresentados, mas não comprovam isoladamente a implementação interna de todos os componentes descritos na arquitetura acadêmica.

## Distinção necessária

### Proposta descrita no trabalho acadêmico
A apresentação final descreve uma arquitetura pretendida que inclui interfaces web/mobile, backend Node.js, bancos MongoDB e SQL Server, processamento em Python, IBM Watson Studio, Watson Machine Learning, feedback e visualização com Power BI.

### Protótipo demonstrado
A apresentação registra que o mockup foi construído no Replit. As telas e o vídeo mostram um fluxo de interface para câmera, instruções, medição e recomendações.

**Não afirmar que toda a arquitetura acadêmica foi implementada ou integrada ao protótipo sem evidência verificável no código e em testes.**

## Riscos e verificações pendentes

- [ ] Confirmar que o código-fonte correto do protótipo está neste repositório.
- [ ] Comparar o conteúdo do repositório com o ZIP original do projeto.
- [ ] Identificar framework, bibliotecas e serviços realmente utilizados.
- [ ] Adicionar instruções de instalação e execução reproduzíveis.
- [ ] Remover chaves, tokens, senhas, arquivos .env e dados pessoais.
- [ ] Verificar se há imagens, vídeos ou dados de usuários no histórico do Git.
- [ ] Revisar dependências e licenças de terceiros.
- [ ] Testar o fluxo em desktop e mobile.
- [ ] Testar permissões, recusa e indisponibilidade da câmera.
- [ ] Testar alternativa de inserção manual, se disponível no código.
- [ ] Verificar se as medidas exibidas são estimativas demonstrativas ou resultados calculados por implementação real.
- [ ] Documentar limitações e casos de falha.

## Backlog recomendado

### P0 — Antes de divulgar o repositório
- [ ] Publicar o código correto, após auditoria.
- [ ] Garantir README coerente com o que está efetivamente implementado.
- [ ] Remover segredos e dados pessoais.
- [ ] Incluir instruções de execução e status do protótipo.

### P1 — Para fortalecer o case
- [ ] Adicionar capturas de tela sem dados pessoais.
- [ ] Documentar fluxo de usuário e decisões de UX.
- [ ] Registrar prompts representativos e como foram refinados, se disponíveis.
- [ ] Explicar quais partes foram geradas/alteradas com apoio de IA e quais decisões foram humanas.
- [ ] Criar roteiro de teste de usabilidade.

### P2 — Evolução do produto
- [ ] Validar precisão de medição.
- [ ] Construir base confiável de medidas por marca e modelagem.
- [ ] Definir método de recomendação e avaliar sua qualidade.
- [ ] Planejar experimento para medir impacto em devoluções.

## Critério de pronto para portfólio

O projeto pode ser apresentado como **case de UX e produto com protótipo experimental** desde que autoria, escopo e limitações estejam claros. Para apresentá-lo como implementação técnica funcional, é necessário publicar e validar o código real, com instruções de execução e evidências dos componentes implementados.
