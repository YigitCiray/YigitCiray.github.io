### #🧭DesignPatterns #💡OOP #💻SoftwareDevelopment

How do you measure the quality of the code? Can we consider that one way is looking into the collaboration among its objects? How do you decide on collaboration between objects when you plan your code? Focusing on these questions can lead you to come up with a simpler and understandablea architecture.

## Why do we need Design Patterns?
We, software developers, need to communicate with each other about the coding solution that we are actively working on or planning to start. Considered that using a pattern name can save us on thousand word of explanation. Design patterns make our life easier, increase the collaboration while keeping the software development on track. On Gang of Four's [Design Pattern](https://en.wikipedia.org/wiki/Design_Patterns) book there are four essential elements:
1. The pattern name is a handle we can use to describe a design problem
2. The problem describes when to apply the pattern
3. The solution describes the elements that make up the design, their relationshipsm, responisbilities and collaborations.
4. The consequences are the result and trade-offs of applying pattern.

"Inheritance", "Encapsulation" and "Polymorphism" not explained in this book as a design pattern becuase programming languages used for problemsare not procedural languages. I am planning to create a post for these three and link to this blog.

## How do we categorize Design Patterns?
### Creational Patterns
- [Abstract Factory](https://ihadahamoment.com/Abstract-Factory-Pattern/)   _#Object_
- Builder   _#Object_
- Factory Method   _#Class_
- Prototype   _#Object_
- Singleton   _#Object_

### Structural Patterns
- Adapter   _#Class and #Object_
- Bridge   _#Object_
- Composite   _#Object_
- Decorator   _#Object_
- Facade   _#Object_
- Flyweight   _#Object_
- Proxy   _#Object_

### Behavioral Patterns
- Chain of Responsibility _#Object_
- Command   _#Object_
- Interpreter   _#Class_
- Iterator   _#Object_
- Mediator   _#Object_
- Memento   _#Object_
- Observer   _#Object_
- State   _#Object_
- Strategy   _#Object_
- Template Method   _#Class_
- Visitor   _#Object_

## What is object granularity, how do you determine it?
Granularity is the size and the complexity of the object. It can vary from size, depth and number. Design patternsare are used for object granularity purpose too. Depending on the pattern you choose, object's granularity also pre-defined and well structured in design patterns. Example by the Four Gang's book, > _The Facade Pattern describes how to represent complete system as objects, Flyweight pattern describes how to support huge numbers of objects at the finest granularities, Abstract Factory and Builder yields objects whose responsibility is creating other objects while other patterns describe specific way of decomposing an object into similar objects_.
