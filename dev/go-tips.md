# Go Tips


## Workflow Go projects

1. Criar git branch p/ feature ou correção
2. Criar o teste
3. GoFmt; GoImports; GoLint
4. Rodar o teste e ver falhar
5. Escrever e compilar código sem erros
6. GoFmt; GoImports; GoLint
7. Rodar o teste e ver falhar - Observar erro
8. Escrever o mínimo de código para teste passar
9. GoFmt; GoImports; GoLint
10. Rodar o teste e obter Ok
11. Git add, Git Commit
12. Git merge feature to master
13. Ao final da feature ou correção: git push origin master

## Consulta documentação

[Packages buit-in](https://golang.org/pkg)
[Go CLI Commands](https://golang.org/cmd)


## Basic Go program

Hello World!  
[Programa básico](https://play.golang.org/p/HmnNoBf0p1z)


## Separação de domínios

Separar um programa em domínios facilita testá-lo e também em dividi-lo em partes menores e mais lógicas. 

[Exemplo 1 - Separação de domínios - Hello World](https://play.golang.org/p/AEsLuSs7EL3)



## Instalação do GO

### Linux

Go é instalado em `usr/local/bin`.  
O workspace do usuário normalmente é em `/home/username/go`.

#### Ajustar ambiente (GOPATH e GOROOT)


Adicionar ao arquivo  `.profile` do usuário:

```go
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

## GO Doc

### Instalar Go Doc

[Sobre Go doc](https://www.bswen.com/2020/07/How-to-install-godoc-tool-for-golang.html)

#### Windows
 `go get -v  golang.org/x/tools/cmd/godoc`

#### Linux
```go
cd / $GOPATH/src/golang.org/x/tools/cmd/godoc
go build -o $GOPATH/bin/godoc
```

### Acessar o godoc

`godoc -http=localhost:6060`

## Peculiaridades do GO

* Go não compila se houver pacotes importados e variáveis não utilizados.
* Go não compila se faltar o pacote de alguma função
* Go não usa ; para separa sentenças. O compilador coloca o ; onde for necessário.
* Go não usa parênteses para declarar condições em if ou switch
* Go não usa break para sair de switchs
* Go pode retornar n valores de uma função
* Go pode aceitar n argumentos para uma função
* O método Println não precisa de espaço na separação de argumentos

## trabalhando com módulos

### Estrutura de pastas para módulos

* Para criar um módulo digite  `go init mymodule`. Será criado arquivo go.mod
* A seguir crie arquivo `main.go` por padrão.
* O conteúdo do arquivo main.go deve iniciar com `package main`.
* Para criar sub-módulos, crie a pasta dos mesmos
* Dentro da pasta do sub-módulo, crie os arquivos do sub-módulo
* Os arquivos do sub-modulo tem que iniciar com `package nome-do-submódulo`.
* No arquivo main.go inclua no import `"nomeDoModulo/nomeDoSub-módulo"`.
* Compile com o comando go-build

#### Módulos externos

* Na pasta do módulo dar o comando go get endereço do pacote.
* Pacote sera registrado no go.mod
* ATENÇÃO: não ficar alterando manualmente o go.mod.

#### Remover dependencias não usadas

* `go mod tidy`

#### Referenciar módulos

* Incluir o caminho completo do módulo externo, incluindo domínio no import
* Ao chamar função do módulo, chamar sempre a referencia depois da última barra do import.

## Go command line

### GO fmt 
Formata documentos recursivamente

`go fmt ./...`

## Tipos primitivos 

### Tipos númericos

```text
Type Range Storage
int8     –128 to 127
8-bit    (one byte)
uint8    0 to 255
int16    –32,768 to 32,767
16-bit   (two bytes)
uint16   0 to 65535
int32    –2,147,483,648 to 2,147,483,647
32-bit   (four bytes)
uint32   0 to 4,294,967,295
int64    –9,223,372,036,854,775,808 to
         9,223,372,036,854,775,807 64-bit (eight bytes)
uint64   0 to 18,446,744,073,709,551,615
```

**Atenção Atenção Atenção:**
Se você atribuir valor superior ao limite de um tipo, ocorrerá overflow.

Porém, se você adicionar um número além do limite de um valor já atribuído, aquele int irá zerar e começará a contar de novo! 

### Strings

```go
// remove espaços antes de depois de uma cadeia de  caracteres
strings.Trim(v)
// converte strings para minusculas
strings.ToLower(v)

```

#### Declarando strings

```go
// Mais facil declarar como Raw
comment1 := `In "Windows" the user directory is "C:\Users\"`

// Declarando interpretado precisa de escape "\" p/ carecteres especiais
comment2 := "In \"Windows\" the user directory is \"C:\\Users\\\""
```

#### Verbos para formatação de strings

```go
%15v %-15v  formata o texto para direita ou esquerda
\n          line feed
\"          Representa " dentro de uma string interpretada
\t          tabulaçao
%d          imprime valor como inteiro decimal
%s          string
%T          mostra do tipo da variável
%v          imrime valor no formato padrão
%2f         formata float com casas decimais
%x          imprime valores em hexadecimal
%b          imprime valores em binário
%t          imprime variavel boleana

```

#### Quebrar palavras em caracteres

Strings são armazenadas como bytes no Go, usando encode UTF-8. 
Isso significa que um caracter pode ser representado por mais de um byte. 

Por isso, não é possível ler diretamente uma string em um  FOR. 
Ao tentar fazer isso, o resultado será bytes. 
O número de bytes poderá ser maior que o número de caracteres.
A solução é converter de byte para strings. 
Porém, nessa solução poderá haver perdas, pois a conversão fará perder os bytes extendidos de algum caracter, se houver. 
A MELHOR solução é trabalhar com rune. 
Converta o slice de strings em rune e trabalhe com ele 
No final, converta de rune para string (byte). 

Exemplo:

```go
username := "Sir_King_Über"
runes := []rune(username)
for i := 0; i< len(runes); i++{
   fmt.Print(string(runes[i]), " ")
}
```

## Tipos compostos

### Arrays x Slices

* Uma vez definido o tamanho de um Array não é possível mudá-lo
* Quando um array é passado como parâmetro de função, é passada uma cópia do array, logo qualquer mudança no array dentro da função é perdida.
* Passar um array como parâmetro para uma função pode ser lento, justamente porque go faz gera uma cópia do array
* Slices são passados em funções como referencias. Logo se o slice for alterado dentro de uma função as alterações não são perdidas ao término da função.
* Por não precisar tirar cópia de Slice, sua passagem como parametro de função não deixa o programa mais lento.

#### Criando array (sempre tem tamanho fixo)

`myarray := [4]int{0,1,2,3}`

#### Criando um slice

* Slice c/ elementos mas sem tamanho fixo
  
`aSliceliteral := []int{1,2,3,4}`

* Slice s/ elementos mas de tamanho fixo
`aIntegerSlice := make([]int, 20)`

* Slice tem tamanho e capacidade. Se chegar ao tamanho maximo go Dobra a capacidade. Isso é ruim se o Slice for grande.

* Para realizar cópia entre arrays e Slices é necessário converter array para slice com a notação [:]

* Ao copiar um array para um slice o slice será reduzido ou aumentado para o tamanho do array e e seus elementos serão preservados.


#### Trabalhando com Slices

É possível adicionar multiplos itens em um slice usando append.
No exemplo abaixo são adicionados dados de um slice dentro de outro slice usando append. Verifique a notação de 3 pontos.

```go
locales :=  []string{"locale1", "locale2"}
var extraLocals []string
locales = append(locales, extraLocals...)
```

##### Excluir item de slice

```go
	sabores := []string{"peperonni", "mussarela", "abacaxi", "marguerita", "quatroqueijos"}


	// inclui indice zero até 1.  
	// 2 fica de fora
	fatia := sabores[0:2]
	fmt.Println(fatia)

	// inclui indice 3 até o final
	fatia2 := sabores[3:]
	fmt.Println(fatia2)

	// exclui item de um slice
	// 0 a 1 e 3 até o final.
	// item 2 é excluido do slice
	fatia3 := append(sabores[0:2], sabores[3:]...)
   	fmt.Println(fatia3)

}

```

##### Adicionar um slice em outro slice

```go
umaslice := []int{1,2,3,4}
outraslice := []int{9,10,11,12}

// adiciona multiplos itens do mesmo tipo na slice
umaslice = append(umaslice, 5,6,7,8)

// não funciona, pois o segundo parametro 
// deve ser o tipo do conteudo da umaslice (no caso são int)
// o que foi fornecido foi um  tipo "outraslice de int"
umaslice = append(umaslice, outraslice)

// o correto é adicionar o CONTEUDO de outraslice (que tb é int)
// para isso usase o unfurl ou seja, os três pontinhos
umaslice = append(umaslice, outraslice...)

// os três pontinhos significa = conteúdo da slice. 
```


##### Make e slices
`make([]T, len, cap) `
len = tamanho
cap = capacidade 

`slice := make([]int, 5, 10)`  

	Se eu crio um slice com tamanho 5 e capacidade 10, eu posso ir adicionando elementos com append.  
	Ao adicionar elementos com append, após exceder o len inicial, eu irei aumentando o len.  
	Se o len passar a capacidade, Go irá jogar fora o slice e criará um novo len atual mas dobro da capacidade.

##### Slice of slice

```go

bidimensional := [][]int{
		{0, 1, 2, 3},
		{4, 5, 6},
	}

	fmt.Println(bidimensional[1][0])  \\ result 4

```

##### Pegadinha do malandro com Slices

[Exemplo 1 - Pegadinha Slice](https://play.golang.org/p/Xt4OiGrLLKg)


  
## Maps

[Exemplo 1 - trabalhando com maps](https://play.golang.org/p/5qmIXSCN5Ov)

## Loop for

```go
for i := 0; i <= 9; i++ {

}
```

## for infinite loop

```go

// isso é um loop infinito com um break em algum lugar
for {
   break
}
```
`Use continue para quebrar a interação do loop`

## If clause

```go
//não há parenteses no teste de condição. 
if a == b {
   
} else if {

} else {

}
```

## Switch case

```go

// não parentesis na strutura do switch
switch n {
   case 1:
      a = b
   case 2: 
      b = c
   falltrought
   default: 
      c = d
}
```

## structs

### Criando structs
[Exemplo 1 - Criando structs](https://play.golang.org/p/H8BG87NNC0e)

### Struct anonima

Structs anomima com mapa e Slice embutidos: 

[Exemplo 1 - Struct Anonima](https://play.golang.org/p/jlEJYUQnZYG)


## Funções

### Funções variádicas

Uma função variádica pode receber n parametros.
O parâmetro varidádico tem que ser o último.m
A função converte os valores recebidos em um slice.
Para mandar um slice para uma função com parametro variadico int
é preciso usar notação de 3 pontos.
Assim o slice é unpacked para int.
Vide exemplo abaixo:  

[Função variadia - exemplo1](https://play.golang.org/p/xYG5aWNyLbN)
[Função varidica - exemplo2](https://play.golang.org/p/lYQyIUp975j)

### Funções - Clousure

Criamos um cloure ao criar uma funcao anonima dentro de outra função e chamar essa funcao anonima como retorno da outra função.  
Isso permite à função anonima, usar parametros que são externos a ela. Exemplos:

[Exemplo 1 - Clousure](https://play.golang.org/p/nvAUskka9GX)  
[Exemplo 2 - Clousure](https://play.golang.org/p/kFBQe0MjM1X)  

### Função `init`

Função que roda antes das outras. Serve para fazer setup antes da aplicação rodar.
`func init(){}`

### Funções callback
Função callback é quando você usa uma função como parâmetro de outra função. 

[Exemplo 1 - CAllback Function](https://play.golang.org/p/PXI8T0o6lxv)
[Exemplo 2 - CAllback Funcion](https://play.golang.org/p/7nVW7vcN0fs)


### Funções como tipos

Em Go, uma função é um tipo, ou seja podemos criar tipos que são funções para poder reusá-los dentro dos programas. 

### Interfaces

A melhor forma de se estudar interfaces é através dos exemplos comentados. 

[Exemplo 1 - Interfaces](https://play.golang.org/p/4sY2v050sMK)



## Ponteiros

Exemplo com explicação:

[Exemplo 1 - Ponteiros](https://play.golang.org/p/tnYbNGp6YuF)
[Exemplo 2 - Ponteiros](https://play.golang.org/p/dBgIOCpU7DH)
[Exemplo 3 - Ponteiros](https://play.golang.org/p/nBFDufLNkPA)
[Exemplo 4 - Ponteiros - Modificando um struct](https://play.golang.org/p/V8Cfk7mP1Wd)



## Defer (adiar)

Defer adia a execução de uma instrução no programa. 
Se tiver mais de um, a primeira instrução com DEFER   entrar na fila é o última a ser executada. O ponto de execução é a função na qual o DEFER foi criado, ou seja, ele executa a instrução antes da função encerrar (que pode ser antes do retorno). 

[Exemplo - DEFER](https://play.golang.org/p/2wXTPjwYt4V)

## Marshal Unmarshal Json

[Exemplo 1 - Marshal and Unmarshal JSon](https://play.golang.org/p/R5N7Sfp-XJl)
[Exemplo 2 - Marshal JSon](https://play.golang.org/p/cakcrC_ygYQ)]
[Exemplo 3 - Unmarshal Json](https://play.golang.org/p/IIzg0SMDq9H)






## Erros

Existem 3 tipos de erros em programação

* Erros de sintaxe
* Erros de compilação ou interpretação
* Erros de semântica

Go não trabalha com tratatamento de exceções `exception handling`.
O tratamento de exceções é uma forma implícita de tratar erros em outras linguagens de programação.

Em go os erros são tratados seguindo paradigma diferente: forma explícita.

O que é um erro em Go? Em go um erro é um valor.

```go
val, err:= someFunc() err
if err !=nil{
   return err
}
return nil
```

A diferença entre um error e panic em go reside no fato de que o erro não causará problemas que impactam na integridade do programa. 
Uma função não irá dar crash se você não tratar o erro.
Ja no panic se o erro não for tratado o programa dará crash. 

## Logs

Ao fazer uma impressão usando pacote log, serão mostrados dados adicionais como
data e hora da execução do comando.

### Log Setflags

Ao setar flags para log, sua operação é modificada, podendo dar mais detalhes

`log.SetFlags(log.Ldate | log.Lmicroseconds | log.Llongfile)`

Pode ser interessante colocar as flags numa função init.

`Log.Fatalln` corresponde a um `fmt.Println`, mas é seguido de um os.Exit(1) onde o programa termina com erro e imprime o log.

A diferença entre `panic` e `fatal` é que a primeira pode ser recuperável, através do uso de `defer`

## Tests

Rodar comando go test recursivo para pastas:
`go test ./...`

Verbose tests - para mostrar todos os testes de todas funções
`go test -v ./...`

Para rodar testes em paralelo colocar debaixo da assinatura das funções de teste:
`t.parallel()`

### Coverage

Verifica cobertura do testes para todos os casos da funçao mas não especifica quais funcoes não estao totalmente cobertas
`go test --cover`

Gerar relatorio de cobertura
`go test --coverprofile cobertura.txt`

Verificar cobertura de testes de todas as funções no relatorio de cobertura.
Depende do relatório de cobertura gerado com go test.
`go tool cover --func=cobertura.txt`

Verificar linhas das funções que não estão cobertas no relatorio de cobertura.
Depende do relatório de cobertura gerado com go test.
`go tool cover --html=cobertura.txt`


## Pacotes interessantes

### `math/big`

Usado para criar números maiores que float64.
Exemplo de uso:

```go
//criando big number
bigA := big.NewInt(math.MaxInt64)

// adicionando ao big number
bigA.Add(bigA, big.NewInt(1))
```

### `math/rand`

Usado para gerar numeros aleatórios
Exemplo:

```go

// gera numero aleatorio entre 1  e 10 
int a := rand.Intn(10)+1

// semeando um numero aleatorio
rand.Seed(time.Now().UnixNano())

```

### `unicode`

Util para checar caracteres de uma string
Exemplo de uso: 

```go

// funcao que checa se texto tem minusculas
func checaTexto(meuTexto string) bool{
   meuTextoR := []rune(meuTexto)
   hasLower = false
   for _, v := meuTextoR{
      if unicode.IsLower(v) {
      hasLower = true
      }
   }
   return hasLower
}
```



### `time`

Manipulação de tempo.
exemplos:

```go
time.Now()
time.Monday



//criando variavel do tipo time
startUpTime time.Time = time.Now()

//criadno variavel do tipo time shorthand
startUpTime := time.Now()
```

### `Error`

```go
errors.New("input can't be a negative number")
```