# Getting Started

```rust
fn main() {
    println!("Hello, world!");
}
```

* Descrevemos funções com fn.
* A função main é sempre a primeira a ser chamada em um programa rust.
* Em println! o uso do ! representa que estamos chamando um macro Rust e não uma função.
* Uso de ponto e vírgula é necessário.

# Guessing Game

```rust
use std::io;

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {}", guess);
}
```

* Para pegarmos a entrada e saída do usuário usamos a biblioteca io que vem da biblioteca padrão std.
* Usamos let para criar uma variável, que por padrão é imutável.
* Usamos mut para definir que uma variável é mutável.
* :: em String::new() indica que new() é uma função de String.
* io::stdin() lida com a entrada padrão do usuário.
* read_line(&mut guess) lê uma linha da entrada padrão e atibui à variável mutável do tipo string passada como parâmetro.
* Usamos & para passar uma variável por referência e economizar memória.
* Por padrão uma referência é imutável, então usamos o mut para torná-la mutável.
* Funções como read_line retornam também um valor do tipo io::Result, esse valor possui duas variantes, Ok e Err.
* Um Result do tipo Ok possui o resultado da função.
* Um Result do tipo Err contém informações de como e porque o erro foi gerado.
* A função .expect() em um Result do tipo Err irá encerrar o programa e imprimir o conteúdo de Err.
* Caso o Result seja do tipo Ok, a função .expect() irá retornar apenas o valor de Ok para uso.
* usamos {} como placeholders para imprimir variáveis no println!();

# Variables

```rust
fn main() {
    let x = 5;

    let x = x + 1;

    let __x = x * 2;

    let x = "The value of x";

    println!("{}", x);
}
```

* Se criarmos outra variável com o mesmo nome de uma já declarada, ocorre um shadow da variável anterior.
* Uma variável mutável não pode mudar seu tipo, apenas seu valor.
* uma variável que recebe shadow pode mudar tipo e valor.

| type      	| notation     	| alt 	|
|-----------	|--------------	|-----	|
| integer   	| i32          	| u32 	|
| Float     	| f32          	| f64 	|
| Boolean   	| bool         	|     	|
| Character 	| char         	|     	|
| Tuple     	| (type, type) 	|     	|
| Array     	| [type; size] 	|     	|

# Functions
### A estrutura de uma função é:

```rust
fn name_of_the_function(parameter1: type1, parameterx: typex) -> return_type {
    expression
}
```

Uma Espression é um statement que retorna um valor. Ex:

```rust
fn main() {
    let x = 5;

    let y = {
        let x = 3;
        x + 1
    };

    println!("The value of y is: {}", y);
}
```
**Importante denotar que o valor de retorno não possui ; no fim.**

# Control Flow

## IF
### A estrutura de um if é:

```rust
if condition {
    expression
} else if condition {
    expression
} else {
    expression
}
```

Também podemos usar um if em uma expressão let, como um operador ternário:

```rust
let number = if condition { value } else { value }
```

De forma que value tem de ser do mesmo tipo.

## LOOP
### A estrutura de um loop é:

```rust
loop {
    expression
}

let result = loop {
    counter += 1;

    if counter == 10 {
        break counter * 2; //retorna o resultado para a variável
    }
};
```

Ele executa um pedaço de código até receber um código de parada (break, ctrl + c)

## WHILE
### A estrutura de um while é:

```rust
while condition {
    expression
}
```

## FOR
### A estrutura de um for é:

```rust
for variable in collection {
    expression
}
```

