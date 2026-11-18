# TrueSizer
### UX & Product Design | Recomendação de tamanhos para e-commerce de moda

**Um experimento de produto para tornar a escolha de tamanhos de roupas online mais clara e confiante.**

[**🚀 Experimentar TrueSizer V2**](https://truesizerv2.replit.app/) · [**Ver protótipo original**](https://serejobruna.github.io/True-Sizer/prototipo/) · [**Ler case de UX e produto**](docs/CASE_DE_PRODUTO_UX.md)

**Visão geral:** projeto acadêmico do Enterprise Challenge IBM + FIAP, com exploração de experiência do usuário, definição de funcionalidades e fluxos, e prototipação com apoio de ferramentas de IA. O protótipo é experimental: as medidas corporais e recomendações de tamanho não foram validadas para uso comercial.

**Foco do case:** descoberta do problema · jornada do usuário · fluxos de medição · prototipação · limites e hipóteses a testar

## TrueSizer V2 — evolução com IA assistindo o desenvolvimento

A **V2** é uma evolução mais refinada e experimental do TrueSizer, desenvolvida posteriormente com **Replit e desenvolvimento assistido por IA**, a partir do protótipo de UX/UI no Figma. O trabalho explora a transformação de requisitos de produto em uma aplicação mobile-first, com experiência também em desktop, jornada de medição corporal, recomendação de tamanhos e fluxos de consentimento e conta.

**[Acessar o aplicativo TrueSizer V2](https://truesizerv2.replit.app/)** · [**Conhecer a documentação da evolução V2**](https://github.com/serejobruna/True-Sizer/blob/feature/truesizer-v2-replit/docs/TRUESIZER_V2_REPLIT.md)

**Meu papel na V2:** condução da evolução de produto, definição de requisitos e experiência, orientação da implementação por prompts e avaliação crítica da solução gerada por IA. A versão acadêmica original mantém os créditos coletivos registrados abaixo.

**Status:** protótipo funcional experimental; a precisão das medidas, a efetividade das recomendações e os fluxos de privacidade/autenticação ainda precisam de validação ponta a ponta. O uso de IA no desenvolvimento não significa que a funcionalidade de medição utilize IA generativa.

## O problema

Comprar roupas online limita a possibilidade de experimentar uma peça e avaliar tecido, caimento e ajuste. A apresentação acadêmica do projeto analisou dados de devoluções fornecidos no desafio e identificou que:
- pouco mais de 53% das devoluções analisadas estavam associadas a compras online;
- o erro de tamanho aparecia como um motivo relevante de devolução;
- o recorte por gênero e faixa etária ajudou a orientar a definição inicial do público-alvo.

Esses números pertencem à análise do material acadêmico do desafio. Não devem ser interpretados como estatísticas universais do mercado.

## Proposta de produto

O TrueSizer propõe uma experiência em que a pessoa pode:
1. entender como funciona a medição;
2. conceder acesso à câmera, quando optar pelo escaneamento;
3. seguir orientações de posicionamento;
4. visualizar medidas estimadas;
5. receber uma recomendação de tamanho;
6. avaliar a experiência.

A experiência também considera a possibilidade de inserir medidas manualmente, como alternativa ao uso da câmera.

## Meu papel e atribuição

O projeto acadêmico original foi desenvolvido por uma equipe de quatro integrantes no Enterprise Challenge IBM + FIAP.

- **Concepção de UX:** realizada pela equipe de UX.
- **Minha contribuição individual:** UX e produto, com participação na definição da experiência, das funcionalidades e dos fluxos.
- **Prototipação:** desenvolvimento orientado por prompts no Replit.

Este repositório apresenta o projeto com atribuição coletiva e individual diferenciadas. Não reivindico autoria individual sobre todo o projeto acadêmico.

## Protótipo e demonstração

- [Abrir protótipo interativo no navegador](https://serejobruna.github.io/True-Sizer/prototipo/)
- [Vídeo de apresentação do TrueSizer](https://www.youtube.com/watch?v=W55JiTZ_fis)
- [Protótipo navegável do TrueSizer](https://www.figma.com/proto/FcVAxuGq3e7gRFWq3evkH2/Untitled?node-id=2-2&p=f&t=3blM9qwJrIvMjIi4-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1&starting-point-node-id=2%3A2&show-proto-sidebar=1)

O vídeo e as telas demonstram a proposta e os fluxos do protótipo. A demonstração não comprova precisão técnica das medidas nem eficácia das recomendações.

## O que foi explorado

- jornada de medição por câmera e alternativa manual;
- instruções e feedback durante o escaneamento;
- apresentação de medidas e recomendações;
- experiência responsiva para navegação mobile;
- oportunidade de conectar a experiência do consumidor a indicadores de devolução e satisfação do varejista.

## Limitações conhecidas

- As medidas exibidas pelo protótipo não foram validadas contra instrumentos de referência.
- A recomendação de tamanho não foi validada com tabelas reais e abrangentes de marcas e modelagens.
- Não há evidência experimental suficiente para afirmar redução de devoluções ou aumento de NPS.
- Imagens e medidas corporais são dados pessoais sensíveis em potencial e exigem tratamento cuidadoso, transparência e controles de privacidade.
- O protótipo deve ser entendido como experimento de produto, não como serviço pronto para produção.

## Documentação

- [Case de produto e UX](docs/CASE_DE_PRODUTO_UX.md)
- [Auditoria técnica e próximos passos](docs/AUDITORIA_TECNICA.md)
- [Arquitetura: proposta acadêmica x protótipo](docs/ARQUITETURA.md)
- [Segurança e privacidade](docs/SEGURANCA_E_PRIVACIDADE.md)

## Status deste repositório

A documentação está sendo organizada para apresentação em portfólio. A publicação do código-fonte do protótipo depende da conferência da estrutura, remoção de credenciais e dados sensíveis, revisão das dependências e testes de execução. Não considere este repositório uma distribuição executável do produto até que essas etapas sejam concluídas.

## Contexto acadêmico

**Enterprise Challenge IBM + FIAP**  
Turma 1TSCOR — projeto TrueSizer.

Integrantes do trabalho acadêmico:
- Bruna Mayara Mendes Serejo
- Cesar Augusto da Silva Pereira
- Gabriel Francisco de Paulo
- Nicolas Kenji Gondo Yorinobu

## Objetivo deste case

Demonstrar raciocínio de produto, identificação de problema, tradução de evidências em uma proposta, desenho de experiência e uso de ferramentas de IA no processo de prototipação — com clareza sobre o que foi proposto, prototipado e efetivamente validado.
