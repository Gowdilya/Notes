

**Observers are aware of the Subject, but Publish-Subscribe does not require Subjects and Observers to know about each other because they communicate through a central broker**.

Developers mainly use ==Observer patterns to carry out data exchange between components of a single application==. To a large extent, such an exchange happens synchronously. In the Pub-Sub pattern, the data exchange can happen across various applications and occurs asynchronously in many cases. However, synchronous communication is possible with producer APIs and consumer APIs of applications implementing Pub-Sub patterns.

In the Observer pattern, the data provider knows the observer. In the Pub-Sub pattern, the publisher does not know about its subscribers, and these two groups can exist and operate without each other. The data exchange in Pub-Sub happens through the bridging component, the broker.

Pub-Sub patterns promote a decoupled architecture, unlike the Observer pattern.

# Observer pattern
https://www.educative.io/answers/how-observer-and-iterator-patterns-work-in-rxjs
**[[RxJS]] is a library that implements the Observer Design Pattern** with reactive programming.

# Publisher-Subscriber

Introduce an asynchronous messaging subsystem that includes the following:

- An input messaging channel used by the sender. The sender packages events into messages, using a known message format, and sends these messages via the input channel. The sender in this pattern is also called the _publisher_.

- One output messaging channel per consumer. The consumers are known as _subscribers_.
    
- A mechanism for copying each message from the input channel to the output channels for all subscribers interested in that message. This operation is typically handled by an intermediary such as a message broker or event bus.
    

The following diagram shows the logical components of this patte
rn:
![[Pasted image 20230807231957.png]]


# Observer Pattern