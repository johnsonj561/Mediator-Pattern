----------------------------------------------------------------------------------------------------------------
Title: The Mediator Pattern

Sources:
Notes below regarding mediator pattern taken from "Design Patterns - Elements of Reusable Object-Oriented Software"
By Gamma, Helm, Johnson, Vlissides

Example Code provided by Derek Banas:
Tutorial: 
Source Code: 

Author: Justin J

Purpose: FAU Object Oriented Software Design Course, Sprint 2017

----------------------------------------------------------------------------------------------------------------

Intent
- define an object that encapsulates how a set of objects interact
- promotes loose coupling by keeping objects from referring to each other explicitly
- allows user to vary interaction of components

Motivation
- OO design encourages distribution of behavior among objects
	- this can lead to many connections between objects, worst case scenario every object knows about each other
- partitioning system into components enhances reusability, but excessive interconnections can again reduce it
	- objects become dependent on each other
- avoid this concern by encapsulating collective behavior in separate mediator object
	- mediator controls and coordinates interaction between the group of objects
	- acts as a 'hub' for communication between objects
	- individual objects do not know about each other, they only know of the mediator

Applicability
- use when objects communicate in well defined by complex ways, when resulting interdependencies are unstructured and difficult to understand
- when reusing an object is difficult because it refers to and communicates with many other objects
- a behavior that's distributed between several classes should be customizable without a lot of subclassing
	
Structure
- see MediatorPattern.png for details

Participants
- mediator
	- defines interface for communicating with Colleague objects
- concrete mediator
	- implements cooperative behavior by coordinating Colleague objects
	- knows and maintains its colleagues
- colleague classes
	- each Colleague class knows its Mediator object
	- each colleague communicates with its mediator whenever it would have otherwise communicated with another colleague

Collaborations
- colleagues send and receive requests from a mediator object
- mediator implements the cooperative behavior by routing requests between the appropriate colleagues

Consequences
- limits subclassing - localizes behavior that would otherwise be distributed among several objects
- decouples colleagues - promotes loose coupling between colleagues
- simplifies object protocols - mediator replaces many to many interactions with ont to many interactions, therefore simplifying functionality
- abstracts how objects cooperate
- centralizes control

Implementation
- there is no need to define abstract mediator class when colleagues work with only one mediator
	- the abstract coupling that mediator provides lets colleagues work with different mediator subclasses
- colleagues have to communicate with their mediator when an event of interest occurs
	- can be implemented as observer pattern.colleagues act as subjects and send notifications to mediator when state changes
		- mediator responds by propagating the effects of the change to other colleagues

Related Patterns
- facade pattern
- observer pattern
