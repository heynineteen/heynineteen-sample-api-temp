# Repositories

A repository implements an interface that is implemented in the domain. It is reponsible for making domain objects available to other layers and for persisting them if necesary. 

The repository forms the bridge between the domain and wherever the assosiated data is stored, and maps data between the structure of the domain model and that of the data store (and back again). There is no requirement for the domain model to reflect the stucture of the way the data modelled in storage. In fact it is often necessary to build and domain objects from more than one data source.


