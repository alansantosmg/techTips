js-tips


## Es2015

### Reload Console
```js
history.go();             // reload page from dev-tools window.location.
reload(true);             // reload page from dev-tools
location.reload();        // reload page from dev-tools
```

### Notação de parenteses
Encontrar ultimo caracter de string

```js
var firsName = 'alan';
var ultimaLetra = firsName[firsName.length -1];
```

### Concactenando variaveis como literais em strings
```js
let temp = 20.5;
let temperatura = 'A temperatura atual é ' + $[temp] + '\u00BC';
console.log(temperatura);
```

### Imprimindo em multiplas linhas com backtick
```js
mVar = `alan é o maior`; console.log(mVar);
```

### Atribuição composta
```js
var myVar = 1;
myVar = myVar + 5;
MyVar += 5;
MyVar /= 5;
Myvar -= 5;
```

### Incremento
```js
var Myvar = Myvar + 1;
Myvar ++;
```

### Arrays unidimensional
```js
var myArray = [1,2,'jose',null];
var myArrayData = myArray[0]; // result = 1
```

### Arrays multidimensionais
```js
var MyArray2 = [[1,2], ['a','b'], 3, 'jose', null];
var myArrayData = myArray[1][0];             // result = a
```

### Add item to the end of array
```js
var Myarray = [1,2];
Myarray.push ([4,5]);                       // result [1,2,[4,5])
```

### Add item to the beginning of array
```js
var Myarray = [1,2];
Myarray.unshift(3);                         // result (3,1,2)
```

### Removes last array element and return element
```js
var MyArray = [1,2,3];
var fora = MyArray.pop();
console.log(fora);                          // [3]
console.log(MyArray);                       // [1,2]
```

### Remove first item in array
```js
var MyArray = [1,2,3]
removeFirst = myArray.shift(); // [2,3]
```

### Function
```js
function myFunction(){
  console.log('Hello World'); };
myFunction();                             // Chamada da função
```

### Function with args function
```js
function myFunction2(a,b){
  console.log(a+b);
}
myFunction();                             // Chamada da função
```

### Function with args and return
```js
function multiplicaDobro(a){
  return a * 2; }
var resultado = multiplicaDobro(3);
console.log(resultado)                    // 6
```

### Example function queue with array
```js
arr = [1,2,3,4];
function filaAnda(arr,item){
  arr.push(item);
  return item = arr.shift(); }
console.log(arr);
```

### if decision true or false simple test function
```js
function testeVerdade(minhaResposta){
  if (minhaResposta) {
    return "Resposta verdadeira"; }
  return 'resposta falsa';
}
```

If decision conditional strict operator convert different types before the comparison
* Example: `1 == '1'` returns true

Strict equality operator does not perform typer conversion
* Example: `1 === '1'` returns false

> IF POSSIBLE ALWAYS USE STRICT EQUALITY OPERATOR


```js
function testVal(val){
  if (val === 10){
    return 'val is true';
  } return 'val is false';
}
myTest = val(11); // myTest = false
```

###  Logical Operators
```
== equal
=== strict equal
!= not equal
!== strict not equal
> < >= <=
&& // and || or
```

### Decision with logic
```js
function test(num){
  if (num <=50 && num >=25){
    return true;
  }
}
test(30); // returns true
```

### While
```js
let count =0;
while(count < 10)
  console.log(count);
  count++; // counts until 9 (10x)
```

### Do While executes loop at least one time
```js
let count=0;
do {
  console.log(count);
  count++;
}while(count < 10);
```

### for loop
```js
for(let i=0; i < 10; i++){
  console.log(i);
}
```

```js
for (let i = 0, j = 5; i < 5; i++, j--) {
} // i increases and j decreases
```

### Nested for loop
```js
for(let i=0; i < 2; i++){
  for(let k=0; k < 2; k++){
    console.log(i + ' ' + k);
  } console.log('\n');
}                               // for each i ran 1 time, k runs 3 times
```

### For in loop
Retorna as propriedades de um objeto obj.a obj.b ...
**Don't use for arrays**
```js
const obj= {a:1, b:2, c:3, d:4, };

for (let o in obj) {
  console.log(obj[o]);         // returns properties of keys in obj
  console.log(o);              // returns the keys }
```

### For out loop
Especifico para coleções retorna os itens da coleção
**Use for arrays and strings**
```js
let iterable = [10, 20, 30];
  for (let value of iterable) {
    console.log(value);
}                               // returns 10, 20, 30 }
```

### Switch case
```js
function myChoice(num){
  let num = 0; switch(num){
    case 1:
      return 1;
    case 2:
      return 2;
    default: // any other option
      return 3; }
}
let returnChoice = myChoice;
```

### sequential switch case
```js
function sequentialSizes(val) {
  var answer = "";
  switch(val){
    case 1:
    case 2:
    case 3: asnwer = 'Low';
      break;
    case 4:
    case 5:
    case 6: answer = 'Mid';
      break
    case 7:
    case 8:
    case 9: answer = 'High';
      break;
  }
sequentialSizes(1);
```


### Return Early Pattern - for functions
```js
function myTest(a,b){ return a === b;   // returns true or fase
                                        // use instead ifs
}
```


## Objects

### An object
```js
alpha = { 'stellarObject': 'star',
          'location': 'Andromeda',
          'parseDistance': 2,
          4: 'w',
          'given Name': 'Polar Star' }
alpha["given Name"] = "South Star";     //change a property
alpha.location = 'M-78';                // change a property
alpha.planets = 2;                      // add property
//delete alpha.4;                         // delete a property
delete alpha.parseDistance;             // delete a property
```

### Using variable to access object properties
```js
family = { father: 'Alan', daughter: 'Alice', son: 'Henrique' }
var memberType = 'father';
var member = family[memberType];
console.log(member)                     // returns Alan
```

### Using Object for lookup instead Switch case or IF
```js
function phoneticLookup(val) {
  var result = "";
  var lookup = { alpha: "Adams",
                bravo: "Boston",
                charlie: "Chicago",
                delta: "Denver",
                echo: "Easy",
                foxtrot: "Frank" }
  result = lookup[val];
  return result;                      // returns Chicago
}
phoneticLookup('Charlie');
```

### Testing if object for property
```js
var myObj = { gift: "pony", pet: "kitten", bed: "sleigh" };

function checkObj(checkProp) {
  if (myObj.hasOwnProperty(checkProp)) {
    return myObj[checkProp];
  } else {
    return "Not Found";
  }
}
checkObj("ponny"); // returns the object if true
```

### Adding objects to an array
#### Using array.push method
```js
var myMusic = [ { "artist": "Billy Joel",
                  "title":  "Piano Man",
                  "release_year": 1973,
                  "formats": [ "CD", "8T", "LP" ],
                  "gold": true } ];

myMusic.push( { "artist": "Madonna",
                "title": "Secret",
                "release_year": 1988,
                "formats": [ "CD", "LP" ],
                "gold": true })
```

### Access nested objects
```js
var myStorage = { "car":
                  { "inside":
                    { "glove box": "maps",
                      "passenger seat": "crumbs" },
                    "outside": { "trunk": "jack" }
                  }
                }
var gloveBoxContents = myStorage.car.inside["glove box"];
```


## ES6

### Make a object imutable with Object.freeze
```js
const MATH_CONSTANTS = { PI: 3.14 };
Object.freeze(MATH_CONSTANTS);
MATH_CONSTANTS.PI = 3,2 // Mutation Not allowed.
```

### Default function parameters
```js
const myName = (firstName = "alan") => console.log(firstName); myName(); // returns alan
myName('john'); // returns john
```

* Variavel local pode ter mesmo nome de variavel global.
* Variavel local tem precedencia sobre global.
* Se nome for igual variavel  com let não pode ser declarada novamente.
* Variavel declarada com const é imutavel, exceto para objetos e arrays.
* No caso de objetos e arrays, o const impede reatribuição do identificador da variavel.
* Use const  para tudo.
* Onde reatribuição, altere para let.
* identificador de variavel const é sempre  maiuscula.
