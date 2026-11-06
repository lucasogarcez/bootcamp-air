# Curso de Linux (Udemy) · Anotações revisadas

- **Data:** 06/11/2026
- **Fonte:** Udemy, "Linux: Da migração à administração do sistema operacional.

## Resumo

- O curso cobre desde o que são terminais e quais os mais utilizados pela comunidade Linux, passando por usuários, gerenciadores de pacotes e processos, mostrando todos os comandos mais utilizados e suas vertentes, até chegar na manipulação de serviços e agendamento de tarefas no sistema. Para engenharia de dados, são muito utilizados os comandos relacionados a arquivos e pastas, comprimindo e descomprimindo, além da constante edição e leitura. Um dos mais importantes, muito usado para criar pipelines são os operadores, que permitem executar vários comandos em conjunto, além dos filtros para buscar arquivos/pastas/palavras de interesse. Possui um conteúdo denso, centrando sua dificuldade na edição e leitura de arquivos, já que se faz necessária a consulta de manuais o tempo todo para se utilizar os diversos comandos e seus inúmeros atributos.

## Comandos

### Shells (terminais)

- Existem vários shells: `bash`, `zsh`, `tcsh`, `ksh` (KornShell).
- `chsh -s {caminho_do_shell}`: muda o shell padrão do usuário (vale no próximo login).
- `echo $SHELL`: mostra o shell padrão (de login).
- `echo $0`: mostra o shell que está em uso agora.

### Usuário e sessão

- `su`: vira root mantendo o ambiente e a pasta atual.
- `su -`: vira root com o ambiente completo dele (login shell) e vai para a pasta inicial do root (`/root`).
- `su - {usuario}`: troca de usuário com o ambiente dele e vai para a pasta inicial dele.
- `Ctrl + D`: encerra o shell atual (dentro de um `su`, volta ao usuário anterior).
- `Ctrl + L`: limpa a tela (`clear`).

### Gerenciador de pacotes

- `apt`: advanced package tool. Instalar e remover exige `sudo`.
- `apt-cache search {nome}`: busca programas.
- `apt-cache show {nome}`: descrição do programa.
- `apt-get install {nome}`: instala um programa.
- `apt-get update`: atualiza a lista de pacotes disponíveis.
- `apt-get upgrade`: atualiza os programas instalados.
- `apt-get remove {nome}`: remove um programa.
- `apt-get source {nome}`: baixa o código-fonte.
- `aptitude`: reúne as funções em um só comando, com interface melhor (nem sempre vem instalado).

### Gerenciador de baixo nível

- `dpkg -I {arquivo.deb}`: informações de um arquivo `.deb`.
- `dpkg -i {arquivo.deb}`: instala um `.deb` (não resolve dependências sozinho).
- `dpkg -s {nome}`: status de um pacote já instalado.

### Ajuda pelo terminal

bash:

- `help`: lista os comandos internos do shell.
- `help {comando}`: ajuda de um comando interno.
- `{comando} --help`: ajuda de comandos externos.

zsh:

- `run-help`: ajuda do comando.
- `alias help=run-help`: exemplo de "apelido" para um comando.

Manuais:

- `apropos {palavra}`: procura a palavra nas descrições dos manuais (uma "busca" do sistema).
- `man man`: manual do próprio `man`.
- `man {seção} {comando}`: manual daquela seção (a seção 1 reúne os comandos de usuário).
- `man -k {palavra}`: equivale ao `apropos`.
- `man -w {comando}`: caminho do arquivo do manual.
- `whatis {comando}`: descrição de uma linha.

### Primeiros comandos

- `ls`: lista arquivos. `ls -a` inclui os ocultos. `ls -l` mostra permissões, dono, tamanho e data.
- `lsblk`: lista dispositivos de bloco (discos e partições).
- `lscpu`: informações do processador.
- `lspci`: dispositivos PCI. `lspci -v`: mais detalhes. `lspci -k`: inclui o driver em uso.
- `lsusb`: dispositivos USB conectados.
- `lsmod`: módulos do kernel carregados (incluindo drivers).
- `pwd`: pasta atual.
- `echo $OLDPWD`: pasta anterior.
- `cd -`: volta para a pasta anterior.
- `cd`, `cd ~`: vão para a pasta inicial do usuário atual.
- `cd ~{usuario}`: vai para a pasta inicial de outro usuário.
- `file {arquivo}`: mostra o tipo do arquivo.

### Comandos frequentes

- `mkdir {pasta}`: cria pasta.
- `mkdir -m {permissão} {pasta}` (ou `--mode=`): cria a pasta já com permissões.
- `mkdir -p a/b/c`: cria pastas aninhadas.
- `mkdir -p {diretorio}/{sub1,sub2}`: cria várias subpastas de uma vez (chaves simples e sem espaços; as chaves fazem parte do comando).
- `cp -v {arquivo} {novo}`: copia mostrando o que foi feito.
- `cp -rv {origem} {destino}`: copia pastas.
- `cp -riv {origem} {destino}`: copia pastas perguntando antes de sobrescrever.
- `mv -v {arquivo} {pasta}/`: move o arquivo para a pasta.
- `mv -v {arquivo} {novo_nome}`: renomeia.
- `rmdir {pasta}`: apaga pasta vazia.
- `rm -r {pasta}`: apaga pastas e arquivos, mesmo não vazios. **Não há lixeira.**
- `diff -r {pasta1} {pasta2}`: compara pastas recursivamente (mostra o que é só de um lado e o que difere).
- `rsync -r {origem}/ {destino}/`: sincroniza, copiando só o que mudou.
- `ln -s {alvo} {nome_do_link}`: link simbólico (um arquivo próprio que aponta para o caminho do alvo).
- `ln {alvo} {nome_do_link}`: link físico (outro nome para os mesmos dados, com o mesmo inode; não é cópia).
- `find {caminho} -name "{nome}"`: busca por nome.
- `find {caminho} -type f`: só arquivos.
- `find {caminho} -name "*.csv" -exec wc -l {} \;`: executa um comando em cada arquivo encontrado.

### Permissões de arquivos e bits especiais

- `ls -l` mostra algo como `drwxr-xr-x`. O 1º caractere é o tipo (`d` pasta, `-` arquivo). Depois vêm três grupos de três: dono (`u`), grupo (`g`) e outros (`o`).
- `r` leitura (4), `w` escrita (2), `x` execução (1).
- `chmod u=rwx,g=rx,o=r {arquivo}`: define por classe (sem espaços). `a` significa todos.
- `chmod g-w {arquivo}`: retira uma permissão. `chmod g+w {arquivo}`: acrescenta.
- `chmod 754 {arquivo}`: dono 7 (rwx), grupo 5 (r-x), outros 4 (r--).
- Com 4 dígitos, o primeiro é de bits especiais (4 setuid, 2 setgid, 1 sticky).

### Histórico e atalhos

- `!!`: repete o último comando (ex.: `sudo !!`).
- `!{texto}`: repete o último comando que começou com o texto (ex.: `!ls`).
- `Ctrl + R`: busca nos comandos digitados.
- `Ctrl + C`: interrompe o comando em execução.
- `Ctrl + Z`: suspende (pausa) o comando; retoma com `fg` ou `bg`.
- `top`: monitor de processos (gerenciador de tarefas do Linux).

### Operadores

- `{a} ; {b}`: executa em sequência.
- `{a} && {b}`: executa `b` só se `a` der certo.
- `{a} || {b}`: executa `b` só se `a` falhar.
- `{a} &`: executa em segundo plano.
- `{a} | {b}`: a saída de `a` vira a entrada de `b`.
- `jobs`: lista o que está em segundo plano.
- `fg %{id}`: traz para o primeiro plano.
- `kill %{id}`: encerra o job em segundo plano.

### Leitura e edição de arquivos de texto

- `cat {arquivo}`: mostra o arquivo. `cat -n`: com numeração de linhas.
- `tac {arquivo}`: mostra as linhas em ordem inversa.
- `head {arquivo}`: primeiras 10 linhas. `head -n {N}`: as N primeiras.
- `tail {arquivo}`: últimas 10 linhas. `tail -n {N}`: as N últimas.
- `less {arquivo}`: navega pelo arquivo; `/{palavra}` pesquisa; `q` sai.
- `grep {palavra} {arquivo}`: filtra linhas com a palavra.
- `grep -v {palavra} {arquivo}`: filtra as linhas sem a palavra.
- `grep -E "{a}|{b}" {arquivo}`: filtra por várias palavras.
- `grep -a {palavra} {arquivo}`: trata arquivo binário como texto.
- `nano {arquivo}`: editor simples. `vim {arquivo}`: editor mais avançado.

### Usuários e grupos

- `adduser {usuario}`: cria usuário.
- `passwd {usuario}`: altera a senha. `passwd -S {usuario}`: mostra o status.
- `addgroup {grupo}`: cria grupo.
- `sudo usermod -s {caminho_do_shell} {usuario}`: troca o shell do usuário (precisa relogar).
- `usermod`: também altera outras informações do usuário.
- `loginctl kill-user {usuario}`: encerra as sessões do usuário.

### Processos

- `ps`: processos do terminal atual. `ps aux`: todos os processos.
- `kill {PID}`: pede o encerramento do processo. `kill -9 {PID}`: força.
- `pgrep {nome}`: mostra o PID dos processos com esse nome.
- `nice -n {N} {comando}`: inicia um comando já com a prioridade ajustada.
- `renice -n {N} -p {PID}`: altera a prioridade de um processo em execução.
- Prioridade (nice) vai de -20 a 19. Valores menores significam mais prioridade, e aumentar a prioridade exige root.

### Serviços

- `systemctl start {servico}.service`: inicia.
- `systemctl stop {servico}.service`: para.
- `systemctl status {servico}`: mostra o estado.

## Correções que fiz nas minhas anotações

| Original | Revisado | Como conferir |
| --- | --- | --- |
| `su -`: "administrador em pasta local" | Login shell: ambiente completo e vai para a pasta inicial do usuário (`/root` no caso do root) | `pwd` antes e depois; `man su` |
| `Ctrl + D`: "sai das pastas, uma por uma" | Encerra o shell atual (EOF); não navega entre pastas | abrir `su` e usar `Ctrl + D` |
| `o (owner)` no `chmod` | `o` = others (outros). O dono é `u` (user). `a` = todos | `man chmod` |
| `chmod u=rwx, g=rwx, o=rwx` | Sem espaços após as vírgulas: `u=rwx,g=rx,o=r` | testar no Linux |
| `lsblk`: "arquivos de bloco" | Lista dispositivos de bloco (discos e partições) | rodar `lsblk` |
| `ln`: "cópia com mesmo índice" | Link físico é outro nome para os mesmos dados (mesmo inode); não é cópia | `ls -li` |
| `Ctrl + C`: "pausa ou mata" | Interrompe. Pausar é `Ctrl + Z` | testar com `sleep 100` |
| `Ctrl + T`: "fecha terminal" | Não é o atalho padrão do bash para isso; para encerrar, `exit` ou `Ctrl + D` (verificar no vídeo) | rever a aula |
| `!!{comando}` | `!!` repete o último comando; `!texto` repete o último que começou com o texto | testar |
| `dpkg -I/-i {nome}` | Esses comandos recebem um arquivo `.deb` | `dpkg --help` |
| `sudo -c "renice ..."` | Sintaxe correta: `sudo renice -n 5 -p {PID}` (verificar o que o vídeo mostrou) | `man renice` |
| `nice` / `renice` juntos | `nice` inicia um comando novo com prioridade; `renice` muda um processo já em execução | `man nice` |
| `diff {pasta1} {pasta2}` | Para comparar recursivamente, usar `diff -r` | testar |
| `rsync`: "não sobrescreve o idêntico" | Sincroniza copiando só o que mudou (arquivos alterados são atualizados) | `man rsync` |
| `cd ~{usuario}/` | Vai para a pasta inicial do usuário indicado (não a sua) | testar |
| `ps`: "processos ativos" | Lista os do terminal atual; `ps aux` mostra todos | testar |
| `mkdir -p dir/{{a,b}}` | Chaves simples e sem espaços: `{a,b}` | testar |
| Erros de digitação | `mkrdir` → `mkdir`; `tshc` → `tcsh`; `usuando` → `usando` | n/a |

## Dúvidas em aberto

- [ ] O que o vídeo quis dizer com "apropos {comando} {tecla de espaço}"? (rever a aula)
- [ ] O comando de prioridade no vídeo era `sudo` ou `su -c`? (anotei `sudo -c`)

## Como isso se conecta ao projeto ou ao negócio

- Qual comando me ajuda a inspecionar um arquivo grande de dados antes de carregá-lo?
  - Os comandos `head` e `tail` são úteis aqui, pois mostram só o começo e o fim do arquivo (como o cabeçalho e as últimas linhas), permitindo me situar antes de processá-lo por inteiro. O `less` também ajuda, porque permite navegar pelo arquivo e pesquisar com `/palavra` sem abri-lo todo.

- Onde permissões de arquivo importam quando os dados são sensíveis?
  - A segurança é um aspecto essencial. Com permissões bem definidas, só quem precisa consegue ler (`r`) ou alterar (`w`) os dados sensíveis, o que protege contra alteração indevida e vazamento. Por exemplo, `chmod 640` deixa o dono ler e escrever, o grupo só ler e os demais sem acesso. O ideal é dar a cada pessoa apenas o acesso de que ela precisa.

- Como `&&`, `||` e processos em segundo plano se relacionam a um pipeline que roda várias etapas?
  - Em um pipeline com várias etapas, o `&&` garante que a próxima só rode se a anterior der certo, por exemplo, para não carregar os dados se a extração falhou. O `||` permite definir o que fazer quando algo falha, como registrar o erro. Já o `&` coloca uma etapa demorada em segundo plano e libera o terminal. Com isso, o pipeline ganha eficiência e controle.

- Para que serve agendar e monitorar serviços em um servidor de dados?
  - Agendar serve para que tarefas recorrentes rodem sozinhas, como o backup do banco de dados, de preferência em horários de pouco uso do sistema para evitar lentidão. Já monitorar os serviços (por exemplo, com `systemctl status`) permite perceber rápido se algo parou ou falhou e manter controle de como e por onde os dados estão fluindo dentro da aplicação.

## Autoteste

1. Qual a diferença entre `su` e `su -`?
   - Resposta: o comando `su` passa para o usuário root, mantendo o ambiente e a pasta local. Em contrapartida, o comando `su -`, mesmo passando também o usuário para root, muda para o ambiente de "login shell" e vai para a pasta inicial do root: "/root".
2. Como ler `drwxr-xr-x`?
   - Resposta: dono: ler, escrever e executar; grupo: ler e executar; outros: ler e executar.
3. Qual a diferença entre `;`, `&&` e `||`?
   - Resposta: a diferença está na condição de execução. Utilizando o operador `&&`, caso o primeiro comando funcione o segundo será executado. Com o operador `||`, somente se o primeiro comando não funcionar é que o segundo será executado. Por último, o operador `;` executa os comandos em sequência, independente de um deles funcionar ou não.
4. Qual a diferença entre link simbólico e link físico?
   - Resposta: o link físico é como outro nome para o mesmo arquivo, mantendo seu ID na memória, enquanto o link simbólico é um arquivo que aponta para o caminho do arquivo original.
5. Como interromper e como pausar um comando em execução?
   - Resposta: para interromper, é utilizado o comando `Ctrl + C` e para pausar o comando `Ctrl + Z`.