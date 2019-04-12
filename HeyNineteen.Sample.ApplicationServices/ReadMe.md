# Application Services

This layer consists of a set of services that implement the **use cases** of an application. Each service coordinates and orchestrates operations and activities to achieve the desired goal. These services to not contain domain logic.

In order to do this, application services interact with the domain, or directly with repositories via interfaces defined in the domain.

The application service is also responsible for transalting the view models of the api to and from the domain model.

In simpler scenarios, the application service layer can be implemented directly in an api controller.
