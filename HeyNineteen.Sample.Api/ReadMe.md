# API

This project marks the process boundary and deals with and exposes view models only. It concerns itself with issues relate to the api layer only such as:

* Simple model validation
* Which Http status codes to respond with
* Endpoint authorisation

All operations are delegated to an application service.

(Sometimes, for simpler scenarios, the application service logic can be incorporated into the api controller.)

