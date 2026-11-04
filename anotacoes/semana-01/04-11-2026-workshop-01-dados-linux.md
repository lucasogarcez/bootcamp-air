# Ciclo de vida do dado; Linux e terminal (Bash) · Workshop 1

- **Data:** 04/11/2026
- **Fonte:** workshop

## Resumo

Aprendi que os dados passam por considerável caminho até serem considerados para uso. A cada etapa, são necessários diversos processos e um constante monitoramento, pois erros em qualquer uma delas podem desencadear análises e previsões erradas lá na frente. A IA nos auxilia bastante nisso, produzindo códigos bons conforme pedido, porém, exige rigorosa revisão e testes. Para além disso, o sistema operacional base para muitas aplicações é o Linux, por isso é importante conhecer seus comandos e sua utilização em processos do dia a dia, envolvendo até sistemas como a AWS e contêineres como o Docker. Mesmo com a IA tendo amplo conhecimento técnico, é importante conhecer e até se aprofundar, conforme necessidade, nos assuntos que serão pedidos a ela, não ignorando importantes aspectos como a segurança.

## Conceitos-chave

- **ETL:** processo de integração de diversos dados em sequência estruturada: extração, tratamento e envio para repositório.
- **Data Lake:** repositório centralizado para armazenar grande volume de dados, sem necessidade de processá-los ou estruturá-los anteriormente.
- **Data Hub:** plataforma centralizada que conecta diversas fontes de informações e padroniza os dados para facilitar o compartilhamento e governança.

## Recomendações

- [Penguin Gym](https://penguin-gym-linux.com/en/terminal): plataforma de testes práticos de comandos Linux, Git, Docker, SQL e entre outras tecnologias.
- AWS Certified Cloud Practitioner

## Como isso se conecta ao projeto ou ao negócio

- **Cenário:** o financeiro guarda o fluxo de caixa em planilhas e precisa dos meses anteriores para projetar o orçamento do mês seguinte.

- **Pergunta:** como saber se esses dados são confiáveis o bastante para realizar análises utilizando eles?

- **Resposta:** 
  - Planilhas costumam ser a origem mais sujeita a erros, pois dependem de preenchimento manual. Por isso, os dados não devem ser considerados confiáveis de imediato: é preciso passá-los por etapas de tratamento e validação até chegarem a uma camada já estruturada e avaliada, como a "Business" ou "Ouro".
  - Diante disso, deve-se verificar formatos e tipos, duplicatas, campos vazios e valores fora do esperado, além de comparar os totais com outra fonte, como o extrato bancário.
  - A confiança vem dessas verificações. Por isso, mesmo com os dados na camada final, o monitoramento continua e, em caso de erros percebidos, corrige-se a origem ou a regra de tratamento e reprocessa-se, em vez de ajustar o resultado manualmente.

## Autoteste

1. Quais as etapas do ciclo de vida do dado?
   - Iniciamos com a geração/coleção dos dados, seguida da ingestão e armazenamento em banco, com posterior processamento, análise e consumo desses dados, governança e qualidade para garantir segurança e rastreabilidade, levando ao arquivamento ou descarte e, como uma etapa constante, o monitoramento dos dados, evitando erros e defasagens.
2. O que é um pipeline?
   - É uma sequência automatizada de etapas que leva um dado da origem ao seu destino.