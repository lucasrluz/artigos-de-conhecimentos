# O básico de Git

## O que é git?
Git é um versionador de código, gratuito e de código aberto. Um versionador de código serve para que possamos criar um histórico de tudo o que fazemos no código, isso é ótimo porque podemos trabalhar em equipe e todas as alterações ficam registradas de forma padronizada, facilitando o estendimento do que a outra pessoa vez no código e tendo a possibilidade de "voltar no tempo", para uma determinada versão do código.

## Configuração básica

Depois de instalar o Git é importante fazer algumas configurações básicas. Primeiro vamos definir o email e username, isso serve para identificar quem faz alguma alteração no código.

```
$ git config --global user.email "<seu-email>"
$ git config --global user.name "<seu-nome>"
```

Agora vamos definir um editor que será utilizado para resolver conflitos (vou falar mais sobre isso para frente).

```
$ git config --global core.editor "<seu-editor>"
```

Para finalizar vamos definir o nome default da branch quando inicializamos o git.

```
$ git config --global init.defaultBranch "main"
```

Agora podemos visualizar as configurações que fizemos com `$ git config --list` e algo assim deve aparecer.

```
$ git config -list

user.email="<seu-email>"
user.name="<seu-nome>"
init.defaultBranch="main"
core.editor="<seu-editor>"
```

## Inicializando um novo repositório local
Antes de inicializar um novo repositório Git vamos criar um diretório para podermos trabahar. 

```
$ mkdir o-basico-de-git
$ cd o-basico-de-git
```

OK, agora com o diretório criado podemos inicializar um repositório Git.

```
$ git init
```

Note que foi criado um diretório `.git` que contém todos os arquivos de repositório necessários.

Um comando muito importante quando se trabalha com Git é o `$ git status`, com ele podemos ver as mudanças que ocorreram no repositório. Executando ele agora podemos ver que o Git informa que não existem commits e não tem nada para fazer commit.  

```
$ git status

On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

## Primeiro commit
Um commit é o registro das modificações do repositório, de forma simplificada ele contém um identificador e uma mensagem que indica o que foi alterado/adicionado.

Depois de inicializar um novo repositório Git no diretório que criamos antes, vamos começar adicionando um novo arquivo com o nome de `a.txt` com um conteúdo qualquer dentro.


```
$ touch a.txt
$ echo "Conteúdo do arquivo a.txt" >> a.txt
```

Agora se executarmos `$ git status` vamos ver algumas informações que na execução anterior não tinha. 

```
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	a.txt
```

Aqui o Git está informando que exite um ou mais arquivos que não estão sendo rastreados, ou seja, caso fizermos alterações nesse arquivo não vamos conseguir ter um histórico do que foi alterado ou adicionado.

Para criar um commit você precisa separar os arquivos que irão para o commit e para isso usamos o comando `$ git add <nome-do-arquivo>...`, no nosso caso vamos adicionar o arquivo `a.txt` e rodar `$ git status` para ver o que mudou. 

```
$ git add a.txt
$ git status

On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   a.txt
```

Nesse caso o Git está informando os arquivos que irão para o próximo commit e o status do arquivo, se ele é novo, foi deletado ou alterado. Note que na mensagem o Git informa como remover um arquivo do próximo commit com `$ git rm --cached <file>...`, isso serve para remover algum arquivo que tenha sido colocado errado.

Agora podemos finalmente fazer o commit com `$ git commit -m "<mensagem-do-commit>"`. 

```
$ git commit -m "adicionado arquivo a.txt"
$ git status

On branch main
nothing to commit, working tree clean
```

Quando estamos trabalhando em equipe as mensagens de commit são importantes porque é com elas que vamos ter o entendimento sem ler o código do que a outra pessoa fez, por isso é muito importante que as mensagens sejam claras e objetivas.

Para visualizar o histórico de commits feitos, podemos usar o comando `$ git log`.

```
$ git log

commit de75b4a5e0affac9c36e70ffdfbcc43f4edd1fb4 (HEAD -> main)
Author: <seu-nome> <seu-email>
Date:   Sun Oct 29 19:18:37 2023 -0300

    adicionado arquivo a.txt
```

Aqui está apresentado todas as informações sobre os commits feitos, data, nome e email de quem fez, a mensagem endicando a mudança e o identificador do commit que fica logo na primeira linha após a palavra "commit". Para sair dessa tela precione a tecla "q".

Agora vamos fazer uma alteração no arquivo `a.txt` adicionado mais conteúdo lá.

```
$ echo "Novo conteúdo do arquivo a.txt" >> a.txt
$ git status

On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Agora podemos além de adicionar esse arquivo para o próximo commit, também podemos reverter a alteralção feita no arquivo com `$ git restore <file>...`, vamos fazer isso para ver o que acontece.

```
$ git restore a.txt
$ git status

On branch main
nothing to commit, working tree clean

$ cat a.txt
Conteúdo do arquivo a.txt
```

Depois de rodar `$ git restore a.txt` podemos ver que a modificação de fizemos foi deletada.

