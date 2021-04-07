# Linux Tips

## Table of contents

- [Linux Tips](#linux-tips)
  - [Table of contents](#table-of-contents)
  - [Arquivos](#arquivos)
    - [Localização de arquivos](#localização-de-arquivos)
    - [Manipulação de Arquivos](#manipulação-de-arquivos)
    - [File descriptors](#file-descriptors)
  - [Atalhos e pipes](#atalhos-e-pipes)
  - [Comandos de compilação](#comandos-de-compilação)
  - [Compactação de arquivos](#compactação-de-arquivos)
  - [Instalador APT](#instalador-apt)
    - [Adicionar PPA](#adicionar-ppa)
    - [Exportar lista de pacotes instalados e restaurar em nova instalação](#exportar-lista-de-pacotes-instalados-e-restaurar-em-nova-instalação)
  - [Monitoramento de processos](#monitoramento-de-processos)
  - [Networking](#networking)
    - [WIFI](#wifi)
  - [Redirecionamento de Comandos com pipe](#redirecionamento-de-comandos-com-pipe)
    - [Redirecionar a saida de um comando p/ outro c/ xclip](#redirecionar-a-saida-de-um-comando-p-outro-c-xclip)
  - [Shell - Programas](#shell---programas)
  - [Usuários e permissões](#usuários-e-permissões)
    - [Alteração de permissões de arquivo em lote](#alteração-de-permissões-de-arquivo-em-lote)
  - [Serviços](#serviços)
  - [SSH](#ssh)
  - [Bash tricks](#bash-tricks)
    - [Aliases legais](#aliases-legais)
  - [Crontab](#crontab)
  - [Monitoramento de disco](#monitoramento-de-disco)


## Arquivos

### Localização de arquivos

| Comando  | Função             |
| -------- | ------------------ |
| `locate` | localizar arquivo  |
| `which`  | localizar programa |
| `grep`   | Find in files      |
| `pwd`    | diretorio atual    |

### Manipulação de Arquivos

| Comando                       | Função                                                 |
| ----------------------------- | ------------------------------------------------------ |
| `touch`                       | criar arquivo                                          |
| `cat`                         | ler arquivo                                            |
| `head`                        | ler 10 linhas inicio arquivo                           |
| `tail`                        | ler 10 linhas final arquivo                            |
| `more`                        | ler arquivo c/ paginação p/ fim                        |
| `less`                        | ler arquivo c/ paginacao inicio/fim (ler pdf no xterm) |
| `wc -w file`                  | Conta palavras ou linhas                               |
| `rmdir`                       | Deletar diretório vazio                                |
| `du - h`                      | Saber tamanho de diretório ou arquivo                  |
| `ln -s lib.so.2 lib.so.1`     | Sistema só tem a lib.so2. apontar lib.so1 p/ ela.      |
| `ln -sf alvo Atalho`          | Cria link simbolico (atalho) para alvo                 |
| `cal -3`                      | Calendario ultimos 3 meses                             |
| `cal -m 6 -3`                 | Calendario maio/junho/julho                            |
| `bc 2+2`                      | Calcula 2+2                                            |
| `tail -f  /var/log/syslog`    | Ver arquivo em tempo real                              |
| `tail -n 100 /var/log/syslog` | Ver ultimas 100 linhas do arquivo                      |

Copiar arquivo para diretório em que está usando ponto: 
`cp /var/log/syslog  .`

Trabalhando com multiplos diretórios: 
`mv dir1 dir2 dir3 /path/to/destiny`

### File descriptors

stderr: Mensagens de erro: 2
stdout: Mensagens de sucesso: 1

Exemplos:

```bash
find / -name "syslog" 1> stout.txt 2 > stderr.txt
find / -name "syslog" 1> stout.txt 2 > /dev/null
find / -nmae "syslog 2 > /dev/null
```

## Atalhos e pipes

| Comando                 | Função                              |
| ----------------------- | ----------------------------------- |
| `tecla tab`             | completa comando                    |
| `Control W`             | Apaga ultima palavra                |
| `Control U`             | Apaga linha inteira                 |
| `Control D`             | Logout                              |
| `!!`                    | repete ultimo comando               |
| `comando1; comando2`    | executa 2 comandos                  |
| `comando1 && comando2`  | executa 2 comandos na sequencia     |
| `comando1 || comando 2` | executa comando2 se comando1 falhar |

## Comandos de compilação

```bash
./configure
make
make install / make uninstall
```

## Compactação de arquivos

| `zip -qc`                        | compact file                                |
| `tar -czvf file.tar.gz file`     | compactar,zip,verbose,arquivo .tar.gz       |
| `tar -xzvf file.tar.gz`          | extract,zip,verbose,arquivo                 |
| `tar -tf file.tar.gz`            | test(list),arquivo                          |

## Instalador APT

| Comando                    | Função                         |
| -------------------------- | ------------------------------ |
| `apt-get install`          | Instala programa               |
| `apt-get update`           | Atualiza cache lista programas |
| `apt-get remove`           | Remove programa                |
| `apt-cache search`         | Procura programa para instalar |
| `apt list --upgradeable`   | lista atualizações p/ instalar |
| `apt-get upgrade`          | Instala atualizações           |
| `dpkg -i file`             | instala pacote .deb            |
| `dpkg -r file`             | remove pacote .deb             |
| `Sudo snap search` pacote  | Procura snap                   |
| `Sudo snap install` pacote | Adiciona snap                  |
| `Sudo snap remove` pacote  | Remove snap                    |

### Adicionar PPA

`sudo apt-add-repository ppa:username/myawesomesoftware-1.0`

### Exportar lista de pacotes instalados e restaurar em nova instalação

```bash
# exportação
sudo apt-get update
dpkg --get-selections > package.list
# importação
sudo apt update
sudo apt install dselect
sudo dselect update  
sudo dpkg --set-selections < packages.list  
sudo apt-get dselect-upgrade
```

## Monitoramento de processos

| Comando                              | Função                                |
| ------------------------------------ | ------------------------------------- |
| `top`                                | CPU/Memory State                      |
| `ps -ef`                             | Listar processos usuário              |
| `ps aux`                             | Listar todos processos usuário        |
| `ps u -C apache`                     | Listar processos que tem apache       |
| `ps aux --sort=-pcpu`                | Listar processos por uso de cpu       |
| `ps aux --sort=-pcpu pipe| head -n5` | Listar processos por uso de cpu       |
| `ps aux --sort=-pmem pipe| head -n5` | Listar processos por uso de ram       |
| `ps aux -l`                          | Listar processos PRI(oridade)  NI(ce) |
| `renice -n 10 -p 41267`              | altera prioridade de processo         |
| `nice -n 10 vim`                     | abre vim com prioridade 10            |
| `sudo nice -n -10 vim`               | aumenta prioridade do processo p/ 10  |
| `killall -s9`                        | Kill proccess tree                    |
| `df -h`                              | status espaço em disco                |
| `free -h`                            | status uso memória                    |

## Networking

| Comando                                    | Função                              |
| ------------------------------------------ | ----------------------------------- |
| `ssh-import-id-gh <username>`              | importa chave ssh do github (ubuntu |
| `ip if=eth0 && sudo ip link set \$if down` | Desabilita interface                |
| `ip addr`                                  | Ver interfaces de rede              |
| `wget url`                                 | download de arquivo da internet     |

### WIFI

| Comando                           | Função                             |
| --------------------------------- | ---------------------------------- |
| `nmcli dev wifi list`             | List wi-fi networks                |
| `mcli dev wifi con my-ssid pwd`   | connect to a network               |
| `nmcli dev`                       | show network interfaces and status |
| `nmcli d`                         | show network interfaces and status |
| `nmcli r wifi on`                 | Start wifi                         |
| `nmcli c add type wifi ssid-name` | add a connection                   |
| `nmcli c modify <PAR>`            | change a connection                |
| `nmcli c up`                      | up a connection                    |
| `nmcli con down ssid`             | disconnnect from AP                |

## Redirecionamento de Comandos com pipe

```bash
 echo "2+2"; echo "3*3" | bc       # Calcula 2+2 e 3*3
 pwd | xsel -b                     # Copia pat para clipboard
 xsel -b                           # Cola path ond está cursor
 wc -w *.txt | grep total          # Conta palavras de arquivos.txt e totaliza
 history | less                    # comandos já digitados
 dmesg | less                      # Log inicialização
 ps -e | wc -l                     # Conta quantos tem rodando no sistema
```

### Redirecionar a saida de um comando p/ outro c/ xclip

```bash
# Instalar o xclip: 
sudo apt-get install xclip
# criar aliases: 
alias c='xclip'
alias v='xclip -o'
```

Exemplo:

```basH
pwd | c
cd (v)
```

## Shell - Programas

| Comando                      | Função                                    |
| ---------------------------- | ----------------------------------------- |
| `program &`                  | iniciar program em background             |
| `program > /dev/null &`      | programa em backgrond sem msgs na tela    |
| `program & > /dev/null 2>&1` | programa em bg sem msgs normais e de erro |
| `jobs (fg, bg)`              | front/background files                    |
| `env |grep path`             | Show path                                 |
| `path=$path:/fs`             | Add /fs to the path                       |

## Usuários e permissões

| Comando                          | Função                                      |
| -------------------------------- | ------------------------------------------- |
| `adduser`                        | Adicionar usuário                           |
| `useradd`                        | Adicionar usuário                           |
| `userdel`                        | Deletar usuário                             |
| `usermod -a -G thegroup theuser` | Adiciona usuário a um grupo                 |
| `paswd username`                 | Altera senha do usuário                     |
| `paswd -l username`              | bloqueia usuário                            |
| `groups theuser`                 | Lista grupos do usuário                     |
| `groupadd user group`            | adiciona grupo ao usuário                   |
| `groupdel user group`            | adiciona usuario ao grupo                   |
| `gpasswd`                        | adicionar / remove grupo do usuário         |
| `Usermod -l`                     | rename login                                |
| `usermod`                        | move home para outro usuário                |
| `Chage -l`                       | view password expiration                    |
| `Chage -M 90`                    | (set expiration password 90 dd              |
| `Chage -m 5` (five caracters)    |
| `chmod -ugoa+rwx file`           | Modificar permissões de arquivo (ex: total) |
| `whoami`                         | Usuário atual logado                        |
| `4 read 2 write 1 execute`       | Octal mode                                  |
| `chmod 755 file or dir`          | user (all), Group (rx) others (rx)          |
| `chmod 777 file or dir`          | user (all), Group (all others (all)         |
| `chmod 400 file or dir`          | user (r) group (none) others (none)         |
| `chmod 775 file or dir`          | user (All) group (all), others(x)           |
| `chown`                          | mudar usuário, grupo do arquivo             |

### Alteração de permissões de arquivo em lote

```bash
# Altera permissão somente de arquivos no path
find /path/to/dir/ -type f -exec chmod 644 {} \\;
# Altera permissão somente de diretorios no path
find /path/to/dir/ -type d -exec chmod 755 {} \\;
```

Para copiar arquivos para todos novos usuários criados, colocar no diretorio `/etc/skel`

Para implementar política de senhas ver configurações em `/etc/pam.d`

## Serviços

| Comando                          | Função                                |
| -------------------------------- | ------------------------------------- |
| `/etc/init.d/`                   | system services dir                   |
| `service file stop/start/status` | services /etc/init.d/                 |
| `/etc/init.d file start/stop`    | start/finish service from etc/init.d/ |
| `systemctl | grep ssh`           | list ssh service                      |
| `systemctl status ssh`           | list ssh service status               |
| `systemctl start, stop, restart` | Inicia ou para serviços               |
| `systemctl enable,disable`       | habilita serviço p/ iniciar no boot   |
| `systemctl enable --now ssh`     | habilita p/ iniciar no boot e inicia  |

## SSH

Para liberar SSH para root ir em /etc/ssh/ssh.conf

## Bash tricks

- Para ver o histórico:  `history`
- Para chamar um comando do historico `!numeroDocomando`
- Para apagar um comando do histórico `history -d numeroDocomando`
- Para não incluir um comando no histórico, dar um espaço antes do comando

Em distribuições que não estão configuradas p/ ignorar histórico com um espaço, incluir no `.bashrc` o comando `HISTCONTROL=ignoreboth`

**Esqueceu de dar sudo antes do comando?** Experimente `sudo !!`  para repetir o comando com sudo. 

**Autocompletar:** usar 2 tabs

Control R  - procura no histórico do bash

A diferença entre encadear comandos com && e ; é que com ; o segundo comando executa mesmo se primeiro não for bem sucedido.

### Aliases legais

```bash
alias cpu10='ps -L aux | sort -nr -k 3 |head -10'
alias mem10='ps -L aux | sort -nr -k 4 |head -10'
alias lsmount='mount |column -t'
```

## Crontab

Listar job: `crontab -l`
criar job: `crontab -e`

```code
minuto  hora  dia   mes   diaSemana       comando
0-60    0-23  1-31  1-12  0-6(sunday-sat) comando
```

## Monitoramento de disco

| Comando         | Função                           |
| --------------- | -------------------------------- |
| `df -i`         | verificar inodes                 |
| `df -h`         | verificar espaço utilizado       |
| `du -hsc *`     | Directory usage                  |
| `fdisk -l`      | list devices                     |
| `fdisk`         | create partition table/partition |
| `lsblk`         | list devices                     |
| `mkfs.ext4`     | Format disk partition            |
| `blkid`         | show uuid for devices            |
| `sudo mount -a` | Mount any fstab entries          |

Fstab formato:

```bash
device     mount point  fstype options   dump check
/dev/sdb1  /mnt/vol1     ext4  defaults  0       0 
```

- check = 0 não checa
- check = 1 checa em caso de erros
- check = 1 checa em todo boot

Verificar espaço em disco amigável: 

Ncurses disk usage: `sudo apt-get install ncdu`

O numero de inodes é limitado por device. As vezes um disco pode conter milhões de arquivos pequenos, usar pouco espaço mas acabar com os inodes disponíveis.

 /dev/nu