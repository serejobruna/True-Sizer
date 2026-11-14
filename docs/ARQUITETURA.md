# TrueSizer — Arquitetura: proposta acadêmica e protótipo

## Arquitetura proposta no trabalho acadêmico

A apresentação final do Enterprise Challenge descreve os seguintes blocos:

1. **Usuário e interface:** React para web e Flutter para mobile; React Hook Form e Yup são citados para formulários.
2. **Aplicação/backend:** Node.js para requisições HTTP e comunicação com banco de dados e APIs externas.
3. **Dados:** MongoDB para dados não estruturados, SQL Server para dados estruturados e uma API de tamanhos para consultar padrões por marca.
4. **Processamento:** Python e IBM Watson Studio para limpeza, preparação e normalização dos dados; Docker para consistência de ambiente.
5. **Machine Learning:** Watson Machine Learning e Watson AutoAI para modelos preditivos de recomendação.
6. **Feedback e avaliação:** formulários em React e Google Analytics.
7. **Consolidação e visualização:** IBM Watson Studio, Python e Power BI para dashboards e indicadores.

A apresentação também menciona medidas de segurança propostas, como SSL/TLS, criptografia AES e OAuth 2.0.

## O que está evidenciado no protótipo

A apresentação final informa que o mockup foi construído utilizando Replit. As telas apresentadas demonstram:
- página inicial;
- permissão de acesso à câmera ou escolha de entrada manual;
- instruções de medição;
- etapa de escaneamento;
- exibição de medidas;
- recomendações de tamanho;
- pesquisa de satisfação.

## O que não está comprovado

A documentação disponível não comprova que todos os serviços, bancos de dados, modelos de machine learning, APIs e controles de segurança descritos na arquitetura proposta estejam implementados e integrados no protótipo.

Por isso, a arquitetura listada nesta página deve ser entendida como **arquitetura proposta no trabalho acadêmico**, não como inventário confirmado da implementação.

## Fluxo conceitual

Usuário → Interface → Coleta de medidas → Processamento/recomendação → Resultado → Feedback

Este fluxo resume a proposta funcional. A implementação técnica de cada etapa deve ser confirmada por inspeção do código e testes.
