* **Transaction Script (110)**
    * Organizes business logic by procedures where each procedure handles a single request from the presentation.
        * \+: Simple
        * \-: Maintainability and scalability - bad
* **Domain Model (116)**
    * An object model of the domain that incorporates both behavior and data.
        * \+: Flexibility, Maintainability, Reusability
        * \-: Complexity, Performance Concerns
* **Table Module (125)**
    * A single instance that handles the business logic for all rows in a database table or view.
        * \+ Easier integration with the underlying table-oriented data structures
        * \- Harder to handle complex logic `compared to Domain Model
* **Remote Facades (388)**
    * Provides a coarse-grained facade on fine-grained objects to improve efficiency over a network.
* **Data Transfer Object(401)**
    * An object that carries data between processes in order to reduce the number of method calls.
//TODO proceed from page 27