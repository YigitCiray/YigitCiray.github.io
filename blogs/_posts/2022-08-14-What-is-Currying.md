## #🧨FunctionalProgramming 
Currying is a functional programming concept which look familiar to me from iOS World but I never thought that this is a concept with a name.

## What is Currying?
Currying is a great way to create compositional functions. It will provide more more reusablity. Can't we call our functions compositional which can take other function(s) as a parameter? Yes, we can, currying is an effort which transforms your ad-hoc function into more reusable one.

Currying is a transformation from 
```swift
f(a, b, c)
```
to
```swift
f(a)(b)(c)
```
It is a helper method to **transform** your method.

## Example
The first method in this example is expecting two parameters. We would like to Curry this method and define constant for the usecase below. 

Curried version of the valuedMember method is manually created and this is not the best approach to curry your method. So what is the better approach? Better approach is having this generic Curry method to create our own curried valuedMember method which expects not two but one parameter.
```swift
func valuedMember(since date: Date, name: String) -> String {
    let format = DateFormatter()
    format.dateFormat = "yyyy"
    let year = format.string(from: date)
    return "\(name) is a valued member since \(year)."
}

// Curried version of the above method
func valuedMember(since date: Date) -> (String) -> String {
    return { name in
        let format = DateFormatter()
        format.dateFormat = "yyyy"
        let year = format.string(from: date)
        return "\(name) is a valued member since \(year)."
    }
}

//Method to Curry the methods
func curry<A, B, C>(_ f: @escaping (A,B) -> C) -> (A) -> (B) -> C {
    return {a in { b in f(a,b) } }
}

```
valuedMember(since:name:) 			**(Foundation.Date, String) -> String**
valuedMember(since:) 				**(Foundation.Date) -> (String) -> String**
curry(valuedMember(since:name:)) 	**(Foundation.Date) -> (String) -> String**

## Usecase
Let's assume that we can use either today's year or sometime which should be provided as a parameter. Let's have a one liner for multiple use.
```swift
let curried = curry(valuedMember(since:name:))(Date())
curried("David")
curried("Joe")
```
"David is a valued member since 2022."
"Joe is a valued member since 2022."

Our first method(valuedMember(since:name:)) is curried with curry(...) and this constant's first parameter is initiated with (Date()).

I'll repeat this, constant's **only** parameter is initiated with (Date()).
Yes, that is the goal, we would like to create a method from an existing method, which needs only one argument rather than two. 

Lastly, this method, which has the first parameter set, is called with other strings, as expected as a second parameter.


## Why it is called currying?
It is not Steph! Yeah! Name is coming from [Haskell Curry](https://en.wikipedia.org/wiki/Currying). He is the programmer who socialized the the concept while Moses Schönfinkel is the founder.

github [link](https://github.com/YigitCiray/DesignPatternsAndPrinciples/blob/main/Functional%20Programming/Currying.playground/Contents.swift)
