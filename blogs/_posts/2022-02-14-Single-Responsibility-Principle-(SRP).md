### #🖋️DesignPrinciples #💡OOP #💻SoftwareDevelopment
My fifth and last post on Principles is about SRP, this is the fifth of reverse order of -S-OLID principles with this blog post.

You can find my other blog posts [Open-Closed Principle](https://ihadahamoment.com/The-Open-Closed-Principle-(OCP)/), [Liskov Substitution Principle](https://ihadahamoment.com/Liskov-Substitution-Principle-(LSP)/), [Interface Segregation Principle](https://ihadahamoment.com/Interface-Segregation-Principle-(ISP)/) and [Dependency Inversion Principle](https://ihadahamoment.com/Dependency-Inversion-Principe-(DIP)/)

**Background**
For Uncle Bob, RSP considered as the least well understood principle because of it's inappropriate name and assumption of every module should do one thing.

1.SRP's rae description stated as 
	_A module should have on, and only **one reason to change**._
2.Rephrased version by the Robert C. Martin on [Clean Architecture](https://www.amazon.com/dp/0134494164/ref=redir_mobile_desktop?_encoding=UTF8&aaxitk=8434daf3e487df1e8f2edba3e416eae3&hsa_cr_id=8875635360201&pd_rd_plhdr=t&pd_rd_r=53d11c49-53c5-4f5d-b2c6-b514524c1e6b&pd_rd_w=LGZv0&pd_rd_wg=TCGzk&ref_=sbx_be_s_sparkle_td_asin_1_img) book as
	_A module should be responsible to one, and only one, **user or stakeholders**._
3.Final version is
	_A module should be respobsible to one, and only **one actor**._
    The module on above statement described as a source file.

**Why do we need Single Responsibility Principle?**
As described above, when a module tries to serve multiple actors when their business logic separated, it can come with a high cost of dependency. One busines logic change can directly effect another without noticing for a while. I would like to demonstrate a coding example using Swift.

 
```swift
//Bad SRP Practice
class SoccerPlayer {
    func saveTheBall(goalkeeeper:String ) { /*find the player by string and use save method*/ }
    func scoreGoal(striker:String ) { *find the player by string and use scoreGoal method*/ }
    func pass() { /*find the player by string and use pass method*/ }
    func tackle(defender:String ) { /*find the player by string and use tackle method*/ }
}

//Good SRP Practice
protocol Goalkeeper {
    func save()
}
protocol Striker {
    func score()
}
protocol Defender {
    func tackle()
}

class SoccerPlayer {
    func saveTheBall(goalkeeeper:Goalkeeper ) { goalkeeeper.save() }
    func scoreGoal(striker:Striker ) { striker.score() }
    func pass() { }
    func tackle(defender:Defender ) { defender.tackle() }
}
```

I wanted to demonstrate an example of a superclass type of SoccerPlayer with only taking a string as a method property. That example uses a string to find a player and call save method for example for the goalkeeper. The improved solution where we have the good SRP practice our protocol for specific position is not only blocking the unexpected break on a change, it also gives us an opportunity to decouple and get rid of the cohesion.  

You can find the related [code document](https://github.com/YigitCiray/DesignPatternsAndPrinciples/blob/main/Design%20Principles/SingleResponsibilityPrinciple.playground/Contents.swift) in here.
