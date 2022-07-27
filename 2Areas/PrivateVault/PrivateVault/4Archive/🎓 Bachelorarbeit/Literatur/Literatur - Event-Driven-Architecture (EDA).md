
## Richards and Media - Software Architecture Patterns
Extracted Annotations (29/05/2020, 16:27:34)

"The event-driven architecture pattern is a popular distributed asynchronous architecture pattern used to produce highly scalable applications. It is also highly adaptable and can be used for small applications and as well as large, complex ones. The event-driven architecture is made up of highly decoupled, single-purpose event processing components that asynchronously receive and process events." (Richards and Media :73)

"The event-driven architecture pattern consists of two main topolo‐ gies, the mediator and the broker. The mediator topology is com‐ monly used when you need to orchestrate multiple steps within an event through a central mediator, whereas the broker topology is used when you want to chain events together without the use of a central mediator. Because the architecture characteristics and imple‐ mentation strategies differ between these two topologies, it is impor‐ tant to understand each one to know which is best suited for your particular situation." (Richards and Media :73)

"The broker topology differs from the mediator topology in that there is no central event mediator; rather, the message flow is dis‐ tributed across the event processor components in a chain-like fashion through a lightweight message broker (e.g., ActiveMQ, HornetQ, etc.). This topology is useful when you have a relatively simple event processing flow and you do not want (or need) central event orchestration." (Richards and Media :76)

"There are two main types of architecture components within the broker topology: a broker component and an event processor compo‐ nent. The broker component can be centralized or federated and contains all of the event channels that are used within the event flow." (Richards and Media :76)

"The event channels contained within the broker component can be message queues, message topics, or a combination of both." (Richards and Media :77)

"This topology is illustrated in Figure 2-3. As you can see from the diagram, there is no central event-mediator component controlling and orchestrating the initial event; rather, each event-processor component is responsible for processing an event and publishing a new event indicating the action it just performed." (Richards and Media :77)

"The event-driven architecture pattern is a relatively complex pattern to implement, primarily due to its asynchronous distributed nature. When implementing this pattern, you must address various dis‐ tributed architecture issues, such as remote process availability, lack of responsiveness, and broker reconnection logic in the event of a broker or mediator failure." (Richards and Media :79)

**Agility**
"Overall agility is the ability to respond quickly to a constantly changing environment. Since event-processor com‐ ponents are single-purpose and completely decoupled from other event processor components, changes are generally iso‐ lated to one or a few event processors and can be made quickly without impacting other components." (Richards and Media :80)

**Easy of deployment**
"Overall this pattern is relatively easy to deploy due to the decoupled nature of the event-processor components." (Richards and Media :81)

**Testability**
While individual unit testing is not overly difficult, it does require some sort of specialized testing client or testing tool to generate events. Testing is also complicated by the asynchronous nature of this pattern.

**Performance**
"While it is certainly possible to implement an eventdriven architecture that does not perform well due to all the messaging infrastructure involved, in general, the pattern ach‐ ieves high performance through its asynchronous capabili‐ ties; in other words, the ability to perform decoupled, parallel asynchronous operations outweighs the cost of queuing and dequeuing messages." (Richards and Media :81)

**Scalability**
"Scalability is naturally achieved in this pattern through highly independent and decoupled event processors. Each event processor can be scaled separately, allowing for fine-grained scalability" (Richards and Media :81)

**Easy of development**
"Development can be somewhat complicated due to the asynchronous nature of the pattern as well as contract cre‐ ation and the need for more advanced error handling condi‐ tions within the code for unresponsive event processors and failed brokers." (Richards and Media :81)