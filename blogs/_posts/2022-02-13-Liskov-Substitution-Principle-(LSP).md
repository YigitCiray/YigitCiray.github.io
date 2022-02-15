#Object Oriented Programming - Design Principles
My third post is about LSP, I am on the third principle of SO-L-ID with this blog post.

Please find my other blog post about [Dependency Inversion Principle](https://ihadahamoment.com/Dependency-Inversion-Principe-(DIP)/) and [Interface Segregation Principle](https://ihadahamoment.com/Interface-Segregation-Principle-(ISP)/)

**Background**
Barbara Liskov defined the subtypes as below in [1988, Data Abstraction and Hierarchy](https://www.cs.tufts.edu/~nr/cs257/archive/barbara-liskov/data-abstraction-and-hierarchy.pdf)
_What is unwanted here is something like the following substitution property:
If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T._

I found the above statement complicated, hard to understand, to have better understanding I read the 3.3 Type Hierarchy from the paper. 

**Why do we need Liskov Substitution Principle?**
By using LSP you can use a single interface, take advantage of substitutability and represent two or more subtypes. I'll try to come up with a coding example using Swift while trying to stay away from the common, by the book I read and blogs, example of square & rectangle.

I decided to demonstrate a car example by using Swift. On the first part of the code I am coupling concrete types and exampling LSP Violation by two class without sharing any interface while there are common functionalities and bussiness logic for the program.

Tesla and BMWHybrid both have     
```swift
    func checkTirePressure() -> Int 
    func start() -> Bool 
    func stop() -> Bool 
    func checkBatteryLevel() -> Int vs (Int, Int) // sign is different
    
    class CarOwner {
	    let car: BMWHybrid
```

To follow LSP, I'll come up with a Interface, by doing that I'll share the common functionalities of two car classes and decouple the CarOwner class from BMWHybrid.

```swift
protocol Car {
    func checkTirePressure() -> Int
    func start() -> Bool
    func stop() -> Bool
    func preStartBatteryLevelCheck() -> Bool
}
```

By creating the above Car protocol, we have decoupled the CarOwner class from BMW, now we our carowner is ready to change her car form hybrdo to fully electric vehicle. I'll demonstrate exact same example with using superclass rather than interface to have less similarity with my other blog/code example of [Dependency Inversion Princple](https://ihadahamoment.com/Dependency-Inversion-Principe-(DIP)/).

```swift
class Car {
    private var battery: Int = 100
    private var tirePressure: Int = 34
    private var carStarted: Bool = false
    
    func checkTirePressure() -> Int {
        return tirePressure
    }
    
    func start() -> Bool {
        carStarted = true
        return carStarted
    }
    
    func stop() -> Bool {
        carStarted = false
        return carStarted
    }
    
    func preStartBatteryLevelCheck() -> Bool{
        return battery > 10
    }
}

class Tesla: Car {
//no override needed at this point
}

class BMWHybrid: Car {
    
    private var fuel: Int = 100
    
    func checkFuelLevel() -> Int {
        return fuel
    }
  
    override func preStartBatteryLevelCheck() -> Bool{
        return super.preStartBatteryLevelCheck() && checkFuelLevel() > 8
    }
}
```

By using superclass we reused Tesla's code and for the fuel specific part of the BMWHybrid, we called super.preStartBatteryLevelCheck() for battery and continued with our custom property and method for fuel.

Find the swift file [here](https://github.com/YigitCiray/DesignPatternsAndPrinciples/blob/main/Design%20Principles/LiskovSubstitutionPrinciple.playground/Contents.swift)

[Clean Architecrute](https://www.amazon.com/dp/0134494164/ref=redir_mobile_desktop?_encoding=UTF8&aaxitk=8434daf3e487df1e8f2edba3e416eae3&hsa_cr_id=8875635360201&pd_rd_plhdr=t&pd_rd_r=53d11c49-53c5-4f5d-b2c6-b514524c1e6b&pd_rd_w=LGZv0&pd_rd_wg=TCGzk&ref_=sbx_be_s_sparkle_td_asin_1_img) by Robert C. Martin
