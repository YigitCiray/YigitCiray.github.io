---
published: true
---

### #🧭DesignPatterns #💡OOP #💻SoftwareDevelopment
This blog post is about Abstract Factory pattern, I also demonstrated a code sample.

## What is Abstract Factory Pattern?
An interface for creating families of related objects without specifying concrete class.

I would like you to walk you trough my code example to explain in more detail.
Let's say that we would like to provide engine types, and these types vary by motorcycle to car and electric to regular.

Abstract Factory pattern intents to create an abstraction on creation.
To do that I will start with my **interface Engine**
```swift
protocol Engine {
    func start()
}
```
Engine client concrete types in my mind while writing this code are **Car**, **EV**, **Motorcycle** and **EM**(Electric Motorcycle). These concrete classes will **conform the Engine protocol**.
```swift
class Motorcycle: Engine {
    func start() {
        print("Motorcycle start method called")
    }
}

class Car: Engine {
    func start() {
        print("Car start method called")
    }
}

class EM: Engine {
    func start() {
        print("EM start method called")
    }
}

class EV: Engine {
    func start() {
        print("EV start method called")
    }
}
```
We successfully conform the **Engine protocol** on four main concrete types, to sake of the factories I would like to create two concrete EngineFactories and separate by car and motorcycle, I could have also choose Electric vs Regular.
Before creating these concrete classes, I would like to create my **abstraction** for factories and conform them afterwards.
```swift
protocol AbstractFactory {
    func getEngine(_ engineType: String) -> Engine?
}
```
Now we are ready for the concrete factory types
```swift
class CarEngineFactory: AbstractFactory {
    func getEngine(_ engineType: String) -> Engine? {
        if (engineType == "Regular") {
            return Car()
        }else if (engineType == "Electric") {
            return EV()
        }
        return nil
    }
}

class MotorcycleEngineFactory: AbstractFactory {
    func getEngine(_ engineType: String) -> Engine? {
        if (engineType == "Regular") {
            return Motorcycle()
        }else if (engineType == "Electric") {
            return EM()
        }
        return nil
    }
}
```
Looks nice right, we loose coupling between concrete classes and will have a smooth process on factory changes, such as changing CarEngineFactroy to ElectricVehiclesAndMotorsFactoy.
How do we consume?
```swift
class FactoryProducer {
    static func getFactory(isCar: Bool) -> AbstractFactory {
        return isCar ? CarEngineFactory() : MotorcycleEngineFactory()
    }
}


    let carFactory = FactoryProducer.getFactory(isCar: true)
    if let ford = carFactory.getEngine("Regular"){
        ford.start()
    }
    if let tesla = carFactory.getEngine("Electric") {
        tesla.start()
    }
    let motorcycleFactory = FactoryProducer.getFactory(isCar: false)
    if let harley = motorcycleFactory.getEngine("Regular") {
        harley.start()
    }
    if let electricMotor = motorcycleFactory.getEngine("Electric") {
        electricMotor.start()
    }
```
FactoryProducer is the class that we use it's static method getFactory, and by using this method. The returned type is an interface on client and method we call from this factory to get our concrete type is another interface method 
```swift
func getEngine(_ engineType: String) -> Engine?
```

find my [swift code](https://github.com/YigitCiray/DesignPatternsAndPrinciples/blob/main/Design%20Patterns/Creational%20Patterns/AbstractFactory.playground/Contents.swift) and more on my github page.
