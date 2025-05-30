# Comandos Básicos

#### Aqui estaremos falando sobre o básico para o começo em GIT, com exemplos, explicações e imagens!

# Inicialização GIT

## 1. Git init

#### Este comando inicializa um novo repositório do GIT, ele cria uma pasta oculta dentro do seu projeto onde guarda:

* Histórico de Commits
* Referências (Suas branchs e tags)
* Arquivo de configuração do repositório

#### Se ultiliza o git init quando voce está começando um projeto e deseja versioná-lo com GIT. 

## Como Utiliza-lo

1. Na Pasta do seu projeto, abra o Git Bash (Voce pode fazer isso apertando Shift + Botão Direito do Mouse) Veja o exemplo abaixo:

![Abrindo o painel de opções](./imagens/Comandos_Básicos/Inicialização/CB_Exemplo1.png)

2. Quando apertar esta opção, irá abrir a tela do Git Bash que é parecida com a de um terminal, veja o exemplo abaixo: 

![Tela do Git Bash](./imagens/Comandos_Básicos/Inicialização/CB_Exemplo2.png)

3. Dentro deste "Terminal" Digite "Git Init" (Sem as aspas) e ele iniciará o seu repositório em sue projeto:

![Demonstração do git init](./imagens/Comandos_Básicos/Inicialização/CB_Exemplo3.png)

* Dentro do seu projeto deve ter criado uma pasta ".git" (É necessário ativar itens ocultos para ve-la):

![Print da pasta .git](./imagens/Comandos_Básicos/Inicialização/CB_Exemplo4.png)

## Git config

#### o Git config tem várias utilizações, mas falaremos somente das básicas, recomendadas de realizar antes de começar seu projeto

## Git config --global user.name "Seu nome"

#### Este comando define o seu nome de usuário global, ou seja, definirá seu nome para todos os projetos feitos.

* Dentro do Git bash, digite o código 'Git config --global user.name "Seu nome"'(Substitua o "Seu nome" pelo seu nome):

![Exemplo do código config nome no Git Bash](./imagens/Comandos_Básicos/Inicialização/CB_Exemplo5.png)

* Note que não houve nenhuma mensagem de confirmação, no final mostro como ver se deu certo

## Git config --global user.email "seuemail@.com"

#### Este comando define o seu email global, ou seja, definirá seu email para todos os projetos feitos.

* Dentro do Git bash, digite o código 'Git config --global user.email "seuemail@.com"'(Substitua o "seuemail@.com" pelo seu email):

![Exemplo do código config email no Git Bash](./imagens/Comandos_Básicos/Inicialização/CB_Exemplo6.png)

* Novamente note que não houve nenhuma mensagem de confirmação, agora vamos verificar estas informações

## Git config --list

#### Este comando irá te mostrar as configurações atuais do GIT

* Dentro do Git bash, digite o código 'Git config --list':

![Lista de configurações do Git bash](./imagens/Comandos_Básicos/Inicialização/CB_Exemplo7.png)

* Este commando irá te trazer uma lista completa de todas as configurações do git, note que as minhas informações de nome e email foram armazenadas

# Repositórios

#### Agora vamos aprender sobre os repositórios

## Git remote add origin "url"

#### Este comando irá linkar o seu projeto local com um projeto remoto, seu objetivo principal é criar uma ponte entre seu projeto local e remoto

* Vejamos como faze-lo no git bash: 

![Adicionando um repositório remoto como "origin"](./imagens/Comandos_Básicos/Repositórios/CB_Exemplo3.png)

* Agora vamos ver se está linkado mesmo com o repositório local

## Git remote -v 

#### Este comando vai listar todos os repositórios linkados com o projeto

* Utilize o comando "git remote -v" para ver os Rep. linkados com seu projeto:

![Lista de remotes do projeto](./imagens/Comandos_Básicos/Repositórios/CB_Exemplo4.png)

# Versionamento

#### Agora veremos sobre o versionamento do seu projeto

## Git status

#### Vai mostrar o estado atual dos arquivos (se foram modificados, não rastreados etc)

* Para ver o status dos seus arquivos basta apenas utilizar o comando "git status": 

![Git bash mostrando arquivos não rastreados](./imagens/Comandos_Básicos/Versionamento/CB_Exemplo1.png)

* Note que diz que os arquivos não estão rastreados, ou seja, falta fazer o "git add"
----
* Se estiver utilizando o VS Code, ele mostrará o status dos arquivos de acordo com a letra ao lado deles:

Letra   | Significado
--------- | ------
"U" | De "Untracked", ou seja, não rastreado,
"M"| De "Modified", ou seja, Arquivo modificado
"A" | De "Added, ou seja, já foi adicionado
"D" | De "Deleted", ou seja, deletado
"R" | De "Renamed", ou seja, Renomeado
"C" | De "Copied", ou seja, copiado
! | Arquivo com conflito de merge

## git add 

#### Este comando adiciona os arquivos que não estão rastreados no staging (preparando para commit), pode ser utilizado de duas formas:

## git add arquivo

* Adicionaa somente o arquivo que está sendo pedido:

![Adicionando somente o arquivo.txt](./imagens/Comandos_Básicos/Versionamento/CB_Exemplo2.png)

## git add .

* Adiciona todos os arquivos que não estão rastreados para staging:

![Adicionando todos os arquivos que faltavam](./imagens/Comandos_Básicos/Versionamento/CB_Exemplo3.png)

## git commit -m

#### Agora vamos commitar estes arquivos que estavam "staged"

* Para commitar os arquivos é só utilzar o comando 'git commit -m "descrição"'.

* **Lembre-se, é de extrema importância colocar uma descrição completa e coerente com o que foi feito no arquivo, todas as modificações tem que ser ditas aqui, pois na hora que for preciso voltar uma versão no projeto, é está descrição que vai ajudar descobrir o que foi feito.**

![Dando commit nos arquivos adicionados](./imagens/Comandos_Básicos/Versionamento/CB_Exemplo4.png)

## git log

#### É com esse comando que vemos todo o histórico de commits feito no projeto

* É feito com o código "git log" dentro do git bash.

![Histórico dos commits adicionados](./imagens/Comandos_Básicos/Versionamento/CB_Exemplo5.png)

* Como pode ver, este comando traz todas as informações necessárias para se saber o que foi feito, quando foi feito e quem o fez.

# Ultimas considerações

#### Esta pagina é de uso para aprendizado, ensinando sobre os comnandos básicos para se utilizar git em um projeto.

### Lembre-se de sempre colocar suas descrições nos commits!!

## Página feita por Keltton Felipe