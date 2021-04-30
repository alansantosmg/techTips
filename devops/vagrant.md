# vagrant

## Requisitos

1. Ter um provider instalado (vmware, hyperv ou Virtualbox)
2. Instalar o vagrant
3. criar a pasta ambiente_dev
4. ir para pasta ambiente dev
5. Criar a pasta da vm

### Comandos básicos

```bash
vagrant up  hashicorp/bionic
vagrant halt
vagrant reload
vagrant destroy -f 
vagrand ssh
```

## Criando chave ssh para rodar o vagrant

### Cenário

Neste cenário nós temos:

Maquina virtual linux  bionic (Guest) provisionada com vagrant num (host)
/home/user_name/ambiente_dev/bionic

### Procedimentos no host:

```bash

ssh-keygen
~/ambiente_dev/bionic/id_mybionickey
cd ~/.ssh/id_mybionickey.pub ~/ambiente_dev/bionic

```

### no Guest

Na pasta bionic do guest entrar: `vagrant ssh`

Copiar chave no guest:

```bash
cp ~/ambiente_dev/bionic/id_mybionickey.pub .
```

Adicionar chave no guest:

```bash
cat ~/id_mybionickey.pub >> .ssh/authorized_keys
```

ir para host e testar conexão:

```bash
ssh -i id_mybionickey vagrant@IP-DO-GUEST:
```

## Vagrant file - Exemplo

```ruby
Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"

    # redirect port 8089 on host to port 80 on the guest
    #
    # Apos instalar um webserver guest, no browser do host
    # entre com: localhost:8089 para acessar o webserver do guest
    config.vm.network "forwarded_port", guest:80, host:8089
    
    # Configura interface de rede host-guest only
    #config.vm.network "private_network", ip: "192.168.50.10"

    # Configura interface de rede com DHCP do provider (vbox)
    #config.vm.network "private_network", type: "dhcp"

    # Configura interface de rede pública em modo bridge
    # se nao especificar ip, pegará ip da rede
    # se especificar ip ele fica fixo - Lembrar de fazer reserva dhcp server
    config.vm.network "public_network", ip: "192.168.2.103", bridge: "wlo1"
  end
  ```

