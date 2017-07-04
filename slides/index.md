- title : Introduction to F#
- description : Introduction to F#
- author : Dave Glassborow
- theme : night
- transition : default

***

## F#?

- ML (1974) / OCaml derivative with strong theoretical background 
- Open source since 2005: [FSharp.org](http://fsharp.org) & [Github](https://github.com/fsharp/)
- Functional First but very pragmatic
- _I can get more complex work done, I have to think less, the compiler does more for me_
- Think _SQL_

---

## Issues with OO

- Packets of hidden state, hard to reason about (limits of our brain)
- The problem with object-oriented languages is they’ve got all this implicit environment that they carry around with them. You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.
- After 20 years of OO, I've become disillusioned (C++,Java,Delphi,C#,Ruby)
- Spagetti code & Little reuse
- Lots of coupling (coupling data and behaviour)

---

## Advantages

- Manage complexity
- Less stressful to code
- More powerful, program at a higher level
- Think differently, apply it to other langauges
- Pit of success
- REPL

--- 

## Disadvantages

- More abstract
- Mathematical naming
- Different way of thinking (map)
- Rabbit hole: Haskell, Dependant types, Category Theory
- More thinking, less typing, which is harder

***

### F# -> C#

- Generics
- Nullable types
- LINQ
- Async/Await
- Tuples
- Pattern matching

***

### Basics

- Everything is an expression
- Types infered
- if / then / else
- match
- fun x -> x
- record / class / DU
- linear
- destructuring
- |> and >>
- Partial application

---

### Examples

    let simpleValue = 5
    let upper (s:String) = s.ToUpper()
    let fact      x     = List.reduce (fun total v -> v * total ) [1..x]
    let factorial x     = List.reduce (*) [1..x]
    let factorialPipe x = [1..x] |> List.reduce (*)
    type Person = {
        Name: string
        Dob: DateTime option
    }

[F# cheatsheet](http://dungpa.github.io/fsharp-cheatsheet/)

--- 

### Linear Dependancies

- Compiles top to bottom, left to right, single pass
- Annoying at First
- Grown to love the constraint
- Foundations first, type driven development
- Leads to less coupled code, less cyclic dependancies

---


#### Specflow

![Specflow](http://fsharpforfunandprofit.com/assets/svg/specFlow.all.dot.svg)

---

#### Tickflow

![Tickflow](http://fsharpforfunandprofit.com/assets/svg/tickSpec.all.dot.svg)

***

### Core Values

- Sane defaults
- _Reason_ about code
- Composiblity: Lego
- Functions: first class, making them, changing them

---

### Sane defaults

- Immutability
- No nulls
- Structural comparisions

---

### Reasoning

_Controlling complexity is the essence of computer programming._

- Types to aid thinking, reduce brain load
- Compiler does more for you
- Declarative
- Purity

---

### Composibilty

- Functional means using functions as first class (adding them together, passing them around)
- Currying
- Parametric
- Monadic

![Lego wall](http://4.bp.blogspot.com/-eHlcNN6L-Ag/UWHaKgfhHsI/AAAAAAAAAXg/tTe6Ar56pMQ/s1600/4.jpg)

***

### Poker

- https://github.com/exeter-fp/poker-puzzle

***

### Active Patterns

- Abstraction over types

#### Complete patterns

    let (|Even|Odd|) i = 
        if i % 2 = 0 then Even else Odd

    let testNumber i =
        match i with
        | Even -> printfn "%d is even" i
        | Odd -> printfn "%d is odd" i

---

#### Parametised

    let (|DivisibleBy|_|) by n = 
        if n % by = 0 then Some DivisibleBy else None

    let fizzBuzz = function 
        | DivisibleBy 3 & DivisibleBy 5 -> "FizzBuzz" 
        | DivisibleBy 3 -> "Fizz" 
        | DivisibleBy 5 -> "Buzz" 
        | i -> string i

***

### Type Providers

- Removing magic strings
- Irritating when the build breaks


CSV,JSON,XML,HTML: [FSharp.data](https://fsharp.github.io/FSharp.Data/index.html)


---

### Lots of them

- Regular Expressions
- AWS S3 / Azure storage
- Databases (ORMS, querys, sprocs)
- WMI
- OData
- Hadoop
- Slack
- [R](http://bluemountaincapital.github.io/FSharpRProvider/)

***

### Other stuff

- Quotations: expression trees
- Computation Expressions: Monads + DSLs
- Units of measure


    [<Measure>] type m
    [<Measure>] type sec
    [<Measure>] type kg

    let distance = 1.0<m>    
    let time = 2.0<sec>    
    let speed = 2.0<m/sec>    
    let acceleration = 2.0<m/sec^2>    
    let force = 5.0<kg m/sec^2>
    let travel = time * speed

*** 

### Quotes

- _Always code as if the guy who ends up maintaining your code will be a violent psychopath who knows where you live._

- _There are two ways of constructing a software design: One way is to make it so simple that there are obviously no deficiencies and the other way is to make it so complicated that there are no obvious deficiencies._

- _Object oriented programming makes code understandable by encapsulating moving parts. Functional programming makes code understandable by minimizing moving parts._

***

## Find out more

### FP

- [Rich Hickey](https://changelog.com/posts/rich-hickeys-greatest-hits)
- [John Carmack](http://www.altdev.co/2012/04/26/functional-programming-in-c/)

### F#

- http://fsharpforfunandprofit.com
- http://connelhooley.uk/blog/2017/04/10/f-sharp-guide
- http://connelhooley.uk/blog/2017/04/30/f-sharp-to-c-sharp
- https://channel9.msdn.com/events/Build/2017/T6064
- [F# koans](https://github.com/ChrisMarinos/FSharpKoans/)
- [Video: F# for C# developers](https://vimeo.com/131640714)