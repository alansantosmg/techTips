# Criar folder compartilhado entre windows e Linux no HyperV

1. No linux - Instalar o cifs:  `sudo apt install cifs-utils`
2. No linux - Criar pasta sharedFolder no home dir: `mkdir ~/sharedFolder`
3. No Windows - Criar pasta sharedFolder em c:\ `md c:\sharedFolder`
4. No Widnows - Criar usuário linuxFolder
5. No Windows - Definir senha para usuário linuxFolder
6. No Windows - Compartilhar pasta SharedFolder
7. No Windows - Dar permissão no compartilhamento p/ usuário linuxFolder
8. No linux -  Executar o comando:
`sudo mount.cifs //nomeDaMaquina/sharedFolder ~/github.com/sharedFolder -o user=linuxFolder`
9. No linux - Digitar a senha quando solicitado
