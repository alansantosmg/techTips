# Vim Tips

## Comandos de entrada, saida e salvamento de arquivos

| Comando        | Função                                     |
| -------------- | ------------------------------------------ |
| :enew!         | não salva e abre novo arquivo sem split    |
| :new arquivo   | abre novo arquivo horizontal               |
| :vnew          | arquivo abre novo arquivo split vertical   |
| :tabnew        | abre novo arquivo em aba                   |
| :edit arquivo  | abre outro arquivo                         |
| :e arquivo     | abre outro arquivo                         |
| :e ctrl d      | mostra arquivos do diretorio para abrir    |
| :split arquivo | abre novo arquivo                          |
| :e .           | abre file explorer na janela atual         |
| :Vex           | Abre file explorer na vertical             |
| :q             | sair do vim                                |
| :q!            | forca saida do vim                         |
| :w             | salva arquivo                              |
| :x             | salva e sai (se modificado)                |
| :w novonome    | salva como novo nome                       |
| :saveas novon  | salva cmoo novo nome e vai p/ novo arquivo |
| :wq            | salva arquivo e sai                        |
| :10,20 w! novo | salva da linha 10 a 20 em novo arquivo     |
| vim .          | abre o vim com file explorer               |
| '0             | reabertura do ultimo arquivo aberto        |
| '1             | reabertura do penultimo arquivo aberto     |
| :wn            | salva e vai para proximo arquivo           |
| :shell         | abre shell (exit para voltar               |
| :!             | run external comando                       |
| :!program %:p  | Abre arquivo com programa padrão.          |
| :terminal      | abre shell numa janela                     |
| :read file2    | carrga file2 abaixo do cursor no file1     |
| :read shell-c  | carrega saida de shell script              |
| :8read file2   | carrega file2 na linha 8 do file1          |

## Comandos de manipulação do buffer de arquivos

| Comando  | Função                                      |
| -------- | ------------------------------------------- |
| badd     | adiciona arquivo ao buffer                  |
| bn       | next file of buffer                         |
| bp       | arquivo anterior                            |
| ls       | lista arquivos do buffer                    |
| b1       | carrega arquivo 1 do buffer                 |
| bw "n"   | fecha buffer sem salvar                     |
| bdelete  | apaga arquivo do buffer                     |
| split #2 | carrega arquivo 2 do buffer em janela horiz |
| vplit #2 | carrega arquivo 2 do bufffer em janela vert |

## Comandos de manipulação de janelas

| Comando             | Função                               |
| ------------------- | ------------------------------------ |
| ctrl wn             | abrir nova janela sobre atual (:new) |
| ctrl wq             | fecha janela atual (:quit)           |
| ctrl wc             | fecha janela atual                   |
| ctrl ws             | Divide janela em duas (:split)       |
| ctrl wo             | Faz janela atual ser unica (:only)   |
| ctrl w w            | alterna entre janelas                |
| ctrl wj             | desce uma janela                     |
| ctrl wk             | sobe uma janela                      |
| crtl wr             | rotaciona janelas                    |
| ctr w x             | inverte janela com a próxima         |
| ctr w X             | inverte janela com anterior          |
| ctrl w+             | aumenta espaço da janela             |
| ctrl w-             | diminui espaço da janela             |
| ctrl w=             | mesmo tamanho para todas janelas     |
| ctrl w\_            | maximizar na horizontal              |
| ctrl w              | maximizar na vertical                |
| :hide               | esconde a janela sem fechar buffer   |
| :wall               | salva todas janelas abertas          |
| :qall               | sai de todas janelas                 |
| :res +5             | aumenta janela horizonal 5           |
| :resize 60          | janela horizontal 60                 |
| :vertical resize 80 |
| :vertical resize +5 |

## Comandos de manipulação de abas

| Comando     | Função                   |
| ----------- | ------------------------ |
| tabnew file | abre arquivo em nova aba |
| tabnext     | avanca proxima aba       |
| tabprevios  | retorna aba anterior     |

## Comandos de ações no modo normal

| Comando     | Função                                  |
| ----------- | --------------------------------------- |
| .           | repete ultimo comando                   |
| viw         | seleciona palavra inteira (cursor nela) |
| vis         | seleciona sentença (cursor nela)        |
| vip         | seleciona paragrafo (cursor nela)       |
| vat         | seleciona ao redor da tag (tag inteira) |
| va{         | seleciona dentro os {}                  |
| vitc        | Altera texto dentro da tag              |
| vi{c        | Altera texto dentro das aspas           |
| vi(c        | Altera texto dentro do parenteses       |
| d           | deletar ou copiar caracter              |
| dd          | recortar ou apagar linha                |
| y           | copiar                                  |
| yy          | copiar linha                            |
| p           | colar abaixo                            |
| P           | colar acima                             |
| .w !xsel -b | colar linha no clipBoard                |
| w !xsel -b  | colar seleção visual no clipBoard       |
| S           | cola sobrescrevendo a linha toda        |
| u           | desfazer (undo)                         |
| x           | apagar uma letra                        |
| o           | insert na linha abaixo (nova linha)     |
| O           | insert na linha acima (nova linha)      |
| i           | inserir                                 |
| I           | inserir no inicio da linha atua         |
| a           | inserir apos caracter atual             |
| A           | inserir no final da lina atual          |
| di          | deletar dentro                          |
| yi          | copiar dentro                           |
| v           | visual / seleção                        |
| /           | buscar (find) n proxima ocorrencia      |
| /;j         | tirar highlight da busca anterior       |
| //          | repete ultima busca                     |
| %           | busca fechamento de parenteses ou chave |
| :s          | substituir (replace)                    |
| :50         | vai para linha 50                       |
| 50gg        | vai para linha 50                       |
| J           | junta linhas (remove breakline)         |
| ZZ          | sai do arquivo e salva                  |
| ~           | alterna maisculas e minusculas          |
| :history    | lista comandos anteriores (só lista)    |
| q:          | escolher e alterar comando anterior     |
| gx          | abre url corrente no browser            |

## Comandos de movimentação no modo normal

| Comando | Função                                |
| ------- | ------------------------------------- |
| gg      | vai pra linha 1 do arquivo            |
| G       | fim do arquivo                        |
| ctrl f  | page foward                           |
| ctrl b  | page back                             |
| nG      | pular para linha n                    |
| \$      | fim da linha                          |
| 0       | inicio da linha                       |
| e       | fim da palavra atual                  |
| b       | incio palavra anterior                |
| w       | inicio proxima palavra                |
| hjkl    | esquerda baixo cima direita           |
| )       | avançar uma frase                     |
| }       | avançar um parágrafo                  |
| H       | vai para primeiro caracter da tela    |
| M       | poe cursor no meio da tela            |
| L       | vai para ultima linha da tela         |
| -       | salta proxima ocorrencia da palavra   |
| \#      | salta p/ ultima ocorrencia da palavra |
| zt      | cursor no topo da pagina              |
| zm      | cursor no fim da pagina               |
| %       | localiza inicio fim de { (            |

## Comandos de alterações no modo normal

| Comando    | Função                             |
| ---------- | ---------------------------------- |
| g,         | avança lista de alteraçoes         |
| g;         | retrocede lista de alterações      |
| u          | desfaz ultima mudança              |
| :changes   | ver lista de alterações            |
| :h changes | lista de alterações detalhadas     |
| UU         | desfaz mudanças da linha editada   |
| ctrl -r    | refaz mudanças desfeitas undo undo |

## Atalhos de teclado no modo de inserção (insert)

| Atalho        | Ação                                    |
| ------------- | --------------------------------------- |
| ctrl y        | copia caracter caracter linha acima     |
| ctrl e        | copia caracter caracter linha abaixo    |
| ctrl w ctrl f | abre arquivo sob cursor na janela atual |
| Shift insert  | inserir texto da area de transferencia  |

## Comandos do modo visual

| Comandos | Função                                   |
| -------- | ---------------------------------------- |
| v        | seleção de caracteres                    |
| V        | selecão de linhas inteiras               |
| Ctrl V   | seleção de blocos                        |
| d        | deleta selecao                           |
| y        | copia selecao                            |
| c        | altera caracteres                        |
| gu       | minusculas                               |
| shift i  | Insert text (press esc esc after insert) |

## Comandos Marcas

| Comandos | Função                      |
| -------- | --------------------------- |
| ma       | cria marca a em modo normal |
| 'a       | move cursor até marca a     |
| d'a      | delete ate a marca a        |
| y'a      | copia ate a marca a         |

## Exemplos de comandos

| Comando         | Ação                                  |
| --------------- | ------------------------------------- |
| jVG:normal.     | repete comando ant tdas linhas abaixo |
| d\$             | apaga até o final da linha            |
| d^              | apaga até o inicio da linha           |
| dG              | apagar até o final do arquivo         |
| dl              | apagar uma letra                      |
| D               | apagar resto da linha                 |
| d3j             | deletar 3 linhas abaixo               |
| yw              | copiar prox. palavra cursor no inicio |
| yiW             | copiar palavra curso no meio          |
| 10j             | avançar 10 linhas                     |
| di}             | apagar tudo dentro das chaves         |
| 2{              | subir 2 paragrafos                    |
| 5p              | colar selecao atual 5 vezes           |
| i               | Editar onde o cursor está             |
| ayy             | copia linha atual para registrador a  |
| ap              | cola registrador a                    |
| fx              | vai ate proxima ocorrencia de x       |
| dfx             | deleta ate proxima ocorrencia de x    |
| ctrl f          | page foward                           |
| ctrl b          | page back                             |
| gi              | insert no ultimo ponto de edição      |
| gv              | repete ultima selecao visual          |
| gf              | abre arquivo sob o cursor             |
| :s:/foo/bar     | substitui foo por bar na linha atual  |
| :1,10 s/foo/bar | substitui foo por bar até a 10a linha |
| :% s/foo/bar    | substitui foo por bar no arquivo todo |
| :1,\$ s/foo/bar | substitui foo por bar no arquivo todo |

## Comandos externos executados em modo normal

| Comando  | Ação                                |
| -------- | ----------------------------------- |
| pwd      | mostra diretorio atual              |
| cd /path | vai para novo diretorio             |
| cd %:p:h | vai para diretorio do arquivo atual |

## Comandos de folding

| Comando | Função                  |
| ------- | ----------------------- |
| za      | abre e fecha fold       |
| zR      | abre todos os foldings  |
| zM      | fecha todos os foldings |
| zi      | enable/disable folding  |

## Comandos plugin Surround

| Comandos | #vim Surround plugin    |
| -------- | ----------------------- |
| cs"'     | change "h" to 'h'       |
| cs'<q>   | change to <q>h<h>       |
| cst      | remove tag inside obj   |
| cs}      | { text }                |
| cs{      | {text}                  |
| ds"      | remove ""               |
| ysiw]    | [] around the word      |
| yss)     | ([x])                   |
| VS<p>    | <p>text</p> visual mode |
| ysiw<em> | text <em>text</em>      |
| ds{ds)   | remove {} and ()        |

## Configurações

- `set fileformat=dos`
- `set fileformat=unix`
- `set fileformat=mac`
- `set number` Show line numbers
onumber` Hide line numbers
- `set relativenumber` Set relative linenumber
- `set norelativenumber` unset relative linenumber

## Recarregar arquivo de configurações:

`:so %`

## Comandos plugin Prettier

| Comando | Função            |
| ------- | ----------------- |
| f5      | formata documento |

## Configurando vim como default editor:

### at user level:

`bash echo "alias editor=vim" >> ~/.bashrc`

### at system wide:

`bash sudo update-alternatives --config editor`

## Solução para travamento do vim (Ctrl s)

`Ctrl Q` Unfreeze VIM

## Mapeamento de atalhos

| Atalho | Função                      |
| ------ | --------------------------- |
| :zj    | Create new line normal mode |
| :zk    | Create new line normal mode |
| `<F2>` | Bprevius                    |
| `<F3>` | Bnext                       |
| Ctrl P | FZF                         |

## NerdTree

| Comando | função                                                  |
| ------- | ------------------------------------------------------- |
| t       | Open the selected file in a new tab                     |
| i       | Open the selected file in a horizontal split window     |
| s       | Open the selected file in a vertical split window       |
| I       | Toggle hidden files                                     |
| m       | Show the NERD Tree menu                                 |
| R       | Refresh the tree, useful if files change outside of Vim |
| ?       | Toggle NERD Tree's quick help                           |

## Vim maps

| Comando        | função               |
| -------------- | -------------------- |
| <F2>           | Nerdtree Find        |
| <F4>           | Nerdtree Toggle      |
| ,f             | Rgrep                |
| ,sh            | terminal             |
| :FixWhitespace | %s/\s\+\$//          |
| Cr -w          | Delete line          |
| ,h             | split                |
| ,v             | vsplit               |
| ,ga            | Git add              |
| ,gc            | Git Commit           |
| ,gsh           | Git push             |
| ,gll           | Git pull             |
| ,gs            | Git status           |
| ,gb            | Git Blame            |
| ,gd            | Git diff             |
| ,gr            | Git remove           |
| ,so            | Open Session         |
| ,ss            | Save Session         |
| ,sd            | Delete Session       |
| ,sc            | Close Session        |
| Shift t        | :tabnew              |
| ,.             | Working dir          |
| ,e             | edit command         |
| ,te            | :tabe                |
| <c-p> <c-r>    | fzf expand           |
| ,b             | :buffers             |
| ,e             | :FZF -m              |
| ,y             | :history             |
| ,z             | :bp                  |
| ,q             | :bp                  |
| ,x             | :bn                  |
| ,w             | :bn                  |
| ,c             | :bd                  |
| ,space         | noh                  |
| ,o             | .Gbrowse             |
| ,dd            | go-def-vertical      |
| ,dv            | go-doc-vertical      |
| ,db            | go-doc-browser       |
| ,r             | go-run               |
| ,t             | go-test              |
| ,gt            | go-coverage-toggle   |
| ,i             | go-info              |
| ,l             | go-linter            |
| Crl-g          | :GoDecls             |
| .dr            | :GoDeclsDir          |
| Crl-g esc      | :GoDecls             |
| esc C-u        | :GoDeclsDir          |
| ,rb :          | :Build-Go-Files      |
| :Crl-u         | :Buid-go-files       |
| Crl-l          | Toogle line Numbers  |
| ,py            | prettier             |
| <F9>           | prettierAsync        |
| zj             | o<esc>k              |
| zk             | O<esc>j              |
| ]r             | Next ale Warning     |
| [r             | previous ale warning |

:GenTocGitlab ,
:GenTocMarked
:UpdateToc
:GenTocGFM
:GenTocRedcarpet

:gcc comment a line
:gc commnet a target

| ## Default Vim 8 Color Schemes

- blue.vim
- darkblue.vim
- delek.vim
- desert.vim
- elflord.vim
- evening.vim
- industry.vim
- koehler.vim
- morning.vim
- murphy.vim
- pablo.vim
- peachpuff.vim
- ron.vim:
- shine.vim
- slate.vim
- torte.vim
- zellner.vim

[[vim-alan-map]
