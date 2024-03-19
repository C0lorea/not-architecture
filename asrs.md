# Group

PL1

- Ahmed Selim Hammami (2023239425)
- Elyot Hamon (2023255505)
- João Manuel Monteiro Penacho (2006124245)
- Thiago Lütz Dias (2023171576)

The system could be used within a domestic / business environment. The following
scenarios were thought as the necessities of a retail store. They aim to
exemplify what reasons may make a store to buy such a system.

# Scenarios

The main problem is employee interaction with the customers. The first scenario
is related to how the work and workplace may affect the employees mood, and as a
consequence the interaction.

The second one is associated with how our employees use their working hours. We
want to maximize the time they have for interacting with the client and diminish
the burden of managing products / resources.

## Self opening / closing

### Description

The necessity of having employees turn everything on in the shop sometimes
leaves them in a bad mood (it's tedious work). As a result of that, they may be
rude to customers. On the other hand, the last shift employees are thinking
about how much they will still need to work after the store closes, making them
not want to interact with the customers, due to how tired they are. We want to
improve their working conditions.

### Types of Devices

- cleaning robots
- smart lights
- smart plugs (automatically turn on machines)
- smart AC / Heater

## Inventory Management

### Description

Keeping track of products and inventory is a necessity, however, it takes a lot
of time from our employees. This time is time they are not interacting and
convincing customers to buy from us. If we could lower the time our employees
spend on inventory, they would have more time for dealing with customers.
Besides that, we could use data about how fast / slow our products are sold and
be more efficient in our re-supllying.

### Types of Devices

- Inventory system (software but thought it was important enough to be here)
- RFID tags / beacons (location, humidity or temperature (niche))
- Shelf sensors (detect when a product has been picked up)
- Digital price tags (with storage availability)

# Stakeholders

- _SH1_ - Store owner
- _SH2_ - Store employee
- _SH3_ - Store manager
- _SH4_ - Development team
- _SH5_ - Hosting platform

# Architectural Drivers (Requirements)

## Functional Requirements

- _FR1_ - Device Integration: allow integration with any IoT device of the main
  brands (e.g Google, Alexa, LG, Apple)
- _FR2_ - Extendability: allow developers to extend their smart home/office
  through access to an API
- _FR3_ - Interface: the system must be available as a website and as a mobile
  app
- _FR4_ - Software Integration: allow integration with major inventory
  management software
- _FR5_ - Control: allow the user to schedule when the shop should "self open"
  and "self close", and which machines should be turned on/off
- _FR6_ - Metrics: the system must collect inventory data and display metrics,
  such as the item most sold, the item that gave most profit, etc
- _FR7_ - Customizability: the users must be able to add, delete, and edit
  devices; give custom names to them, and reorder them
- _FR8_ - Inventory: automatically update number of available items

## Quality Attributes

### _QA1_ - Availability

Ensure that the system will be available for atleast 99%
of working hours (9am - 5pm)

- **Source** -> Server deployed in a server farm (e.g AWS)
- **Stimulus** -> Server fails during work hours, is not available
- **Artifact** -> Server
- **Environment** -> Production
- **Response** -> Warn cluster of failure and restart (cluster management should
  reroute requests to another instance)
- **Response Measure** -> Make system available again within 1min

### _QA2_ - Performance

The system should take at most 1s of computation time, disregarding network

- **Source** -> API and DB operations
- **Stimulus** -> Request performed by the client (web / mobile)
- **Artifact** -> API
- **Environment** -> Production, Staging and Development
- **Response** -> Log operations and time required
- **Response Measure** -> Detect and record faults

### _QA3_ - Privacy

Ensure that the _data_ is well protected and encrypted

- **Source** -> User data
- **Stimulus** -> Someone accesses the Database
- **Artifact** -> Database
- **Environment** -> Production and Staging
- **Response** -> Data is not human readable (encrypted)
- **Response Measure** -> Encrypt data on storing and decrypt on reading

### _QA4_ - Security

System should be secure agains malicious users, not being vulnerable to hack
attempts, both from local and external sources

- **Source** -> Malicious user
- **Stimulus** -> Tries to find vulnerabilities within the system
- **Artifact** -> Whole system
- **Environment** -> Production
- **Response** -> Notify maintainers of suspicious activity
- **Response Measure** -> Notification

### _QA5_ - Load

When not self hosted, the system should comfortably deal with 5 thousand
requests / minute

- **Source** -> Server
- **Stimulus** -> Multiple requests sent by clients
- **Artifact** -> Server
- **Environment** -> Production
- **Response** -> Automatically deploy multiple instances and balance load
- **Response Measure** -> ???

## Constraints

### Technical

- _TC1_ - Language: the API must be implemented in Go
- _TC2_ - Host: the system must have the option of being self hosted
- _TC3_ - Compatibility: assure that the mobile application works on both
  android and iOS devices, and the website works in all Chromium based browsers

### Business

- _BC1_ - Data: the system must abide to data protection laws
- _BC2_ - Cost: the upkeep of the system must not surpass $5.000/month
- _!BC3_ - Process: the development must follow the SCRUM principles, with one of
  the stores employees as domain expert
