# Object-Oriented-Analysis-Design-Review-11

## Object-Oriented Design: Use Case Realizations

### 6-Phase SDLC index

1. Identify problem
2. Plan and monitor project
3. Analyze details
4. **Design components**
5. Build / Develop solution
6. Deploy / Implement solution

-----

### Bridging from Analysis to Implementation

**OO-Design Process**:
- A set of detailed OO design models are built to be used for coding

**OO-Design Strength**:
- Requirements models are extended to design models
- Not reinventing the wheel
- Design models are created in parallel to actual coding/implementation with iterative SDLC

#### Design to Implementation - 3 layer architecture
1. A person enters student ID: *Input Window Object*
2. Request student object upon login: *Student Object*
3. Retrieve student information: *DB access Object*
4. The person enters personal information updates: *Input Window Object*
5. Update student information: *Student Object*
6. Save updates to DB: *DB access Object*

-----

### Model Flow

#### Information about things
**Analysis models**
- Problem domain class diagram
**Design models**
- Design class diagram
**Programming models**
- Object-oriented program classes with methods

#### Information about process flow and flow of execution
**Analysis models**
- Use case descriptions
- System sequence diagrams
- Activity diagrams
**Design models**
- Communications diagrams
- Sequence diagrams
- CRC Cards
**Programming models**
- Object-oriented program classes with methods

-----

### Object-oriented design
The pocess to identify classes, methods and the messages for a use case

**Use case driven**:
- Design is carried out use case by use case

**3 paths**:
- Simple use case: *CRC Cards*
- Medium use case: *Comunication diagram*
- Complex use case: *Sequence diagram*

#### Design class diagrams
**Stereotype**
- Way of categorizing a model element by its characteristics
- indicated by guillemots << >>

**Persistent class**
- Class whose objects exist after a system is shut down (data remembered)

**Entity class**:
- A design identifier for a problem domain class (usually persistent)

**Boundary class / view class**
- Class that exists on a system’s automation boundary
- Such as an input window form or Web page

**Controller class**
- Class that mediates between boundary classes and entity classes
- Acting as a switchboard between the view layer and domain layer

**Data access class**
- A class that is used to retrieve data from and send data to a database

#### First-cut Design class diagram
1. Use case by use case are added to the diagram
2. Pick the domain classes that are involved in the use case (see preconditions and post conditions for ideas)
3. Add a controller class to be in charge of the use case
4. Determine the initial navigation visibility requirements using the guidelines and add to diagram
5. Elaborate the attributes of each class with visibility and type
6. Note that often the associations and multiplicity are removed from the design class diagram as in text to emphasize navigation, but they are often left on

-----

### Designing with CRC Cards
**Classes, Responsibilities, Collaboration**
OO-design is about assigning Responsibilities to Classes for how they Collaborate to accomplish a use case

Usually a manual process done in a brainstorming session:
- 3×5 note cards
- 1 card per class
- Front has responsibilities and collaborations
- Back has attributes needed

#### Example of CRC Card

**Front of card**:
|      Class       |                 |
|------------------|-----------------|
| Responsibility 1 | Collaboration 1 |
| Responsibility 2 | Collaboration 2 |
| Responsibility 3 | Collaboration 3 |
| Responsibility 4 | Collaboration 4 |
| Responsibility 5 | Collaboration 5 |
| Responsibility 6 | Collaboration 6 |

**Responsibility**: use case, such as update name, update address, process sale
**Collaboration**: person/department, such as student, sales, financing

**Back of Card**:
|    Class     |
|--------------|
| Attribute 1  |
| Attribute 2  |
| Attribute 3  |
| Attribute 4  |
| Attribute 5  |
| Attribute 6  |

**Attribute**: Class variables / parameters, such as accountNo, customerName

-----

### Fundamental Principles for Good Design
**Responsibilities**: include "knowing" & "doing"

#### 1. Object Responsibilities
A design pricinple and fundamental assumption that states objects are responsible for carrying out system processing

- Objects know about other objects (associations) and they know about their attribute values. Objects know how to carry out methods, do what they are asked to do
- If deciding between two alternative designs, choose the one where objects are assigned responsibilities to collaborate to complete tasks
  - (don’t think procedurally).

#### 2. Separation of Responsibilities
- Applied to a group of classes
- Segregate classes into packages or groups based on primary focus of the classes
- Also separates permissions, which is crucial for a healthy operation
- Basis for multi-layer design – view, domain, data
- Facilitates multi-tier computer configuration

#### 3. Protection from Variations
A design principle that states parts of a system unlikely to change are separated (protected) from those that will surely change

- Separate user interface forms and pages that are likely to change from application logic
- Put database connection and SQL logic that is likely to change in a separate classes from application logic
- Use adaptor classes that are likely to change when interfacing with other systems
- If deciding between two alternative designs, choose the one where there is protection from variations

#### 4. Indirection
A design principle that states an intermediate class is placed between two classes to decouple them but still link them

- A controller class between U I classes and problem domain classes is an example
- Supports low coupling
- Indirection is used to support security by directing messages to an intermediate class as in a firewall
- If deciding between two alternative designs, choose the one where indirection reduces coupling or provides greater security

#### 5. Coupling
A quantitative measure of how closely related classes are linked (tightly or loosely coupled)

- 2 classes are tightly coupled of there are lots of associations with another class
- 2 classes are tightly coupled if there are lots of messages to another class
- It is best to have classes that are loosely coupled
- If deciding between two alternative designs, choose the one where overall coupling is less

#### 6. Cohesion
A quantitative measure of the focus or unity of purpose within a single class
  - (high or low cohesiveness)

- One class has high cohesiveness if all of its responsibilities are consistent and make sense for purpose of the class
  - A customer carries out responsibilities that naturally apply to customers
- One class has low cohesiveness if its responsibilities are broad or makeshift
- It is best to have classes that are highly cohesive
- If deciding between two alternative designs, choose the high cohesive one

-----

### Object-Oriented Design with Interaction Diagrams
**Use case realization**
- The process of elaborating the detailed design for a particular use case using interaction diagrams
**Communication diagram**
- A type of interaction diagram which emphasizes the set of objects involved in a use case
**Sequence diagram**
- A type of interaction diagram which emphasizes the sequence of messages involved in a use case

#### Communication Diagrams

**Actor**
- the external role of the person or thing that initiates the use case.  Sends messages
**Object**
- The instantiated class objects that perform the actions (methods) to execute the use case
- They receive messages and process messages
**Link**
- Simply connectors between objects to carry the messages
**Message**
- The requests for service with an originating actor or object and a destination object, which performs the requested service

#### Package Diagrams
- Define formal packages such as subsystems
- (Informally) Group classes together for understanding

**Dependency relationship**
- A relationship between packages or classes within a package in which a change of the independent component may require a change in the dependent component.
- Indicated by dashed line.  Read in the direction of the arrow
- i.e. A-->B is A depends on B. 

**Dependencies**
- View layer depends on Data Access layer
  - SearchItemWindow depends on ProductItem

-----

### Updating and Packaging the Design Classes

**1. Implementation Issues**
- View Layer Class Responsibilities
  - Display electronic forms and reports
  - Capture such input events as clicks, rollovers, and key entries
  - Display data fields
  - Accept input data
  - Edit and validate input data
  - Forward input data to the domain layer classes
  - Start and shut down the system

**2. Domain Layer Class Responsibilities**
- Create problem domain (persistent) classes.
  - Process all business rules with appropriate logic.
  - Prepare persistent classes for storage to the database.

**3. Data Access Layer Class Responsibilities**
- Establish and maintain connections to the database.
  - Contain all SQL statements.
  - Process result sets (the results of SQL executions) into appropriate domain objects.
  - Disconnect gracefully from the database.

-----

### Design Patterns
Standard design techniques, templates that are widely recognized as good practice
- Became widely accepted after the publication of Elements of Reusable Object-Oriented Software (1996)
- The best wway to handle common problem

There are architectural design patterns talked about already
  - Three layer or model-view-controller architecture

The 1st example of a programming design pattern shown is the Controller Pattern.
  - **Problem - reduce coupling**:
    - How to handle all of the messages from the view layer to classes in the problem domain layer
  - **Solution**:
    - Assign one class between the view layer and the problem domain layer that receives all messages
    - Acts as a switchboard directing messages to the problem domain

#### More Design Patterns
**Adapter**:
- Like an electrical adapter
- Place an adapter class between your system and an external system
**Factory**:
- Use factor class when creation logic is complex for a set of classes
**Singleton**:
- Use when only one instance should exist at a time and is shared 

-----

### Quiz

#### Project Management

The term “_____” refers to the organization and direction of other people to achieve a planned result within a predetermined schedule and budget.
- Project management

The final decision of project scope in an Agile project rests with the users.
- False

The sequence of tasks in a schedule that cannot be delayed without delaying the project is called the _____:
- Critical path

##### Iterative Development

In iterative development the system is grown organically
- True

An iteration normally only includes three or four of the core processes.
- False

The meeting held at the end of an iteration to determine what was successful and what can be improved is called what?
- Retrospective

#### Analysis job positions
##### Project Manager
Which of the following is NOT a common question asked by the client before giving project approval?
- Who is the project manager

Which of the following is NOT one of the activities associated with staffing the project team?
- ​Setting up programming rules and guidelines.

List the three major external responsibilities of a project manager.
- Manage Stakeholders
- Risk Management
- Organizing and motivating a project team

#### Project Sponsor
The person or group that funds the project is called the _____ 
- Project Sponsor

#### Core Processes
Determining team members and assigning responsibilities is done in which Core Process?
- 2

List the five activities of the second core process: Plan and monitor the project.
- Make sure to create a good project plan
- Oversee project schedules
- Monitoring the budget
- Tracking the scope of the project
- Monitoring project resources

Two important goals or steps within Core Process one are ____ and _____. 
- identify the solution objective
- obtain project approval

#### Diagrams
A package diagram is useful to document the various subsystems in a system.
- True

A document that identifies and lists all of the tasks to be completed within an iteration is called:
- Work breakdown structure


#### Risk & feasibility Analysis
Which is NOT one of the primary areas for risk and feasibility analysis?
- Deployment risks​

Project Quality Management is different for Agile projects because they place heavy emphasis in what additional area?
- The quality of the project processes.

Missing milestones on a project may be an indication of project that has high ____ risk:
- Schedule

#### System Analysis
The process of understanding and specifying in detail what the information system should accomplish is called systems ____.
- Analysis

Systems analysis is sometimes referred to as "understanding and specification."
- True

The primary skill required of a good systems analyst is to be able to program effectively and efficiently.
- False

Today the nature and types of jobs for information system graduates is more varied than ever before.
- True

List several (at least four) reasons why projects fail.​
- Poor planning / Unclear objectives
- Unrealistic expectations / Unrealistic objectives
- Unrealistic due dates
- Limited Resourses
- Bad Communication
- Scope Creep

#### Cost-benefit Analysis
What is the name given to the process of comparing costs and benefits to see whether investing in a new system will be beneficial?​
- Cost-benefit analysis

What is the term that describes the time period after which the dollar benefits have offset the dollar costs?
- Payback period

During analysis activities the project team build two types of diagrams: Use Case diagram and Package diagram.
- False

A benefit that can be measured in terms of dollars is called a(n):
- Tangible benefit

#### Testing

Overall functional testing is included in which Core Process?
- 6
