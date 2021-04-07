# Go Tips

23/04/2020 23:52## Fluxo de trabalho em Go

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

```https://golang.org/pkg/nomeDoPacote
   https://golang.org/cmd/nomeDoComando
```

## Basic Go program

```go
package main
import "fmt"
func main() {
   fmt.Println("vim-go")
}
```

## Basic program Domain separate

```go
package main
import "fmt"

func goHello() string{ // Function is out of main
  return "Hello World"
}

func main(){
   fmt.Println(goHello())
}

```

## local de instalação

Go é instalado em `usr/local/bin`.
Adicionar ao `.profile`:

```go
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

## construir o godoc

```go
cd / $GOPATH/src/golang.org/x/tools/cmd/godoc
go build -o $GOPATH/bin/godoc
```

## Acessar o godoc

```go
godoc -http=localhost:6060
```

## Peculiaridades do GO

* Go não compila se houver pacotes importados e variáveis não utilizados.
* Go não compila se faltar o pacote de alguma função
* Go não usa ; para separa sentenças. O compilador coloca o ; onde for necessário.
* Go não usa parênteses para declarar condições em if ou switch
* Go não usa break para sair de switchs
* Go pode retornar n valores de uma função
* Go pode aceitar n argumentos para uma função
* O método Println não precisa de espaço na separação de argumentos

## Arrays x Slices

* Uma vez definido o tamanho de um Array não é possível mudá-lo
* Quando um array é passado como parâmetro de função, é passada uma cópia do array, logo qualquer mudança no array dentro da função é perdida.
* Passar um array como parâmetro para uma função pode ser lento, justamente porque go faz gera uma cópia do array
* Slices são passados em funções como referencias. Logo se o slice for alterado dentro de uma função as alterações não são perdidas ao término da função.
* Por não precisar tirar cópia de Slice, sua passagem como parametro de função não deixa o programa mais lento.

### Criando array (sempre tem tamanho fixo)

`myarray := [4]int{0,1,2,3}`

### Criando um slice

* Slice c/ elementos mas sem tamanho fixo
  
`aSliceliteral := []int{1,2,3,4}`

* Slice s/ elementos mas de tamanho fixo
`aIntegerSlice := make([]int, 20)`

* Slice tem tamanho e capacidade. Se chegar ao tamanho maximo go Dobra a capacidade. Isso é ruim se o Slice for grande.

* Para realizar cópia entre arrays e Slices é necessário converter array para slice com a notação [:]

* Ao copiar um array para um slice o slice será reduzido ou aumentado para o tamanho do array e e seus elementos serão preservados.
  
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

### Formata documentos recursivamente

`go fmt ./...`

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

```go

//criando tipo struct
type teste struct {
nome string
cpf  string}

//declarando variavel struct
var u teste
u.nome = "alan"
u.cpf = "875.607.556-15"

//declarando variável struct
u2 := teste{"Carlos", "12"}

//declarando variavel struct
u3 := teste{nome: "samara"}
   
```

## Int types

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

### `math/rand`

Usado para gerar numeros aleatórios
Exemplo:

```go

// gera numero aleatorio entre 1  e 10 
int a := rand.Intn(10)+1

// semeando um numero aleatorio
rand.Seed(time.Now().UnixNano())

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

### `strings`

```go
// remove espaços antes de depois de uma cadeia de  caracteres
strings.Trim(v)
// converte strings para minusculas
strings.ToLower(v)

```

## Declarando strings

```go
// Mais facil declarar como Raw
comment1 := `In "Windows" the user directory is "C:\Users\"`

// Declarando interpretado precisa de escape "\" p/ carecteres especiais
comment2 := "In \"Windows\" the user directory is \"C:\\Users\\\""
```

## Verbos para formatação de strings

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

## Quebrar palavras em caracteres

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

## Trabalhando com Slices

É possível adicionar multiplos parametros em um slice usando append.
No exemplo abaixo são adicionados dados de um slice dentro de outro slice usando append. Verifique a notação de 3 pontos.

```go
locales :=  []string{"locale1", "locale2"}
var extraLocals []string
locales = append(locales, extraLocals...)
```

## Funções variádicas

uma função variádica pode receber n parametros.
O parâmetro varidádico tem que ser u último.
A função converte os valores recebidos em um slice.
Para mandar um slice para uma função com parametro variadico int
é preciso usar notação de 3 pontos.
Assim o slice é unpacked para int.
Vide exemplo abaixo:  

```go
func main() {
   i := []int{5, 10, 15}
   fmt.Println(sum(5, 4))
   fmt.Println(sum(i...))
}

func sum(number ...int) (result int) {

   for i := range number {
      result += number[i]
   }
   return result
}
```

## - Funções - Clousure

Criamos um cloure ao criar uma funcao anonima dentro de outra função e chamar essa funcao anonima como retorno da outra função
Isso permite à função anonima, usar parametros que são externos a ela.
Exemplo abaixo:

```go
func main() {
   counter := 4

   x := decrement(counter)
   fmt.Println(x())
   fmt.Println(x())
   fmt.Println(x())
   fmt.Println(x())

}

func decrement(i int) func() int {

   return func() int {
      i--
      return i

   }

}
```

### Função `init`

Função que roda antes das outras. Serve para fazer setup antes da aplicação rodar.
`func init(){}`


### Funções como tipos

Em Go, uma função é um tipo, ou seja podemos criar tipos que são funções para poder reusá-los dentro dos programas. 

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

## Ponteiros

Exemplo com explicação:

```go

var a := 100

// B é um ponteiro de int
var b *int

// B aponta para endereço de A
b = &a

// imprime endereço de a (ja que ele aponta pra la)
fmt.Println(b)

// imprime o que está dentro do endereço de 
fmt.Println(*b)

// se mudar o valor de a, o valor de *b tb será alterado

```

Outro exemplo de ponteiro:

```go
package main

import "fmt"

func main() {
   temperatura := 100
   fatorEbulicao := 2

   // Ponteiro nao aceita valor, logo deve ser passado endereço 
   // do valor (da variavel que armazena valor)
   pontoEbulicao(&temperatura, fatorEbulicao)
   fmt.Println(temperatura)
}
]//declaracao de parametro do tipo ponteiro
// esse parametro vai receber um endereço de memoria de alguma variavel
func pontoEbulicao(temp *int, fe int) {

   // Neste caso a funçao nao precisa de retorno
   // pois já está alterando valor fora dela
   // no caso, a variavel temperatura
   *temp = *temp * fe
}
```

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

## Time

Retorna tempo de forma mais amigável:****
`time.Now().Format(time.ANSIC)`
