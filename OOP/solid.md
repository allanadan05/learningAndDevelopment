# SOLID Principle

Solid principles are key in object-oriented programming. But what does each principle actually mean, and why are they significant?

**SOLID represents five principles of object-oriented programming.** Whether or not you use OOP, **knowing these principles gives you a lens into the foundations of clean code** which can be applied to many areas of programming.

**S** - Single Responsibility Principle
**O** - Open/Closed Principle
**L** - Liskov Substitution Principle
**I** - Interface Segregation Principle
**D** - Dependency Inversion Principle

Let's break down each principle :arrow_down:

## 1. Single Responsibility Principle (SRP)

Each unit of code should only have one job or responsibility. A unit can be a class, module, function, or component. This keeps the code modular and removes the risk of tight coupling.

## 2. Open-Closed Principle (OCP)

Units of code should be open for extension but closed for modification. You should be able to extend functionality with additional code rather than modifying existing ones. This principle can be applied to component-based systems such as React frontend.

## 3. Liskov Substitution Principle (LSP)

You should be able to substitute a subclass with its base class. In other words, all functionality in the base class should be utilized by all of its subclasses. If it can't, it shouldn't be in the base class.

An example of this is with a Bird base class. You might assume that it should have a fly method. But what about the birds that can't fly? Like a Penguin. In this example, fly should not be in the base class as it does not apply to all subclasses.

## 4. Interface Segregation Principle (ISP)

Provide multiple interfaces with specific responsibilities rather than a small set of general-purpose interfaces. Clients shouldn't need to know about the methods & properties that don't relate to their use case.

Complexity :arrow_down:
Code flexibility :arrow_down:

## 5. Dependency Inversion Principle (DIP)

You should depend an abstractions, not on concrete classes. Use abstractions to decouple dependencies between different parts of the systems. Direct calls between units of code shouldn't be done, instead interfaces or abstractions should be used.

