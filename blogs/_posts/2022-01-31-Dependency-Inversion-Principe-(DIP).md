## Dependency Inversion Principle

I would like to start my blog with my first post about Dependency Inversion Principle. Decided to reverse the order to show myself how successfull I am on reverse engineering:P 
**SOLID** to remember all;
- **S**-> Single responsibility 
- **O**-> Open-closed
- **L**-> Liskov substitution
- **I**-> Interface segregation
- **D**-> Dependency inversion

The Solid design principles were promoted by Robert C. Martin, referenced many times as DIP on [Clean Code](https://www.amazon.com/dp/0132350882/ref=cm_sw_em_r_mt_dp_CEBYC0H1FXGR5FE5JVND) book.

TLDR; The DIP says that our classes should depend upon abstraction, not on concrete classes. 

I choose DIP to start my blog because I tend to misuse Dependency Injection over Dependency Inversion Principle while the reality is opposite, DI is based on DIP. 

Historically Inversion of Control(IoC) first written in 1988 by Ralph E. Johnson & Brian Foote on Designing Reusable Classes paper. The concept was popularized by Robert Martin’s paper OO Design Quality Metrics An Analysis of Dependencies, 1994. 

While IoC principle suggesting more abstractin, Dependency Inversion’s idea is making the module independent of concrete types which it controls, and reuse freely. 
Goal is as always, achieve Loose Coupling. I also demonstrate a coding example [under this link](https://github.com/YigitCiray/DesignPatternsAndPrinciples/blob/main/Design%20Principles/Dependency%20Inversion%20Principe.playground/Contents.swift).

In the first example we have coupling, and concrecte class used for a keyboard.
Class laptop has the concrete keyboard brand class. 

On the second example, I demonstrated Dependency Inversion Principle, improved loose coupling and introduced protocol, where it confirmed by keyboard concrete types and invoked by laptop class.

```javascript
protocol KeyboardConnection {
    func connect(laptopName: String, viaBluetooth:Bool)
}
```

In the object-oriented design, classes have to interact with each other to manage functionalities and eventually create application.

Main disadvantage of using concrete types, it controls the creation and lifetime of objects of the dependency class. However, with DIP goal is delegating control to another class. Rather than using the Class B in Class A, use interface of Class B, delegate the method, this way you can achieve more loosely coupled classes and abstraction.





[Designing Reusable Classes By Ralph E. Johnson & Brian Foote, June/July 1988](https://www.cse.msu.edu/~cse870/Input/SS2002/MiniProject/Sources/DRC.pdf)

[OO Design Quality Metrics An Analysis of Dependencies By Robert Martin October 28,1994](https://linux.ime.usp.br/~joaomm/mac499/arquivos/referencias/oodmetrics.pdf)
