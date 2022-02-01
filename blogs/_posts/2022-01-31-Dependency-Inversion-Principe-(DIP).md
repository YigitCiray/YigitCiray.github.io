## Dependency Inversion Principle


I would like to start my blog with my first post about Dependency Inversion Principle. Decided to reverse the order to show myself how successfull I am on reverse engineering:P 
**SOLID** to remember all;
- **S**-> Single responsibility 
- **O**-> Open-closed
- **L**-> Liskov substitution
- **I**-> Interface segregation
- **D**-> Dependency inversion


The Solid design principles were promoted by Robert C. Martin, referenced many times as DIP on Clean Codebook.

TLDR; The DIP says that our classes should depend upon abstraction, not on concrete details. 

I choose DIP to start my blog because I tend to misuse Dependency Injection over Dependency Inversion while DI is based on DIP. 
Historically Inversion of Control was first written in 1988 by Ralph E. Johnson & Brian Foote on Designing Reusable Classes paper. The concept was popularized by Robert Martin’s paper OO Design Quality Metrics An Analysis of Dependencies, 1994. 

Dependency Inversion’s idea is making the module independent of the details that it controls, then giving a chance to reuse freely. It is inverting dependencies with OOD

Achieve Loose coupling

The IoC principle suggests inverting the control, meaning that instead of driving the car yourself, you hire a cab, where another person will drive the car. Thus, this is called inversion of the control - from you to the cab driver. You don't have to drive a car yourself and you can let the driver do the driving so that you can focus on your main work.


In the object-oriented design approach, classes need to interact with each other in order to complete one or more functionalities of an application

Essentially, it controls the creation and lifetime of objects of the dependency class.

This means delegating control to another class. In other words, invert the dependency creation control from class A to another class, as shown below.

Inversion of Control IOC
Remember, IoC is a principle, not a pattern. It just gives high-level design guidelines but does not give implementation details. You are free to implement the IoC principle the way you want.

public class Factory
{
    public static B GetObjectOfB() 
    {
        return new B();
    }
}

As you can see above, class A uses Factory class to get an object of class B. Thus, we have inverted the dependent object creation from class A to Factory. Class A no longer creates an object of class B, instead, it uses the factory class to get the object of class B.

In an object-oriented design, classes should be designed in a loosely coupled way. Loosely coupled means changes in one class should not force other classes to change, so the whole application can become maintainable and extensible.


DIP Definition
1. High-level modules should not depend on low-level modules. Both should depend on the abstraction.
2. Abstractions should not depend on details. Details should depend on abstractions.
To understand DIP, let's take an example from the previous chapter, as shown below.


As per the DIP definition, a high-level module should not depend on low-level modules. Both should depend on abstraction. So, first, decide which is the high-level module (class) and the low-level module.

A high-level module is a module that depends on other modules. 


What is an Abstraction?
In English, abstraction means something which is non-concrete.

abstraction in programming means to create an interface or an abstract class that is non-concrete.

Still, we have not achieved fully loosely coupled classes because the CustomerBusinessLogic class includes a factory class to get the reference of ICustomerDataAccess.



Enter text in [Markdown](http://daringfireball.net/projects/markdown/). Use the toolbar above, or click the **?** button for formatting help.


[Designing Reusable Classes By Ralph E. Johnson & Brian Foote, June/July 1988](https://www.cse.msu.edu/~cse870/Input/SS2002/MiniProject/Sources/DRC.pdf)

[OO Design Quality Metrics An Analysis of Dependencies By Robert Martin October 28,1994](https://linux.ime.usp.br/~joaomm/mac499/arquivos/referencias/oodmetrics.pdf)
