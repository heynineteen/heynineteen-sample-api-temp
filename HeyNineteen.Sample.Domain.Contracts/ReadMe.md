# Domain

This where the business concepts are defined and the business logic of the application is implemented.  

Classes in this layer have *no dependencies* on any classes or libraries outside of this layer. Classes from any other layer in the application are free to take a dependency on classes in the domain layer.

Since the domain layer is completely independent, there is no requirement for the structure of domain classes to reflect either that of view models exposed by the api or data models exposed by the infrastructure layer.

## Domain objects == Business objects == Domain entities

These are classes that contain both data **and** behaviour. We avoid the anaemic domain model be incorporating business behaviour into our classes. These classes can have complex interactions between each other and be part of inheritance hierarchies where appropriate.

These classes are usually immutable or contain logic that carefully manages any changes in state.

If part of a hierarchy, these objects will form part of an aggregate. Each aggregate has an aggregate root which is responsible for ensuring the consistency of the data in the aggregate as a whole.

Domain classes are persistence agnostic. Persistance or retrieval from an external data store is the responsibility of repositories. 

## Domain Services

If domain logic does not fit neatly into the realm of a single domain class, then a domain service may be necessary.

A domain service contains functionality, but no state, that operate on more than one domain object to achieve a business goal.

A domain service will also make use of the domain logic that is internal to the domain objects.

## Contracts
These fall into 3 categories:

* interfaces that define how non-domain code comnunicates with domain services
* interfaces that define how both non-domain code and domain services communicate with repositories of domain objects
* domain objects that make up the parameters and return values of the above 2 categories of contract

### Domain service contracts
These define interfaces of domain services so they can be injected into clients in the usual way.

### Repository contracts
Repository implementations are defined in the infrastructure layer as they interact with data stores such as databases and web services. However, the interfaces they implement are defined in the domain. This is because the domain should not depend on types in any other layer, so it defines interfaces it needs to interact with the outside world for other layers to implement.

### Domain objects 
These will form part of parameters to and return values of methods defined in the interfaces of domain services and repositories. As such, they form part of the contracts of those interfaces.

### Splitting out the domain
Given the different flavours of types within the domain it could be argued that the domain could be split into separate projects:

* Domain.Services - contains domain service implementations
* Domain.Contracts - contains interfaces of domain services, repositories and the implementations of domain objects. This can be split further into:
    * Domain.Contracts - contains interfaces of domain services, repositories
    * Domain - domain objects