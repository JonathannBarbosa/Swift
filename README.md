# Swift — Conceitos Básicos

Repositório de estudos sobre os fundamentos da linguagem Swift, com foco em sintaxe, tipos, controle de fluxo e orientação a objetos. Escrito por um dev vindo do ecossistema JavaScript/React Native.

---

## Sumário

- [Variáveis e Constantes](#variáveis-e-constantes)
- [Tipos de Dados](#tipos-de-dados)
- [Opcionais (Optionals)](#opcionais-optionals)
- [Controle de Fluxo](#controle-de-fluxo)
- [Funções](#funções)
- [Closures](#closures)
- [Structs e Classes](#structs-e-classes)
- [Protocolos](#protocolos)
- [Enums](#enums)
- [Coleções](#coleções)

---

## Variáveis e Constantes

```swift
var nome = "Jonathan"   // mutável
let pi = 3.14159        // imutável (equivalente ao const no JS)

var idade: Int = 25     // tipagem explícita
```

> **Dica:** prefira `let` sempre que possível. O compilador avisa quando um `var` poderia ser `let`.

---

## Tipos de Dados

| Tipo | Descrição | Equivalente JS |
|---|---|---|
| `Int` | Inteiro | `number` (inteiro) |
| `Double` | Ponto flutuante | `number` (decimal) |
| `String` | Texto | `string` |
| `Bool` | Booleano | `boolean` |
| `Character` | Um único caractere | — |

```swift
let texto: String = "Olá, Swift!"
let numero: Int = 42
let preco: Double = 9.99
let ativo: Bool = true
```

---

## Opcionais (Optionals)

Um dos conceitos mais importantes do Swift. Um optional representa um valor que **pode ou não existir**.

```swift
var nome: String? = "Jonathan"  // pode ser nil
var vazio: String? = nil

// Unwrap seguro com if let
if let n = nome {
    print("Nome: \(n)")
}

// Nil coalescing (equivalente ao ?? do JS)
let exibir = nome ?? "Anônimo"

// Guard let — sai cedo se for nil
func saudacao(nome: String?) {
    guard let n = nome else { return }
    print("Olá, \(n)!")
}
```

---

## Controle de Fluxo

```swift
// if / else
let temperatura = 30
if temperatura > 25 {
    print("Calor!")
} else {
    print("Frio.")
}

// switch (muito mais poderoso que no JS)
let dia = "Segunda"
switch dia {
case "Sábado", "Domingo":
    print("Fim de semana")
case "Segunda", "Terça", "Quarta", "Quinta", "Sexta":
    print("Dia útil")
default:
    print("Dia inválido")
}

// Ranges funcionam bem com tipos numericos
let nota = 7
switch nota {
case 9...10:
    print("Ótimo")
case 7...8:
    print("Bom")
case 5...6:
    print("Regular")
default:
    print("Insuficiente")
}

// for-in
for i in 1...5 {
    print(i)
}

// while
var contador = 0
while contador < 3 {
    contador += 1
}
```

---

## Funções

```swift
// Função básica
func somar(a: Int, b: Int) -> Int {
    return a + b
}

somar(a: 2, b: 3) // → 5

// Parâmetro com label externo
func apresentar(nome apelido: String) {
    print("Olá, \(apelido)!")
}

apresentar(nome: "Jonathan")

// Sem label externo
func multiplicar(_ a: Int, _ b: Int) -> Int {
    return a * b
}

multiplicar(3, 4) // → 12
```

---

## Closures

Equivalente às arrow functions (`() => {}`) do JavaScript.

```swift
// Closure completa
let dobrar: (Int) -> Int = { (numero: Int) -> Int in
    return numero * 2
}

// Forma resumida (trailing closure)
let triplicar = { $0 * 3 }

// Uso com map (igual ao .map() do JS)
let numeros = [1, 2, 3, 4]
let dobrados = numeros.map { $0 * 2 }  // [2, 4, 6, 8]
```

---

## Structs e Classes

```swift
// Struct — tipo de valor (copiado ao ser passado)
struct Ponto {
    var x: Double
    var y: Double
}

var p1 = Ponto(x: 1.0, y: 2.0)
var p2 = p1   // cópia independente
p2.x = 99     // p1.x continua 1.0

// Class — tipo de referência (como objetos no JS)
class Pessoa {
    var nome: String
    var idade: Int

    init(nome: String, idade: Int) {
        self.nome = nome
        self.idade = idade
    }

    func apresentar() {
        print("Sou \(nome), \(idade) anos.")
    }
}

let dev = Pessoa(nome: "Jonathan", idade: 25)
dev.apresentar()
```

> **Regra geral:** use `struct` por padrão. Use `class` quando precisar de herança ou referência compartilhada.

---

## Protocolos

Equivalente às `interfaces` do TypeScript.

```swift
protocol Autenticavel {
    var email: String { get }
    func login() -> Bool
}

struct Usuario: Autenticavel {
    var email: String

    func login() -> Bool {
        return !email.isEmpty
    }
}
```

---

## Enums

```swift
enum Status {
    case ativo
    case inativo
    case pendente(motivo: String)
}

let estado = Status.pendente(motivo: "Aguardando aprovação")

switch estado {
case .ativo:
    print("Online")
case .inativo:
    print("Offline")
case .pendente(let motivo):
    print("Pendente: \(motivo)")
}
```

---

## Coleções

```swift
// Array
var frutas: [String] = ["Maçã", "Banana", "Uva"]
frutas.append("Manga")
frutas.first        // Optional("Maçã")

// Dictionary (equivalente ao objeto/Map do JS)
var notas: [String: Int] = ["Matemática": 9, "Português": 8]
notas["História"] = 7
notas["Matemática"]   // Optional(9)

// Set (valores únicos, sem ordem)
var ids: Set<Int> = [1, 2, 3, 2, 1]
// ids = {1, 2, 3}
```

---

## Referências

- [Swift.org — The Swift Programming Language](https://docs.swift.org/swift-book/)
- [Hacking with Swift](https://www.hackingwithswift.com/)
- [Swift by Sundell](https://www.swiftbysundell.com/)



- [SwiftFiddle](https://swiftfiddle.com/)
- [Online Swift Playground](https://online.swiftplayground.run/)
