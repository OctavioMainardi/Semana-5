# Instruções
- Faça uma cópia deste arquivo .md para um repositório próprio
- Resolva as 8 questões objetivas assinalando a alternativa correta e **justificando sua resposta.**
- Resolva as 2 questões dissertativas escrevendo no próprio arquivo .md
- Lembre-se de utilizar as estruturas de código como ``esta aqui com ` `` ou
```javascript
//esta aqui com ```
let a = "olá"
let b = 10
print(a)
```
- Resolva as questões com uso do Visual Studio Code ou ambiente similar.
- Teste seus códigos antes de trazer a resposta para cá.
- Cuidado com o uso de ChatGPT (e similares), pois entregar algo só para ganhar nota não fará você aprender. Não seja dependente da máquina!
- Ao final, publique seu arquivo lista_01.md com as respostas em seu repositório, e envie o link pela Adalove. 

# Resolução da Lista de Exercícios

## Questões Objetivas

### 1) Considerando a execução do código abaixo, indique a alternativa correta e justifique sua resposta.

```javascript
console.log(x);
var x = 5;
console.log(y);
let y = 10;
```

**Resposta:** a) A saída será `undefined` seguido de erro.

**Justificativa:** 
- A variável `x` é declarada com `var`, que sofre hoisting. Isso significa que a declaração de `x` é movida para o topo do escopo, mas sua inicialização não. Portanto, `console.log(x)` imprime `undefined`.
- A variável `y` é declarada com `let`, que também sofre hoisting, mas não é inicializada até a linha onde é declarada. Portanto, `console.log(y)` gera um erro de referência, pois `y` não foi inicializada ainda.

---

### 2) O seguinte código JavaScript tem um erro que impede sua execução correta. Analise e indique a opção que melhor corrige o problema. Justifique sua resposta.

```javascript
function soma(a, b) {
    if (a || b === 0) {
        return "Erro: número inválido";
    }
    return a + b;
}
console.log(soma(2, 0));
```

**Resposta:** a) Substituir `if (a || b === 0)` por `if (a === 0 || b === 0)`.

**Justificativa:** 
- A condição `if (a || b === 0)` está incorreta porque `a` será avaliado como `true` se `a` for um valor truthy (não zero), e `b === 0` será avaliado separadamente. Isso não faz o que se espera, que é verificar se `a` ou `b` é zero.
- A correção `if (a === 0 || b === 0)` verifica corretamente se `a` ou `b` é zero.

---

### 3) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.

```javascript
function calcularPreco(tipo) {
    let preco;

    switch(tipo) {
        case "eletrônico":
            preco = 1000;
        case "vestuário":
            preco = 200;
            break;
        case "alimento":
            preco = 50;
            break;
        default:
            preco = 0;
    }

    return preco;
}

console.log(calcularPreco("eletrônico"));
```

**Resposta:** b) O código imprime 200.

**Justificativa:** 
- No `switch`, quando `tipo` é `"eletrônico"`, `preco` é definido como `1000`, mas como não há um `break` após essa atribuição, o código continua executando o próximo caso (`case "vestuário"`), onde `preco` é redefinido como `200`. Portanto, o valor retornado é `200`.

---

### 4) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.

```javascript
let numeros = [1, 2, 3, 4, 5];

let resultado = numeros.map(x => x * 2).filter(x => x > 5).reduce((a, b) => a + b, 0);

console.log(resultado);
```

**Resposta:** d) 24

**Justificativa:** 
- `map(x => x * 2)` transforma o array `[1, 2, 3, 4, 5]` em `[2, 4, 6, 8, 10]`.
- `filter(x => x > 5)` filtra o array para `[6, 8, 10]`.
- `reduce((a, b) => a + b, 0)` soma os elementos do array filtrado, resultando em `6 + 8 + 10 = 24`.

---

### 5) Qual será o conteúdo do array `lista` após a execução do código? Indique a alternativa correta e justifique sua resposta.

```javascript
let lista = ["banana", "maçã", "uva", "laranja"];
lista.splice(1, 2, "abacaxi", "manga");
console.log(lista);
```

**Resposta:** c) `["banana", "abacaxi", "manga", "laranja"]`

**Justificativa:** 
- O método `splice(1, 2, "abacaxi", "manga")` remove 2 elementos a partir do índice 1 (`"maçã"` e `"uva"`) e insere `"abacaxi"` e `"manga"` no lugar. Portanto, o array resultante é `["banana", "abacaxi", "manga", "laranja"]`.

---

### 6) Abaixo há duas afirmações sobre herança em JavaScript. Indique a alternativa correta e justifique sua resposta.

I. A herança é utilizada para compartilhar métodos e propriedades entre classes em JavaScript, permitindo que uma classe herde os métodos de outra sem a necessidade de repetir código.
II. Em JavaScript, a herança é implementada através da palavra-chave `extends`.

**Resposta:** a) As duas afirmações são verdadeiras, e a segunda justifica a primeira.

**Justificativa:** 
- A afirmação I é verdadeira, pois a herança permite que uma classe herde métodos e propriedades de outra classe, evitando a repetição de código.
- A afirmação II também é verdadeira, pois em JavaScript, a herança é implementada usando a palavra-chave `extends`, que permite que uma classe herde de outra.

---

### 7) Dado o seguinte código. Indique a alternativa correta e justifique sua resposta.

```javascript
class Pessoa {
  constructor(nome, idade) {
    this.nome = nome;
    this.idade = idade;
  }

  apresentar() {
    console.log(`Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`);
  }
}

class Funcionario extends Pessoa {
  constructor(nome, idade, salario) {
    super(nome, idade);
    this.salario = salario;
  }

  apresentar() {
    super.apresentar();
    console.log(`Meu salário é R$ ${this.salario}.`);
  }
}
```

I) A classe `Funcionario` herda de `Pessoa` e pode acessar os atributos `nome` e `idade` diretamente.
II) O método `apresentar()` da classe `Funcionario` sobrepõe o método `apresentar()` da classe `Pessoa`, mas chama o método da classe pai usando `super`.
III) O código não funciona corretamente, pois `Funcionario` não pode herdar de `Pessoa` como uma classe, já que o JavaScript não suporta herança de classes.

**Resposta:** a) I e II são verdadeiras.

**Justificativa:** 
- A afirmação I é verdadeira, pois `Funcionario` herda de `Pessoa` e pode acessar os atributos `nome` e `idade`.
- A afirmação II é verdadeira, pois o método `apresentar()` em `Funcionario` sobrepõe o método da classe `Pessoa`, mas ainda chama o método da classe pai usando `super`.
- A afirmação III é falsa, pois o JavaScript suporta herança de classes usando `extends`.

---

### 8) Analise as afirmações a seguir. Indique a alternativa correta e justifique sua resposta.

**Asserção:** O conceito de polimorfismo em Programação Orientada a Objetos permite que objetos de diferentes tipos respondam à mesma mensagem de maneiras diferentes.
**Razão:** Em JavaScript, o polimorfismo pode ser implementado utilizando o método de sobrecarga de métodos em uma classe.

**Resposta:** b) A asserção é verdadeira e a razão é falsa.

**Justificativa:** 
- A asserção é verdadeira, pois o polimorfismo permite que objetos de diferentes classes respondam ao mesmo método de maneiras diferentes.
- A razão é falsa, pois JavaScript não suporta sobrecarga de métodos (múltiplos métodos com o mesmo nome, mas diferentes parâmetros). O polimorfismo em JavaScript é geralmente implementado através de herança e sobrescrita de métodos.

---

## Questões Dissertativas

### 1) O seguinte código deve retornar a soma do dobro dos números de um array, mas contém erros. Identifique os problema e corrija o código para que funcione corretamente. Adicione comentários ao código explicado sua solução para cada problema.

```javascript
function somaArray(numeros) {
    let soma = 0; // Inicializa a variável soma com 0 para acumular a soma

    for (let i = 0; i < numeros.length; i++) { // Corrige o uso de 'size' para 'length'
        soma += 2 * numeros[i]; // Acumula a soma do dobro de cada número
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4])); // Saída esperada: 20
```

**Explicação:**
- **Problema 1:** A variável `soma` não foi inicializada, o que poderia levar a resultados inesperados. Inicializei `soma` com `0`.
- **Problema 2:** O uso de `numeros.size` está incorreto. O correto é `numeros.length`, que retorna o número de elementos no array.
- **Problema 3:** A soma do dobro dos números não estava sendo acumulada corretamente. Usei `soma += 2 * numeros[i]` para acumular a soma.

---

### 2) Crie um exemplo prático no qual você tenha duas classes:

```javascript
class Produto {
    constructor(nome, preco) {
        this.nome = nome;
        this.preco = preco;
    }

    calcularDesconto() {
        return this.preco * 0.9; // Aplica 10% de desconto
    }
}

class Livro extends Produto {
    constructor(nome, preco, autor) {
        super(nome, preco); // Chama o construtor da classe pai
        this.autor = autor;
    }

    calcularDesconto() {
        return this.preco * 0.8; // Aplica 20% de desconto para livros
    }
}

// Exemplo de uso
const produto = new Produto("Notebook", 1000);
console.log(produto.calcularDesconto()); // Saída: 900

const livro = new Livro("JavaScript: The Good Parts", 50, "Douglas Crockford");
console.log(livro.calcularDesconto()); // Saída: 40
```

**Explicação:**
- **Herança:** A classe `Livro` herda de `Produto`, o que significa que `Livro` tem acesso aos atributos `nome` e `preco`, bem como ao método `calcularDesconto()` da classe `Produto`.
- **Sobrescrita de Método:** A classe `Livro` sobrescreve o método `calcularDesconto()` para aplicar um desconto de 20% em vez de 10%. Isso é feito redefinindo o método na classe `Livro`.

---

### Link do Repositório
[Link do repositório](https://github.com/seu-usuario/seu-repositorio)
```