git-tips

#Git

## Instalação e configuração inicial

### Instalação (linux .deb systems)

`sudo apt-get install git`		  # instala Git

### Configuração global

`git config --global user.name "nome"	  # seta usuario global`
`git config --global user.email "email"	  # seta email user global`
`git config --global core.editor vim 	  # seta editor principal`

### Configuração local (por projeto)

`git config --local user.name "nome"	  # seta usuario projeto`
`git cofnig --local user.email email   # seta email usuario projeto
`

## Criação de repositórios

### Criação de repositório Bare (source)

`git init --bare # cria repo remoto na pasta (server) `

**Permissão deve ver 777 -R na pasta**

### Criação de Repo local

`git init # cria repo na pasta (local)`

### Conectando repositório local ao Bare

`git remote add local /path_repo_server/   # Conecta reposerver p/ local client`

`git remote add origin /path_repo server/  # Conecta reposerver p/ origin` 

### Removendo conexão entre repositório local e Bare

`it remote rm origin			  # exclui remote do local  # ex: se path estiver errado.`

### Listando repositórios Bare conectados no Repo local

```
git remote			 # lista repos remote
git remote -v		 # lista repos remote c/ path
```

### Buscar dados do repo Bare (master)
`git pull local master	 # busca dados do repo remoto master  p/ repo no client chamdo local`

### Envar dados para repo Bare (master)

Envia dados p/ remoto master. Se master não existir será criado. Usado p/ popular o remoto master no inicio do dev.
`git push local master`			  


### Clonar repositório Bare para Repo local

Cria pasta do projeto e  clona repo remoto master
`git clone /remote-path nome-do projeto`


## Exemplos de uso


### Criação de repo vazio no server:

```bash

mkdir projeto
cd ./projeto 
git init --bare

```

### Criação de repo no 1o cliente e popula remote master com arquivos: 

```bash
mkdir projeto
cd ./projeto
touch file1-do-projeto.js
touch file2-do projeto.js
git init
git status
git add .
git status
git commit -m "inicio do projeto"
git status
git remote add origin /path-projeto-server/ ou url
git push -u  origin master   
git log

```

### Clonando o repo do server (cliente2):

```bash
git clone /path-projeto-server/ nome-do-projeto
cd nome-do-projeto
git status
git log

```

### Operacao basica no repo do client:

```bash
vim arquivo1.txt (altera arquivo txt)
git status
git add arquivo1.txt
git status
git commit -m "arquivo alterado"
git status
git log

```

## Desfazendo alterações

```bash
git checkout --arquivo-alterado-a-adicionar    # tira da lista de alterados
git checkout -- arquivo.txt # volta arquivo ao estado original desde o último commit.

git HEAD --arquivo adicionado-para-commit      # tira da lista de adicionados
git revert HASH				       # defaz commit


```

## BRANCHES - Criar p/ trabalhar em equipe (funcionalidades)

```
git branch				      # lista branchs
git branch titulo			      # Cria branch titulo
git branch botao-adicionar		      # Cria branch botao-adicionar
git branch lista			      # Cria branch lista
git checkou -b lista			      # Cria branch lista e vai p ele
git branch remove lista			      # remove branch lista

```
### Rebase e merge de branchs
```
git rebase  ## refaz linha de commits depois do master
git merge   ## junta commits no master (e faz novo commit)
```

### fluxo de trabalho - Estrategica p/ evitar conflitos: 

```
git pull origin master      ## busca arquivos do master
git checkout -b feature     ## cria branch de trabalho
realiza alteraçoes          ## alteraçoes nos arquivos (com commits) 
git pull origin master      ## busca arquivos do master (outros dev alteraram)
rebase master               ## inclui alteracoes do master no feature
git checkout master         ## muda pro branch master
git merge feature           ## merge entre master e feature
git log	                    ## master = feature
git push origin master      ## envia alterações para master do remoto

```

>  **Nota:** 
>  O arquivo .gitignore deve ficar fora do .git


## Stash - Area de armazenamento temporário
```
git stash		    ## armazena modificacoes temporarias
git stash list		    ## lista modificações temporarias
git stash apply 0	    ## aplica a modificação zero
git stash drop		    ## remove modificações do stash
git stash pop		    ## aplica modificações, e faz merge 
git diff commit1 commit2    ## mostra diferença entre commits
git tag -a v0.1.0 -m "msg"  ## adiciona uma tag com versão
```

## Rebase para commit anteriores
```
git rebase -i  HEAD~3   
git rebase -i selecionar commit anterior aos 3.

```
## Git log 
```
git log --oneline	    ## hash7 / head/ description

```



$ git remote set-url origin git@github.com:your_user/name_repository.git


[[git-tips]]