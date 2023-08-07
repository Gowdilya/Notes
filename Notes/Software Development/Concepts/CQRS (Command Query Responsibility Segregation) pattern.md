
https://www.youtube.com/watch?v=akTfrZhHc5Y

The CQRS pattern assumes that a programmer will use three main types of _**requesting classes**_ to trigger and orchestrate business logic:

**Commands** that are responsible for altering state-of-application data; 

**Queries** that are used solely for retrieving application data without mutating the application state;

**Events** that can be raised throughout business logic execution. For instance, ones that may trigger some additional processing of data after the execution of a command.
The event-driven pattern is regularly used in areas such as:

- Distributed systems
- Microservices architectures
- Real-time applications
- Event sourcing and CQRS

- Loose coupling between components so its very easy to maintain and scale the system.
- Improved scalability and reliability so as components can react to events in parallelly.
- Improved agility and faster time into the market as every new features can be added by adding new event handlers.


CQRS vs REST

REST is more tightly coupled.


CQRS stands for ==Command and Query Responsibility Segregation==, a pattern that separates read and update operations for a data store. Implementing CQRS in your application can maximize its performance, scalability, and security.
https://www.makeuseof.com/nest-js-cqrs/

https://www.learmoreseekmore.com/2021/10/nestjs-application-using-cqrs-design-pattern.html

[[Event Sourcing]]

## CRUD
![[Screenshot 2023-08-02 at 9.10.13 PM.png]]

CQRS vs CRUD
Read operations map to Queries
Create Update Delete are replaced by Commands
Commands are not data centric![[Screenshot 2023-08-02 at 9.09.59 PM.png]]

A command represents the inetention to perform a Task, A command returns no data ![[Screenshot 2023-08-02 at 11.32.03 PM.png]]![[Screenshot 2023-08-02 at 11.34.39 PM.png]]

1. **CRUD:** In this pattern, the system will always be consistent as reads and writes are done in the same Db. So, any effect on any write will be instantly visible in later reads. This type of consistency is called **strong consistency**.
2. **CQRS:** The consistency which we saw in CQRS is called eventual consistency because any change in the write side will take some time for its effects to show on the read side. There is no escaping from eventual consistency in CQRS. But due to this eventual consistency, we should not ignore CQRS, instead, we should learn to embrace eventual consistency. That means we should design our application such that eventual consistency will not impact the application adversely. For example, consider we are designing a booking application in CQRS. Here if a person sees that 10 items are available (from the read side) and tries to book those 10 items. But as we know due to eventual consistency that maybe the person was seeing older data and those 10 would have been sold. To tackle these kinds of problems, we will just have to put one condition in our write query such that the Db does not become inconsistent. This was just one simple example for each application eventual consistency should be handled differently.1. **CRUD:** In this pattern, the system will always be consistent as reads and writes are done in the same Db. So, any effect on any write will be instantly visible in later reads. This type of consistency is called **strong consistency**.
2. **CQRS:** The consistency which we saw in CQRS is called eventual consistency because any change in the write side will take some time for its effects to show on the read side. There is no escaping from eventual consistency in CQRS. But due to this eventual consistency, we should not ignore CQRS, instead, we should learn to embrace eventual consistency. That means we should design our application such that eventual consistency will not impact the application adversely. For example, consider we are designing a booking application in CQRS. Here if a person sees that 10 items are available (from the read side) and tries to book those 10 items. But as we know due to eventual consistency that maybe the person was seeing older data and those 10 would have been sold. To tackle these kinds of problems, we will just have to put one condition in our write query such that the Db does not become inconsistent. This was just one simple example for each application eventual consistency should be handled differently.
3. 