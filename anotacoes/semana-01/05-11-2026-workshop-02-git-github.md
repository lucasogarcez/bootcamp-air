# Git e GitHub · Workshop 2

- **Data:** 05/11/2026
- **Fonte:** workshop

## Resumo

É sempre importante manter cada projeto organizado. Em um trabalho com muitas pessoas no mesmo projeto, o Git é necessário para versionar os arquivos e registrar o histórico de alterações (quem mudou o quê e quando). Já o GitHub, um repositório online, permite que todos armazenem e acessem o projeto e colaborem por meio de ferramentas como o Pull Request.

## Conceitos-chave

- **Git:** sistema de controle de versão distribuído, que registra o histórico de alterações dos arquivos e permite voltar a versões anteriores.
- **GitHub:** plataforma online que hospeda repositórios Git e oferece ferramentas de colaboração, como Pull Requests, revisão de código e issues.
- **Repositório:** pasta do projeto com todo o seu histórico, que pode ser local ou remoto.
- **Commit:** registro das alterações preparadas com `git add`, salvo no histórico com uma mensagem e o autor.
- **Branch:** linha independente de desenvolvimento, que permite alterar o projeto sem afetar a `main` até a integração.
- **Merge:** integra as alterações de uma branch em outra. Se as mesmas linhas foram alteradas de formas diferentes, ocorre um conflito, resolvido manualmente.
- **Push:** envia os commits locais para o repositório remoto.
- **Pull:** baixa os commits do repositório remoto e os integra na branch atual.
- **Pull Request:** pedido, feito no GitHub, para integrar uma branch em outra, com espaço para revisão e discussão antes do merge.

## Comandos ou código que funcionam

```bash
git init                      # cria um repositório Git na pasta atual
git add README.md             # prepara o arquivo para o commit
git commit -m "first commit"  # registra as alterações preparadas, com a mensagem
git branch -M main            # renomeia a branch atual para "main"
git remote add origin https://github.com/usuario/nomedorepositorio.git  # registra o remoto com o apelido "origin"
git push -u origin main       # envia a "main" ao remoto e a vincula (-u) à branch remota
```

Resultado obtido: repositório local criado, com um commit contendo o `README.md`, branch renomeada para `main` e enviada ao repositório remoto no GitHub.

## Como isso se conecta ao projeto ou ao negócio

- **Cenário:** um time de desenvolvimento está modificando uma funcionalidade de um site e duas pessoas alteraram as mesmas linhas do mesmo arquivo, em branches diferentes.

- **Pergunta:** como resolver o conflito entre as alterações e garantir que a versão final esteja correta?

- **Resposta:**
  - Ao integrar as branches (`git merge` ou `git pull`), o Git avisa do conflito e marca no arquivo as duas versões (`<<<<<<<`, `=======`, `>>>>>>>`).
  - Quem está integrando decide o que permanece: escolhe uma versão ou combina as duas, remove os marcadores, executa `git add` no arquivo e conclui com `git commit`.
  - Para reduzir conflitos: branches curtas, `git pull` frequente e Pull Requests pequenos, com revisão de outra pessoa. A governança do repositório entra na revisão e nas regras de proteção da `main`.

## Autoteste

1. Em um time de desenvolvimento, como várias pessoas conseguem trabalhar no mesmo projeto?
   - Cada pessoa trabalha em uma branch própria, registra suas alterações em commits e as envia ao repositório remoto. Depois, abre um Pull Request para revisão e integração na `main`. O histórico de commits mostra quem alterou o quê e quando.
2. O que acontece quando duas pessoas alteram as mesmas linhas de um arquivo, e como resolver?
   - O Git não decide sozinho: ele interrompe o merge e marca o conflito no arquivo. É preciso editar o arquivo, escolher ou combinar as versões, executar `git add` e concluir com `git commit` (ou `git merge --continue`). O `git merge` é o comando que dispara o conflito, e não o que o resolve.