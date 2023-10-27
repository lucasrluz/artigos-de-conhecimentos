# O básico de Git

## O que é git?
Git é um versionador de código, gratuito e de código aberto. Um versionador de código serve para que possamos criar um histórico de tudo o que fazemos no código, isso é ótimo porque podemos trabalhar em equipe e todas as alterações ficam registradas de forma padronizada, facilitando o estendimento do que a outra pessoa vez no código.

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
user.email="<seu-email>"
user.name="<seu-nome>"
init.defaultBranch="main"
core.editor="<seu-editor>"
```

## Inicializando um novo repositório local
Antes de inicializar um novo repositório Git devemos ter um diretório na qual vamos trabalha.

Para inicializar um novo repositório Git usamos o seguinte comando:
```
$ git init
```

Note que foi criado um diretório `.git` que contém todos os arquivos de repositório necessários.

Com o comando `$ git status` podemos ver as informações a respeito de mudanças no nosso repositório. Caso rode o comando agora, deve aparecer algo indicando que não existe commits e nada foi alterado.

```
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

## Primeiro commit
Depois de inicializar um novo repositório Git no diretório de sua escolha, vamos começar adicionando um novo arquivo com o nome de `a.txt` e dentro vou colocar o seguinte conteúdo:

```
Conteúdo do arquivo a.txt
```

Agora se executarmos o seguinte comando `$ git status` vamos ver algumas informações que na execução anterior do mesmo comando, não tinha. Além das informações anteriores, temos:

```
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	a.txt
```
Aqui o Git está informando que exite um ou mais arquivos que não estão sendo rastreados, ou seja, caso fizermos alterações nesse arquivo não vamos conseguir ter um histórico do que foi alterado ou adicionado.
