# bootcamp-air

Meu diário técnico do bootcamp **AI/R Fellowship: AI-Driven Data Engineering** (novembro de 2026).
Aqui ficam minhas anotações, laboratórios práticos e o registro de como uso IA para estudar.

> Todas as anotações são escritas com minhas palavras. Nenhum material de curso é copiado.

## Sobre mim

Lucas Oliveira Garcez · estudante de Engenharia da Computação · [LinkedIn](www.linkedin.com/in/lucas-oliveira-garcez) · [E-mail](lucas.o.garcez1@gmail.com)

## Objetivo

Aprender engenharia de dados na prática (terminal, Git, SQL com PostgreSQL, Python para dados, ETL, testes e Docker) e deixar o caminho documentado e reproduzível.

## Cronograma e progresso

| Semana | Data | Tema | Anotações | Laboratório | Status |
| --- | --- | --- | --- | --- | --- |
| 1 | 04/11 | Workshop 1: ciclo de vida do dado; Linux e terminal (Bash) | `anotacoes/semana-01/` | `labs/semana-01-bash/` | Feito |
| 1 | 05/11 | Workshop 2: Git e GitHub | `anotacoes/semana-01/` | `labs/semana-01-git/` | Feito |
| 2 | 10/11 | Workshop 3: modelo relacional e SQL com PostgreSQL | `anotacoes/semana-02/` | `labs/semana-02-sql/` | Pendente |
| 2 | 12/11 | Workshop 4: fluxo de Pull Request, testes de consulta e decisões com IA | `anotacoes/semana-02/` | `labs/semana-02-sql/` | Pendente |
| 3 | 17/11 | Workshop 5: Python aplicado a dados | `anotacoes/semana-03/` | `labs/semana-03-python/` | Pendente |
| 3 | 19/11 | Workshop 6: ETL como padrão arquitetural, com APIs e bancos de dados | `anotacoes/semana-03/` | `labs/semana-03-etl/` | Pendente |
| 4 | 24/11 | Workshop 7: testes (pytest), revisão de código e Docker | `anotacoes/semana-04/` | `labs/semana-04-testes-docker/` | Pendente |

Atualizo a coluna "Status" para "Feito" conforme concluo cada etapa.

## Estrutura do repositório

```
bootcamp-air/
├── README.md
├── .gitignore
├── anotacoes/          # uma pasta por semana, um arquivo por workshop ou curso
│   ├── _modelo.md      # modelo de anotação
│   └── semana-01/
├── labs/               # exercícios práticos que rodam (scripts, SQL, notebooks)
│   └── semana-01-bash/
└── ai-log/             # registro de uso de IA, um arquivo por dia
```

## Como usar os laboratórios

Cada pasta em `labs/` tem seu próprio `README.md` com:

1. o que o laboratório pratica;
2. como executar (comandos, versões usadas);
3. o resultado esperado.

## Uso de IA

Uso IA como apoio para estudar e programar, e registro cada uso em [`ai-log/`](ai-log/): o que pedi, o que veio, como verifiquei e o que decidi. Nada gerado por IA entra aqui sem que eu o tenha testado e entendido.

## Segurança

Não há senhas, chaves ou dados pessoais neste repositório. Configurações sensíveis ficam em arquivos `.env`, ignorados pelo Git.