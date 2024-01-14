#web 

# [[Model View Controller {MVC}]]

This is an architectural pattern which separates applications into three main logical components:

**Model**
**View**
**Controller**

## Model
---
Stores data and its related logic and is the lowest level of the pattern that handles data

If data is being retrieved from a database, it manipulates the data and sends it back to the database using the controller

## View
---
Represents the presentation of data to the user by requesting data from the model

Includes data from charts, diagrams, and tables

## Controller
---
Handles the user interaction of an application (e.x. if a user clicks the mouse or types something with the keyboard, the controller interprets that new input)

After the new input is interpreted, the controller sends signals to the view to update in real time 

![[Pasted image 20240113135222.png]]
