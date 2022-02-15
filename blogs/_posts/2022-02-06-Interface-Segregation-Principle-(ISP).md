### Object Oriented Programming - Design Principles
My second post is about ISP, I am on I of SOL-I-D principles on this document.

You can find my other blog post about [Dependency Inversion Principle](https://ihadahamoment.com/Dependency-Inversion-Principe-(DIP)/).

**Why do we need Interface Segregation Principle?**
Interface is a clean way to form a contract between the class and the outside world. As abstraction is the essential part of Object Oriented design, ISP focuses on contracting unnecessary methods with class. 

By design we are forced to implement all the methods of interfaces. Considered that all the applications we develop are evolving creatures, we extend the interface and the classes with new methods and functionalities. We use interfaces to have loose coupling and abstraction but extending interface will require new method on each class confirming the interface. 

The Interface Segregation Principle states that **clients should not be forced to implement interfaces they don't use**. 

Since I am a software engineer, I would like to trade off smaller interfaces with larger ones.
Interface with multiple dimension of responsility methods, let use an example of payment

// Bad ISP pratice
```swift
protocol Payment{
	func usemyBTCWallet()
	func useCreditCard()
	func useCheck()
}
```

// Good ISP practice
```swift
protocol BitcoinPayment{
	func usemyBTCWallet()
}
protocol CreditCardPayment{
	func useCreditCard()
}
protocol CheckPayment{
	func useCheck()
}
```


**Bad ISP** practice has all the payments method in one place. it is an abstraction for all payments, while I would like to use other cryptocurrencies but for specific places where user perefer to use BTC as a payment method.
That scenario would end up adding the 4th method to my Payment protocol and all the classes that confirming this protocol has to have the new method. Since will not be used, literally end up as this in the codebase.

```swift
class CartUIViewController: Payment{
	func usemyBTCWallet() {//functionality}
	func useCreditCard() {//functionality}
	func useCheck() {//functionality}
	func useETHWaller() {
    	//method not used
    }
}
```



**Good ISP** practice suggests you to create new ETH protocol. 
```swift
protocol EtheriumPayment{
	func usemyETHWallet()
}
```
I think main advantage is on growing codebases, we know that some payment methods needs to grow like "usemyBTCLightningAccount()" and under that circumstances this change will be always valid method to fill in by the classes confirming the protocl.
```swift
protocol BitcoinPayment{
	func usemyBTCWallet()
	func usemyBTCLightningAccount()
}
```

Another round of trade off is about how we can maintain the amount of interfaces we have, if we will literally create a new one for each of them. I prefer numerosity over less amount of bulky interfaces. My focus is on reusability, mostly ending up with many interfaces to confirm on a single class but good thing is when you evolve the code you know that each change will be made on only necessary files.

Find the swift file [here](https://github.com/YigitCiray/DesignPatternsAndPrinciples/blob/main/Design%20Principles/interfaceSegregationPrinciple.playground/Contents.swift)
