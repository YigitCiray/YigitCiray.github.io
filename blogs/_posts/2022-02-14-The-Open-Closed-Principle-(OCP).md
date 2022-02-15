### Object Oriented Programming - Design Principles
My fourth post is about OCP, I am on the fourth principle of reverse order of S-O-LID principles with this blog post.

You can find my other blog posts [Liskov Substitution Principle](https://ihadahamoment.com/Liskov-Substitution-Principle-(LSP)/), [Interface Segregation Principle](https://ihadahamoment.com/Interface-Segregation-Principle-(ISP)/) and [Dependency Inversion Principle](https://ihadahamoment.com/Dependency-Inversion-Principe-(DIP)/)

**Background**
Bertrand Meyer described the principle as below on [Object-Oriented Software Construction](https://en.wikipedia.org/wiki/Object-Oriented_Software_Construction) in 1988
_A software artifact should be open for extension but closed for modification._

**Why Open Closed Principle is important?**
By using OCP we are commiting that entities such as classes, modules and emthods can be extendiblewithout having to modify. The best way to understand a bad practice of OCP by Uncle Bob's Clear Architecture book is, if an extension requires massive change then the architects of that software engaged in a spectacular failure. New code is always the necessity but how much of a change needed for the existing code. Less code change means more success on architecture of the initial development.

Even the idea introduced as inheritence by Bertrand Meyer, since inheritence comes up with a tight coupling, Robert C. Martin and future resources prefers to use intrface rather than super class.

I will demonstrate an example using Swift in this document.
This time I'll do only the good practice of OCP. Swift language has a keyword 'final' to declare that this class is not can not be inherited from. Still we can have the extension for the class as demonstrated in this [file](https://github.com/YigitCiray/DesignPatternsAndPrinciples/blob/main/Design%20Principles/OpenClosedPrinciple.playground/Contents.swift).
 
```swift
final class Car {
    
    var engine: Engine
    
    init(engine: Engine) {
        self.engine = engine
    }
    
    func start() {
        engine.started = true
    }
    
    func stop() {
        engine.started = false
    }
    
    func maxPower(){
        engine.sportMode()
    }
}

protocol Engine {
    var started: Bool { get set }
    func sportMode()
}

class BMWHybrid: Engine {
    var started: Bool = false
    
    func sportMode() {
        print("BMW sport mode")
    }
}

class Tesla: Engine {
    var started: Bool = false
    
    func sportMode() {
        print("Tesla sport mode")
    }
}


let tesla = Car(engine: Tesla())
let bmw = Car(engine: BMWHybrid())

extension Car {
    func start2() {
        print("start2")
    }
}
```

Example demonstrated above is close for inheritence and by using engine as a protocol we are open for extensions and extendibility.