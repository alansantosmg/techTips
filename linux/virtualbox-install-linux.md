# Corrigir erro secure boot virtual box linux

Abra o terminal e instale o virtualbox com apt-get install virtualbox (ignore os avisos e pedidos para desativar o boot seguro do UEFI)

Crie um “par de chaves X.509”:

```bash
openssl req -new -x509 -newkey rsa:2048 -keyout vboxdrv.priv -outform DER -out vboxdrv.der -nodes -days 36500 -subj "/CN=MySelf/"
```

Assine o módulo do virtualbox:

```bash
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./vboxdrv.priv ./vboxdrv.der $(modinfo -n vboxdrv)
```

Importe a chave pública gerada com: 

`sudo mokutil --import vboxdrv.der`

## rodar script abaixo apos atualizar o kernel

```bash
#!/bin/bash
CERTDIR="/path/to/certs"
/usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 $CERTDIR/vboxdrv.priv $CERTDIR/vboxdrv.der $(modinfo -n vboxdrv)
/sbin/modprobe vboxdrv
```
