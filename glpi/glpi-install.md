
# Instalação GLPI

## instalação SSH server



Verificar se ssh server está instalado e ativo:
```
systemctl status sshd
```

Caso não esteja instalado, instalar: 
```
sudo apt-get install openssh-server
systemctl status sshd
```

---

## Instalação de requisitos

```
sudo apt install mariadb-server
sudo apt-get -y install apache2 libapache2-mod-php
sudo apt-get -y install php php-{curl,gd,imagick,intl,apcu,memcache,imap,mysql,cas,ldap,tidy,pear,xmlrpc,pspell,mbstring,json,common,xml,gd}
```

## Parametrização mysql

```
sudo mysql_secure_installation
```


* Digitar enter p/ acessar mysql (senha em branco root)
* Definir senha de root para mysql
* Remover acesso anonymo para produção
* Nao permitir conexão remota de root
* Remover base de teste
* Recarregar privilégio das


### Privilégios de root no mysql
```
sudo mysql -u root -p
```

### Script para permissão de root no mysql
```
UPDATE mysql.user SET plugin = 'mysql_native_password' WHERE User = 'root';
FLUSH PRIVILEGES;
QUIT;
```


### Configurar extensões faltantes do PHP
```
sudo vim /etc/php/7.4/apache2/php.ini
```

Descomentar as extensões: 
* extension=curl
* extension=gd2
* extension=imap
* extension=ldap
* extension=mbstring
* extension=mysqli
* extension=xmlrpc
* extension=xsl

### Habilitar extensões novas no PHP
```
sudo service apache2 restart
```

---

## Instalação GLPI

### Criação de base de dados do GLPI 
```
mysql -u root -p
```

#### Script para criação de base no GLPI
```
CREATE DATABASE glpi;
CREATE USER 'glpi'@'localhost' IDENTIFIED BY 'StrongDBPassword';
GRANT ALL PRIVILEGES ON glpi.* TO 'glpi'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```


### Instalação do software GLPI

```
cd ~
export VER="9.4.6"
wget https://github.com/glpi-project/glpi/releases/download/$VER/glpi-$VER.tgz
tar xvf glpi-$VER.tgz
sudo mv glpi /var/www/html/
```

#### Setar permissoes Apache GLPI
```
cd /var/www/html/glpi
chmod 755 files -R
sudo chown -R www-data files
chmod 755 config -R
sudo chown -R www-data config
```

### Configurar GPLI

Acessar via browser  ```10.0.0.212/gpli/install```

#### Dados para configuração inicial
* Database = gpli
* servidor de banco de dados: 127.0.0.1
* senha de conexão: usar a senha do database do GLPI

#### Acesso inicial GPLI
* user: glpi
* password: glpi


#### Remover arquivo de instalação do GLPI

```
rm /var/www/html/glpi/install/install.php
```

#### Alterar senha para usuários
Alterar senha dos usuários padrão criados pelo GLPI na interface do programa: 
* normal
* tech
* post-only
* glpi


#### Dados para sincronização LDAP
* criar usuário glpi no Active directory e atribuir uma senha
* Acessar GLPI como administrador
* Ir em: Configurar -> autenticação -> Diretórios LDAP

Parametros: 

nome: `acotel.local`

servidor: `10.0.0.201`

Filtro de Conexão: `(&(objectClass=user)(objectCategory=person))`

Porta ldap: `389`

base dn: `dc=acotel,dc=local`

root dn: `acotel\glpi`

senha: senha do usuario glpi do AD

campo de login: `samaccountname`

#### Importar usuários do AD
* Ir em Administração -> usuários -> link do diretorio ldap
* Ir em importar novos usuários
* Ir em avançado


baseDN: `dc=acotel,dc=local`

pesquisar `filtros para usuários: (& (samaccountname=*) )`


* Clicar em pesquisar
* Marcar usuários na lista
* Clicar em ação
* Selecionar importar no combo box. 
* Dar ok e aguardar importação



### Instalação do fusion inventory plugin
```
cd ~
wget https://github.com/fusioninventory/fusioninventory-for-glpi/releases/download/glpi9.4%2B2.4/fusioninventory-9.4+2.4.tar.bz2
tar -jxvf fusioninventory-9.4+2.4.tar.bz2
mv fusioninventory /var/www/html/glpi/plugins
```


### Ativar o plugin no GLPI
Configurar -> Plugins -> fusioninventory +

Após configurar, habilitar o plugin
