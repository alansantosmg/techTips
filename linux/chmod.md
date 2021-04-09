# Permissões Linux

```txt

Nível      u   g   o
Permissão rwx r-x ---
Binário   111 101 000
Octal      7   5   0

```

## Para arquivos (-)
rwx 
000  0  (zero) permissão negada
001  1   permissão de execução
010  2   permissão de gravação
011  3   permissão de gravação e execução
100  4   permissão de leitura
101  5   permissão de leitura e execução
110  6   permissão de leitura e gravação
111  7   soma de todas as permissões

## Para diretórios (d)
rwx
000  0  (zero) permissão negada
001  1   permissão para entrar no diretório
010  2   permissão para gravar dentro do diretório
011  3   permissão de entrar e gravar no diretório
100  4   permissão para listar o conteúdo do diretório
101  5   permissão de listar e entrar no diretório
110  6   permissão de listar e gravar no diretório
111  7   soma de todas as permissões

## chmod command

```bash

chmod o+rwx arquivo.extensao
chmod ugoa-rxw arquivo.extensao

```

### chmod options:

- u = user
- g = group
- o = other
- a = all
- -R recursive
- -c changes
- -f silent
