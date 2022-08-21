### #🧨FunctionalProgramming #💻SoftwareDevelopment #📱iOS 
Composition represents has-a relationship. It is an OOP way of reusing code by adding object to another object. Oppose inheriting, it does not have a parent/ child relationship. 

## What is Composition of Functions?
We use multiple functions to get a result, and combining these functions in a static way ex.

is an enemy of reusability. It creates boilerplate code and serves only for one specific need. 
This is why we need to compose functions to create a function that we need to use. Also, others can create rather than ad-hoc solutions all over the codebase.

## How do we compose functions?
What we would like to do is composing;
```swift
f: (A) -> B
g: (B) -> C
```
to create
```swift
c: (A) -> C
```

## How do we use this in Swift?
```swift
infix operator +++: ForwardComposition

func +++ <A, B, C>(f: @escaping (A) -> B, g: @escaping (B) -> C) -> ((A) -> C) {
    return { a in
        g(f(a))
    }
}

incr +++ square   		sign of this method == (Int) -> Int
square +++ String.init  sign of this method == (Int) -> String
```
pointfree.co used [>>>](https://www.pointfree.co/episodes/ep1-functions) for the function composition. 

## What are the use cases?
let's assume that we have two methods for power of two and increment;
```swift
func incr(_ x: Int) -> Int {
    return x + 1
}

func p2(_ x: Int) -> Int {
    return Int(pow(Double(2),Double(x)))
}
```

and there are many use cases such as incrementing first and p2, p2 and increment, or do each and convert to string. These all can be seperate methods which will create boilerplate code and not help your DRY or you can create these beatiful funciton compositions.

```swift
incr +++ p2 					sign of this method == (Int) -> Int
(incr +++ p2) (2) result = 8

p2 +++ incr 					sign of this method == (Int) -> Int
(p2 +++ incr) (2) result = 5

p2 +++ incr +++ String.init 	sign of this method == (Int) -> string
(p2 +++ incr +++ String.init) (2) result = "5"

incr +++ p2 +++ String.init 	sign of this method == (Int) -> string
(incr +++ p2 +++ String.init) (2) result = "8"

```
