#book Design Patterns, Elements of Reusable Object-Oriented Software (GOF)
6/10 - good 1st half, bad 2nd half
------------->
A dashed arrowhead line indicates a class that instantiates objects of another class. The
arrow points to the class of the instantiated objects.

______\>_____
We indicate the subclass relationship with a vertical line and a triangle

An arrowhead line with a diamond at its base denotes aggregation

A diagram may include pseudocode for an operation's implementation; if so, the code will appear in a
dog-eared box connected by a dashed line to the operation it implements.

A mixin class is a class that's intended to provide an optional interface or functionality
to other classes.

Aggregation implies that one object owns or is responsible for another object. Generally we speak of
an object having or being part of another object.

Acquaintance implies that an object merely knows of another object. Sometimesacquaintance is
called "association" or the "using" relationship. Acquainted objects mayrequest operations of each
other, but they aren't responsible for each other. Acquaintance is a weaker relationship than
aggregation and suggests much looser coupling between objects.

Design System is basically recursive composition which entails building increasingly complex
elements out of simpler ones.

#book Design Patterns, Elements of Reusable Object-Oriented Software (GOF)
part 2/2
Abstract Factory (87)
Provide an interface for creating families of related or dependent objects without specifying their
concrete classes.

Adapter (139)
Convert the interface of a class into another interface clients expect. Adapter lets classes work
together that couldn't otherwise because of incompatible interfaces.

Bridge (151)
Decouple an abstraction from its implementation so that the two can vary independently. In this case
abstraction means high level work and implementation means an interface for more specific usecases.

Builder (97)
Separate the construction of a complex object from its representation so that the same construction
process can create different representations.

Chain of Responsibility (223)
Avoid coupling the sender of a request to its receiver by giving more than one object a chance to
handle the request. Chain the receiving objects and pass the request along the chain until an object
handles it.

Command (233)
Encapsulate a request as an object, thereby letting you parameterize clients with different
requests, queue or log requests, and support undoable operations.

Composite (163) - basically a ui design system example or file system
Compose objects into tree structures to represent part-whole hierarchies. Composite lets clients
treat individual objects and compositions of objects
uniformly.

Decorator (175) - modifiy func under the same interface
Attach additional responsibilities to an object dynamically. Decorators provide a flexible
alternative to subclassing for extending functionality.

Facade (185) - decrease coupling
Provide a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level
interface that makes the subsystem easier to use.

Factory Method (107)
Define an interface for creating an object, but let subclasses decide which class to instantiate.
Factory Method lets a class defer instantiation to subclasses.

Flyweight (195)
Use sharing to support large numbers of fine-grained objects efficiently.

Interpreter (243)
Given a language, define a represention for its grammar along with an interpreter that uses the
representation to interpret sentences in the language.

Iterator (257)
Provide a way to access the elements of an aggregate object sequentially without exposing its
underlying representation.

Mediator (273) Proxy is transparent, mediator is not.
Define an object that encapsulates how a set of objects interact. Mediator promotes loose coupling
by keeping objects from referring to each other explicitly, and it lets you vary their interaction
independently.

Memento (283)
Without violating encapsulation, capture and externalize an object's internal state so that the
object can be restored to this state later.

Observer (293)
Define a one-to-many dependency between objects so that when one object changes state, all its
dependents are notified and updated automatically.

Prototype (117)
Specify the kinds of objects to create using a prototypical instance, and create new objects by
copying this prototype.

Proxy (207) - dagger.Lazy<>. Decorator adds, proxy controlls
Provide a surrogate or placeholder for another object to control access to it.

Singleton (127)
Ensure a class only has one instance, and provide a global point of access to it.

State (305)
Allow an object to alter its behavior when its internal state changes. The object will appear to
change its class.

Strategy (315)
Define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets
the algorithm vary independently from clients that use it.

Template Method (325)
Define the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template
Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's
structure.

Visitor (331)
Represent an operation to be performed on the elements of an object structure. Visitor lets you
define a new operation without changing the classes of the elements on which it operates.

![telegram-cloud-photo-size-2-5440558099342677187-x.jpg](..%2F..%2F..%2FLibrary%2FGroup%20Containers%2F6N38VWS5BX.ru.keepcoder.Telegram%2Fappstore%2Faccount-18037556929251400032%2Fpostbox%2Fmedia%2Ftelegram-cloud-photo-size-2-5440558099342677187-x.jpg)

GRASP:
Information expert - who has info, does calculations
Creator - who needs obj - creates it
Controller - orchestrates input events
Low Coupling - SRP
High Cohesion - SRP
Polymorphism - Polymorphism
Pure fabrication - not an entity
Indirection - dependency inversion
Protected Variation - use 8 previous

Prototype pattern is just Kotlin’s data class .copy()
Repository using different strategies of saving objects(sharedPrefs, db, backend) is Strategy pattern
