# Fundamentals_of_Modeling

## 0. COURSE OVERVIEW  

In this course, you will model a system on ThingWorx and communicate Why the model is important. You will create a simple Thing Model and ts entities. Lastly, you will build 
and incorporate services and detine their role when modeling applications on ThingWorx. 

Prerequlsltes: ThingWorx Fundamentals Overview

Toplcs
* Thing Model  
* ThingWorx Properties
* Thing Templates and Shapes
* Model Patterns and Model Hierarchy
* ThingWorx Services


## 0. Create a Project  
l. Create a Project entity With the name **M1.GV.Project**.   
2. Save Your project.  
3. Set the Project Context to Ml.GV.ProJect.  

![Set Project Context to specific Project](https://github.com/MLA81/ThingWorx/blob/main/pics/01/001_Set_Project_Context_to.jpg)

ℹ️ Note:
Setting the Project Context will allow you to automaticaly add subsequent entities to the prolect, saving you a step in the creation process. 

_________________________________________________________________________________________________________
_________________________________________________________________________________________________________

## 1. THING MODEL  
### 1.1 Highlights  
The ThingWorx model is the backbone ot all ThingWorx applications. 
In this section, we discuss wnat the model is, Why it is important, and what features the model can have. 
Lastly, we introdUce the class project and model the first Thing tor that Project.

_________________________________________________________________________________________________________


### 1.2 WHY IS MODELING IMPORTANT?  
#### 1.2.1 Thing Model Qualities 
* Scalability  
* Flexibility  
* Interoperability  
* Collaboration  
* Seamless Plattorm  
![Why is modeling important](https://github.com/MLA81/ThingWorx/blob/main/pics/01/002_Why_is_modeling_important.jpg)


Modeling is the central data hub that all other Parts ot the ThingWorx application use. 
For that reason, it is central to the ThingWorx development process. 

_A well-designed model is:_  
* connected, organizing data trom devices and enterprtse systems.  
* used by the user intertaces.  
* used by analytics tools like ThingWorx Analytics to discover trends.  
* organized in a Way that makes it easy to deploy to other systems.  
* designed in a way that scales well, making it easy to add additional devices, device variants, or other functionality. 
* organized intuitively, meaning that entities have the properties and services that would 5e expected of them.
  For example, a retrigerator would have a temperature setpoint property, but a solar panel would not.

_________________________________________________________________________________________________________
#### 1.2.2 THINGS AS DIGIITAL TWINS FOR PHYSICAL ASSETS  
A digital twin is a digital representation ot a pnysjcal product, used to Pain Great insignt into its state, Performance, and behavior. 
* ThingWorx Things  
* Creo Models  
* Vutoria Experiences  
* Windchill BOMs  

A Thing is a type ot digital twin, used to represent a physical asset in the digital World. 
In the case ot ThingWorx, a Thing represents that device's properties and tunctionality. However, there are other types ot digital twins. Creo models and Windchill BOMs represent the physical contiguration ot a physical asset rather than its current properties and functionality. Vutoria experiences represent the physical object digitally in the real World using augmented reality. 

_________________________________________________________________________________________________________
#### 1.2.3 What is a Thing?  
* Analogous to an object or instance.  
* May have Properties With Values, tunctions, and business logic.  
* Frequently represen% and connects to assets, devices, systems, or subsystems.  
* May be helper objects With services that assist the application.  

A Thing is like an object or instance in a programming language: an instantiated entity that can do something. 
lt may have properties With values, functions you can Call, or other business logic.  

Most ot the time, Things are used to represent connections to physical devices.
They display its current state in the form ot properties and may enable you to conduct operations on the device using services. 
However, the connection does not need to be to a physical device. lt can be to an enterprise system, such as a business intelligence system. a table of data like a stream of service tickets, or a remote data store. 

Other Things may be helper objects, containing code that helps the application but does not specifically represent anything n the real world.

_________________________________________________________________________________________________________
### 1.3 ATTRIBUTES OF A THING  
A Thing can encapsulate a great deal ot functionality.  

ThingWorx categorizes this functionality into several attribute types: 
* General information about the Thing.  
* Properties ot the Thing and their history, which is stored in value streams.  
* Services or functions that can be executed against the Thing.  
* Events which are triggered, and subscriptions which respond to the events.  
* Contiguration tables, which are like properties but are not intended to change frequently.  

_________________________________________________________________________________________________________
### 1.4 GENERAL INFORMATION  

General information is basic information that identifies the Thing. This includes:  
* The Thing name, which ThingWorx uses to reference 'he Thing internally.  
* The description and documentation fields are tor reference and optional. ThingWorx does not use these 
fields, but they may be used to describe or document the Thing.  
* The project refers to the project entity that the Thing belongs to.  
* The base template is the template that this Thing is most directly derived trom, The template will provide the 
Thing with other attributes, such as properties and services. 
* The identitier is optional and may be used instead ot the name to identity the Thing. Generally, this is a 
uniquely identitying string like a serial number.  

_________________________________________________________________________________________________________
### 1.5 PROPERTIES AND VALUE STREAMS  
A property is a current data point for the Thing. For example, our Thing's battery may be at 90% power, and it may be located on Dock A. 

🔍  
**Battery**  = 90%
**Location** = Dock A

The historical values of a property may optionally be logged to a value stream. The value stream stores the 
historical value ot the property over time. For example, if we log the temperature ot Our Thing in a value stream, we can look back and view its temperature at any time the past. 

🔍  
|Time  | Value|
|:----:|:----:|
|13:00 |    89|
|12:59 |    87|
|12:58 |    83|
|12:57 |    83|

lt you do not log a property to a value stream, ThingWorx only keeps the current value, and historical values are 
lost.

_________________________________________________________________________________________________________
### 1.6 PROPERTY BASE TYPES  
Every property must have a name and a base type, which defines what kind ot data the property stores. There 
are simple base types that store a single piece ot information, like a number or a string. There are also complex 
base types such as images and JSON objects that can store entire tables, binary files, or structured data.  


**Base Types**  
* Number  
* String  
* Boolean  
* Location  
* Image  
* Intotable  
* Datetime  
* XML  
* JSON  

_________________________________________________________________________________________________________
### 1.7 SERVICES  
🔍  
**Name:** GetHeight 
**Output:** Number 
**Code:** <code>return me. ForkHeight;</code>  

Services are functions that a user can request a Thing to perform. For example, a forklift may raise or Iower the fork, stop, start, or set a destination. 

For example, our GetHeight service returns the current fork height ot a forklift. 

Most services are written in JavaScript and are far more complex than this trivial service. They can contain a 
great deal ot programming logic, input parameters, error checking, and more.  

_________________________________________________________________________________________________________
### 1.8 EVENTS AND SUBSCRIPTIONS  
🔍  
|Events|Subscriptions|
|:-----|:------------|
|Property alerts|code executed upon an event|
|Data change||
|custom events||


Events and subscriptions are interrelated.  

A Thing can fire an event under specitied conditions. For example, an event could be fired if 
* the temperature property exceeded a threshold,  
* if the destination changed,  
* or the battery was draining too rapidly. 

However, an event by itselt does not do anything. An isolated event is like the proverbial tree falling with nobody to hear it. Did it make a sound? There is no way to prove it did.
Similarly, events without a subscription do nothing. For ThingWorx to respond to an event, there must be a matching subscription.  

A subscription executes a piece ot code when the event is fired. Like services, this code is usually writing in 
JavaScript. However, unlike services. a user cannot make ThingWorx execute the code. Subscription code is 
only executed when the matching event is detected.  
An example ot a subscription would be to shut down the device when a motor overheat event is detected.

_________________________________________________________________________________________________________
❓  
Think of a product that could be represented as a Thing. 
What is an appropriate property for that Thing?
What is an appropriate event and subscription for that Thing?  

_________________________________________________________________________________________________________
### 1.9 CONFIGURATION TABLES  

|Configuration Tables |Examples        |
|:--------------------|:---------------|
|* Thing constants    |* Timer Thing   |
|* Thing type specific|* Database Thing|
||* Notification Thing|

Configuration tables store constants related to the Thing. 
They are like properties, but with a few significant differences: 
* They are not designed to change frequently. Items in a contiguration table do not change unless a 
significant event has happened to the Thing that changes it.  
* Contiguration table history cannot be stored in a value stream.  
* Contiguration table items do not have a specific timestamp or quality associated with them.  


Typically, contiguration tables are used to define how the Thing acts or connects to something. A few examples are:  
* A timer or scheduler Thing has a configuration table that specifies when it emits a timed or scheduled event.  
* A database Thing has a contiguration table containing connection information and credentials required to 
connect to a database.  
* A notitication Thing has a contiguration table instructing it what email account and credentials to use when 
sending a notitication.  


_________________________________________________________________________________________________________
### 1.10 EXCERSISE USE CASE - EXPERIENCE  
**Who is the application for?**
Inventory and logistics managers at a factory, responsable tor making sure factory workstations have the supplies they need when they need it.
They manage a fleet ot guided vehicles (GVs) that shuttle supplies around the factory. 
There are fork truck GVs that move heavy objects that factory employees cannot lift and transport GVs that shuttle smaller supplies.  


Betore building any ThingWorx application, you need to know who you are creating it tor. 
In this course, we model an application for the inventory and logistics managers at a factory. These people are 
responsible for making sure workstations have the supplies they need. 
These supplies are deltvered primarily using a fleet of guided vehicles. Currently, there are two types ot guided 
vehicles: 
* Fork truck guided vehicles move large items that are too heavy' tor employees to lift. These trucks resemble 
forklifts and bring the supplies to the correct locations. 
* Transport guided vehicles bring smaller items to the factory employees. These trucks resemble small flatbed 
trucks. Employees remove supplies from the trucks at their workstations. 
Additional types ot guided vehicles may be added in the future.

**What do the users need?**  
The logistics managers need to monitor the guided vehicles. 
All vehicles need to have their speed, temperature, and power status monitored. 
Fork trucks also need to have their weignt and fork height monitored. 
Transport trucks need to have their location and payload type monitored.


For the initial application, our managers need to monitor their fleet of guided vehicles.  

All vehicles need to monitor: 
* Temperature, to prevent the vehicle from tailing and overheating.  
* Speed, to prevent accidents and conserve power.  
* Battery level, to prevent the vehicle from running out ot power on the factory floor.  

Additionally, fork trucks need to monitor: 
* Their weight, to make sure they do not tip torward.  
* Their fork height, to make sure they do not crash into the top of a doorway.  

Transport vehicles need to monitor: 
* Their factory floor location, since workers pull inventory directly from the transport trucks as they work. 
* Their payload type, indicating what is on the truck.  

This the first iteration ot the application. Although it is a simple monitor use case, more functionality may be 
added in the future.



_________________________________________________________________________________________________________
_________________________________________________________________________________________________________
## 2. THINGWORX PROPERTIES  

_________________________________________________________________________________________________________
_________________________________________________________________________________________________________
## 3. THING TEMPLATES AND THING SHAPES 

_________________________________________________________________________________________________________
_________________________________________________________________________________________________________
## 4. MODELING PATTERNS AND MODEL HIERARCHY  

_________________________________________________________________________________________________________
_________________________________________________________________________________________________________

## 5. THINGWORX SERVICES

_________________________________________________________________________________________________________
_________________________________________________________________________________________________________
