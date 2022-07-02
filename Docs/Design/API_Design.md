# API Design

## Sections of the API (CRUD)
* DB/table Creation
    * This should only happen in the backend at startup
    * See ERD for tables
* DB/table deletion
    * This shouldn't be accessible by the end user, only an admin user
    * Needs some level of "protection" around it at the API level

* Reading from specific tables 
    * Do we want to hardcode the table names in the API?
        * (Probably not, to make this harder to reuse later)
* Updating tables 
    * writing new data to the tables we're reading above

## Software Design
* We're using Golang to write this API as a golang package
* We need to remember to use the SQL inline statements insted of Go's 
`sprintf()` function otherwise the db will complain. 
* We will try and use a basic SQL library in Go, and intend not to use
an ORM such as `gorm`

This repo will be a combination of the API and backend logic, with functions
returning values so that front ends in other repos (either a CLI or a web
interface) can access the data returned. 
