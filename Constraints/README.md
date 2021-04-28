# REST API Architecture Constraint

## Client-Server
*"REST application should have Client-Server architecture"*

  - Client: Requests the resources
  - Server: serves tge resources as a response. Server may serve multiple resources and multiple clients.

> Client-Server should NOT run in same process

![Client-Server](./../docs/images/clientServerInSameProcess.png)  

So technically this is feasible, but it's definitely not a good idea as the client component and the server component will be very tightly coupled. Such tight couple will lead to many challenges. And most times it may not even be possible to package the client and server in the same process to achieve highest level or decoupling between the client and the server. The client will make request to the server or some kind of network.  This way, the client and server can change independently without impacting each other.  

This decoupled architecture leads to what is known as the separation of concerns. 

The client and the server in have a different set of concerns that they need to address and manage on the server end.
![Client-Server Concerns](./../docs/images/clientServerConcern.png)  

The two NS can continue to independently manage these concerns without impacting the other end, as long as the uniform interface between the client and the server is maintained.

Another advantage of the decoupled architectural approach is that the client and the server can evolve independently. 

- The client server architecture constraint provides the foundation for the implementation of risk APIs.
- This architectural style is suggested as it leads to decoupling between the client.
- The client side and the server side can change without impacting the other site as long as the uniform interface is maintained.
- Another advantage is separation of concern.  A different set of concerns that they can manage independently, the client and the server can evolve over a period of time in an independent fashion.

___

## Uniform Interface

*"Client and Server share a common Technical Interface"*
  - interface  defines the contract between the client and the server
  - technical implies that there is no business context for this contract.

There are 4 guiding principles used for defining the contract between the client and the server and they are: 

  - **Individual resources are identified in the Request (URI/URL)**  
  - **Representation of the resources**  
  may be used by the client to manipulate the resource state.
  - **Self descriptive messages - metadata**  
  the messages are self descriptive. There is metadata contained in the request and responses that can be used by the client and the server.
  - **Hypermedia**  
  server can only send back responses but hypermedia links that can be used by the client for further discovery of resources.

> Uniform Interface = Contract between client and server

___

## Statelessness

*"Client MUST manage its own state thus making the server stateless"*

**Typical Web Application**
![Typical Web Application](./../docs/images/typicalWebApp.png)  
For every client that is connecting to the Web application, the Web application manages the state independently. This practice of managing the state in the server is not considered a good practice for building RESTful APIs.

> The RESTful API server does not manage the state of the client. Each of the client connecting to the RESTful Apps server manages its own state.

The management implementation is left to the client application and is not governed or defined by the REST API server.
![Client Manage its own State](./../docs/images/clientManagesItsOwnState.png)

The benefit of this approach is that it simplifies the implementation of the RESTful API. It allows the API server to easily scale horizontally and it reduces the resource need for the observer.

The request received from the client applications or address clients are self-contained. And what that means is that server receives all of the state information that it needs for processing the client request.

> Server receives state info from the client applications

> Each request received by the server is treated as an independent request without regard to any previous request from the same client or from other clients.

![Statelessness](./../docs/images/statelessness.png)

___
