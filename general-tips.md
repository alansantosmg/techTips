it-tips

**strong text**# It - Notas, dicas e truques do dia-a-dia  <!-- omit in toc -->

Olá. Aqui você encontrará algumas dicas, truques e notas técnicas sobre diversos tópicos em tecnologia da informação. Anoto para não ter que ficar lembrando de comandos, atalhos ou mesmo soluções inteiras que desenvolvi ou encontrei em minhas pesquisas, liberando a memória para atividades mais nobres. Se me ajudaram, talvez possam ser úteis a outros em sua jornada profissional. Bom proveito!

- [Firefox Tweaks](#firefox-tweaks)
  - [Correção de background de forms em tema Dark no Linux](#correção-de-background-de-forms-em-tema-dark-no-linux)
  - [Parar de receber as irritantes solicitações de notificação de sites](#parar-de-receber-as-irritantes-solicitações-de-notificação-de-sites)
- [Git](#git)
  - [Instalando o Git no linux](#instalando-o-git-no-linux)
  - [Configurando usuário e email no GIT](#configurando-usuário-e-email-no-git)
  - [Criando um novo repositório GIT local](#criando-um-novo-repositório-git-local)
  - [Verificando status do repositório](#verificando-status-do-repositório)
  - [Verificando histórico do projeto (commits)](#verificando-histórico-do-projeto-commits)
  - [Adicionando um repositorio remoto](#adicionando-um-repositorio-remoto)
  - [Removendo um repositorio remoto](#removendo-um-repositorio-remoto)
  - [Operação básica do GIT](#operação-básica-do-git)
  - [Criação e utilização de branch](#criação-e-utilização-de-branch)
  - [Criando um arquivo gitignore](#criando-um-arquivo-gitignore)
- [Linux](#linux)
  - [Comandos de terminal úteis](#comandos-de-terminal-úteis)
  - [Atualização do cache de fontes](#atualização-do-cache-de-fontes)
  - [Acertar horário Windows em máquinas dualboot Linux](#acertar-horário-windows-em-máquinas-dualboot-linux)
  - [Correção erro ao carregar loja de apps do Ubuntu](#correção-erro-ao-carregar-loja-de-apps-do-ubuntu)
- [Visual Studio Code (vscode)](#visual-studio-code-vscode)
  - [Definindo Vscode como editor de textos padrão no Linux](#definindo-vscode-como-editor-de-textos-padrão-no-linux)
  - [Atalhos de teclado não óbvios do Vscode](#atalhos-de-teclado-não-óbvios-do-vscode)
  - [Extensão Markdown All in One](#extensão-markdown-all-in-one)
    - [Criação automática de sumário (Table of Contents)](#criação-automática-de-sumário-table-of-contents)












## Firefox Tweaks

### Correção de background de forms em tema Dark no Linux

Quando usuário opta por utilizar tema escuro no LInux, o Firefox acaba renderizando caixas de texto dos formulários de forma incorreta (fundo escuro com fonte preta), dificultando a digitação de texto e leitura.
Para corrigir:

1. Abra o Firefox e digite `about:config` na barra de navegação.
2. Clique com o botão direito do mouse abaixo da barra search e crie um nova entrada de registro do tipo `string`.
3. Ao criar a entrada preencha o parâmetro name com:  `widget.content.gtk-theme-override`.
4. Preencha o parâmetro value com: `Adwaita:light`.
5. Reinicie o Firefox.

### Parar de receber as irritantes solicitações de notificação de sites

1. Abra o Firefox e digite `about:config` na barra de navegação.
2. Na caixa search busque o termo: `webnotif`.
3. Dê um duplo clique na chave: `dom.webnotifications.enabled` e altere o valor de `true` para `false`.
4. Reinicie o Firefox.

## Git

### Instalando o Git no linux

Nas distribuições baseadas em Debian o git deve ser instalado com o seguinte comando:

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```

### Configurando usuário e email no GIT

Setup your e-mail and account to use with git. Do the following commands in your terminal:

```bash
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR EMAIL ADDRESS"
```

### Criando um novo repositório GIT remoto (server)

```bash
git init --bare
```

### Adicionando um repositório remoto no repositório local

Ir até o diretório local e digitar os comandos: 

```bash
git remote add local /my-git-remote-repo-path/
git remode add outronome /my-git-remote-repo-path
```

### Listar repositórios remotos adicionados ao repositório local

```bash
git remote 
git remote -v 
```
### Buscar dados de um repositório remoto master para um repo chamado local
```git pull local master``` 

### Buscar dados de um repositório remoto master para um repo chamado origin
```git pull origin master```

### Enviar dados para um repositório remoto master de um repo chamado local

Se o repositório remoto master não existir será criado e populado.

```git push local master```

### clonar um repositório renomeando-o no local
git clone /path/ nome-do-projeto


### Criando um novo repositório GIT local

É necessário ter o git instalado na máquina para criar um repositório local.
Para criar um repositório local para seu projeto com GIT digite:

```bash
git init
git add *
git commit -m "first commit"
```

### Verificando status do repositório

```bash
git status
```

### Verificando histórico do projeto (commits)

```bash
git log
git log -p -2
git log --stat
git log --pretty=oneline
git log --pretty=full
git log --pretyy=short
git log --prety=fuller
git log --pretty=format:"%h - %an, %ar : %s"
git log --pretty=format"%h %s" --graph

```

```bash
git remote add origin https://github.com/myAccount/myProject.git
git push -u origin master
```

### Removendo um repositorio remoto

```bash
git remote rm origin
```

### Operação básica do GIT

```bash
git add arquivo-to-commit
git commit -m "mensagem de commit"
git push
git checkout --arquivo-to commit

```

Desfazendo alterações: 
git reset HEAD arquivo-adicionado para commit
git checkout --arquivo-para-adicionar


git revert <hash>
Desfaz o commit <hash>
gera commit para explicar pq



### Criação e utilização de branch

Um branch é um fork realizado no projeto principal. Cria-se um branch para por exemplo trabalhar uma nova feature ou uma determinada correção, distinguindo um trabalho específico do resto do código. Uma vez finalizado o trabalho, o branch pode ser reunido ao ramo principal através de um merge. É possivel ter equipes diferentes trabalhando em features diferentes. Portanto pode-se criar um branch para feature A e outro para feature B e outro para correção e assim cada equipe trabalha em uma atividade sem interferir nas atividades da outra.  Depois é feito o merge e conflitos podem ser resolvidos. 

git branch                     Lista branchs existente e branch ativo
git branch  teste              Criar branch teste
git checkout teste	       Muda para branch teste
git chekcout -b lista          Criar branch lista e muda para ele


git rebase:
junta o que foi feito no master em seu repo local

git merge
junta o que foi feito no branch local para o master




### Criando um arquivo gitignore

O gitignre é um arquivo que fica escondido dentro do seu repositório git. Ele é usado para fazer o git ignorar determinados tipos de arquivo. Para criá-lo é possível usar o script shell abaixo:

```bash
touch gitignore
echo "*.log" >> gitignore
echo "*_pycache_" >> gitignore
echo "*.[oa]" >> gitignore
echo "*~" >> gitignore
echo "!lib.a" >> gitignore
echo "*.pyc" >> gitignore
echo ".vscode" >> gitignore
echo "*.vscode" >> gitignore
echo "settings.json" >> gitignore
echo
sleep 2
clear
echo "Arquivo gitignore criado em ./.git"
echo "Não monitorando (ignorando): "
sleep 2
echo "---------------"
cat gitignore
echo "---------------"
sleep 10
echo
```

## Linux

### Comandos de terminal úteis

| Comando     | Função                               |
| ----------- | ------------------------------------ |
| `ss -a`     | Listar portas abertas no server.     |
| `uname -a`  | Mostrar versão do kernel do sistema. |
| `uname - r` | Mostrar versão do kernel sistema.    |
| `ip addr`   | Listar interfaces de rede.           |

### Atualização do cache de fontes

Após instalar uma fonte nova executar no terminal: `sudo fc-cache –f -v`

### Acertar horário Windows em máquinas dualboot Linux

Em instalações dualboot windows/linux o horário do Windows fica incorreto.
É possível corrigir no linux:

1. Verifique se o relógio do Linux está usando UTC:
    - `timedatectl | grep local`
2. Se estiver, mude para local time:
    - `timedatectl set-local-rtc 1`
3. Caso queria desfazer a mudança:
    - `timedatectl set-local-rtc 0`

### Correção erro ao carregar loja de apps do Ubuntu

O cache da loja de aplicativos do Ubuntu pode se corromper levando a duas situações: ou a loja não carrega ou a lista de aplicativos é baixada cada vez que o software é aberto (não faz cache). Para corrigir é preciso apagar o cache. Abra um terminal e digite os comandos abaixo e depois abra novamente a loja para baixar a lista de apps e criar um novo cache:  

- `killall gnome-software`
- `sudo rm -rf ~/.local/share/gnome-software`

## Visual Studio Code (vscode)

### Definindo Vscode como editor de textos padrão no Linux

Abra um terminal e digite:
`xdg-mime default code.desktop text/plain`.

### Atalhos de teclado não óbvios do Vscode

| Comando            | Função                                                               |
| ------------------ | -------------------------------------------------------------------- |
| `ctrl + ` `        | Open terminal                                                        |
| `Ctrl + Shift + V` | Markdown Preview:(depende da extensão Markdown All in One instalada) |

### Extensão Markdown All in One

A extensão MarkdownAll é recomendada para ser instalada e reune em si diversas funcionalidades interessantes.

- Fornece atalhos para formatação rápida do documento em MD.
- Converte arquivos MD em HTML.
- Ajuda a criar sumário automaticamente para arquivos MD.

#### Criação automática de sumário (Table of Contents)

Após criar seu documento MD no Vscode com suas respectivas seções faça:

1. Posicionar o cursor no local onde ficará o sumário.
2. teclar ```Ctrl + Shift + P```
3. Digitar na janela de comando:  ```Markdown All In one: Create table of contents```
4. Salvar o arquivo.

Para atualizar o sumário repetir o procedimento acima, porém usando o comando:
```Markdown All in one: update table of content```
