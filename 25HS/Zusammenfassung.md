
</style>
# Zusammenfassung Data Product and Services

# Basics of Data Products and Services

## Definition of Services
**macroeconomic view of services**
- primary sector: agriculture
- secondary sector: manufacturing
- tertiary sector: services (in CH growing sector since 1800, main sector today)
	- quartenary sector: information services - division of labour in transport, communication, trade, and administration through high information content.
	- quinary sector: human services - Services that change and improve the recipient in health, education annd recreational services.

![different services in an economy](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/services.png){width=800  height=auto}

## Value of data & analytics today

Most large companies have data-driven business models. Good data accquisition and analyzation of data provide a huge value.

## Importance of data product thinking

Top Big Data challenges:
- Determing how to get value from big data
- Defining strategy
- Obtaining skills and capabillities necessary
- Integratting multiple data soources
- Infrastructure and/or architecture
- Security, privacy and data quality risks and issues
- funding
- understanding of big data
- leadership / organizational issues

Data product concepts provided reliably added value, therefore a data product:
1. generates a customer benefit or satisfies customer needs
2. is relevant for more than one user
3. goes through a production process and is produced with quality
4. is managed within a product life cycle
5. is a combination of data assets, data related capabillities that together form/contribute to value added prooduct offerings

### Data assets
They belong to a multitude of different data types, like
- transactional data
- demographic data
- time series data
- location data
- IoT Data
- etc.

### Data capabillities
They span a wide variety of areas.

![data related capabillities](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/dataCapabillities.png){width=800  height=auto}

### value-added product offerings
There are four mechanisms of how data and analytics provide value.

![data offerings](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/productOfferings.png){width=800  height=auto}

Prescriptive Analytics translate trends/prediction into actions.


## Three types of data products

1. **Data as a service**
	- This product does not exists without the data it is its , since together with the analytics it generates sales.
	- Swiss Post Adress Management service
	- MS Azure Computer Vision service
2. **Data-enhanced products**
	- Extends an existing business model by increasing the value of another product (new customer value proposition new revenue streams).
	- Tesla Auto Pilot
	- Bosch Predicitve Maintenance
3. **Data as insights**
	- Supports business model to improve internal processes for example. It benefits decision making for product innovation and management.
	- Manufacturing-Analytics
	- Supply Chain-Analytics
	- Marketing-Analytics

## Data product design process

### Cross-industry standard process for data mining 

![CRISP-DM](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/crisp.png){width=800  height=auto}

data understanding is often forgotten but a very important step

**Generic Tasks and Outputs of the phases**

![CRISP-DM](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/crispTasks.png){width=800  height=auto}

(don't need to memorize the outputs for the exam. only understanding on the high level is needed)



# Waiting Queues

Examples
- Waiting at a counter
- Waiting for the machine to become free
- Waiting for vacant call center employees
- Waiting for a free doctor
- Waiting for a green light

Questions
- How long do I have to wait?
- How long will I be "in the system"?
- How likely is it that I won't have to wait?

## Capacity Managment
Most services fullfill IHIP properties
- Intangible: Services are no physical object, they are experienced
- Heterogeneous: customer involement
- Instantaneous: 
- Perishable:

--> Operations managers are concerned with ensuring that the service process has **sufﬁcient resources** to deal with the anticipated levels of **customer demand** in such a way that **quality of service** meets pre-set targets in the most **cost-effective ** manner.

## Strategies 
- **Low capacity**: steady caapcity and deal with the consequences of customer insatisfaction and service quality
- **Chase capacity**: capacity matches predicted demand
- **Demand management**: influence/ notch cusstomers to prefer non peak times

## Queue design
- Multiple lines, multiple servers
- single line, multiple servers

### Queue Parameters 
Arrival rate $\lambda$
Service time S
Notation: a/b/c
a Probability distribution of the arrival rate
	D = Deterministic
	M = Poisson
	G = General
b Probability distribution of service time 
	D = Deterministic
	M = Exponential
	G = General
c Number of servers

![Queue Characeristics](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/queueCharacterisitcs.png){width=800  height=auto}

### Performance M/M/1 Queues
![](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/mm1Queues.png){width=800  height=auto}



### Markov chain of the M/M/1 Queue
![](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/markovChain.png){width=800  height=auto}
System Probability: P<sub>n</sub> = p<sup>n</sup> (1-p)
Queue Probability: P<sub>n+1</sub> = p<sup>n+1</sup> (1-p), n>1 (Queue empty but service ppl is directly servicing)
### Example Post Office
- single service employee
- 22 customers/h (lambda, poisson dist.)
- 30 customers/h (mu, exp. dist.)
**Questions**
1. To what extent of his time is the postal employee busy serving customers?
	22/30 = 73.3%
2. What is the probability that the post office is empty?
	P<sub>0</sub> = (22/30)<sup>0</sup> (1 - 22/30) = 26.7%
	a) What is the probability that the queue in the post office is empty?
	p<sup>0</sup>(1-p) + p<sup>1</sup>(1-p) = 1-p<sup>2</sup>
	1-p<sup>2</sup> = (22/30)<sup>0</sup> (1- 22/30) + (22/30)<sup>1</sup> (1- 22/30)
3. What is the probability that exactly two customers will be in the post office?
	P<sub>2</sub> = (22/30)<sup>2</sup> (1 - 22/30) = 14.3%
	a) What is the probability that exactly one customer will be in the queue?	
	14.3% 1 in Queue 1 Serviced --> 2 customers are in the office
4. What is the probability that there will be three or fewer customers in the post office?
	P<sub>0</sub> + P<sub>1</sub> + P<sub>2</sub> + P<sub>3</sub> = 71%
5. What is the expected number of customers in the post office? --> LQ and LS (length queue/system)
	LS = (22/30)/(1 - 22/30) = 2.75
6. What is the expected number of customers served by the postal officer?
	LS - LQ = p = 0.733
8. What is the expected number of customers in the queue?
	LS - p = 2.75 - 0.733 = 2.02

--> For a functioning system or model arrival rate has to be smaller than the serrrvice rate
### M/M/1 waiting queue network
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/mm1network.png){width=800  height=auto}
Incomin arrival rate = outcoming arrival rate --> Average Time in System or Service Time is equal to the sum of the individual stations
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/mm1combinations.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/mm1networkformula.png){width=800  height=auto}

# Demand management (= Yield management, Price optimization)
Revenue Management embraces techniques to allocate limited resources to different types of 
customers at different prices in order to maximize company revenues.
-> Smooth the load on resources by influencing the demand.

Revenue managment is most effective:
- product can be sold in advance because it has a limited shelf life
- limited product capacity and increasing capacity takes a lot of effort
- market/customer can be divided into segments
- low variable cost, flying with full or empty plane is roughly the same
- fluctuating demand, demand is not known at time of decision
- adjustable pricing

Revenue management is used in airlines, hotels, car rentals, freight but also in energy, broadcasting, health services, golf, clothing industry.

### Case example American airlines
- They need to sell the right payces to the right customers at the right price. 
- The value of a seat varies depending on demand. (seat hortage<->high prices, as soon as plane takes off seats are worthless)
- Strategy has to consider millions of bookings, cacellation and corrections. Business model needs to divide problems into overbooking, dsicounts, data-traffic management
Proof their strategy works: trillion in revenue and other airline applied their revenue Management

![case example](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/germanwings.png){width=800  height=auto}

## Demand functions (Preis-Absatz-Funktion)
Equation representing the relationship between the quantity of a good or service consumers are willing and able to buy and the factors influencing that quantity, primarily price, but also income, tastes, population, and expectations.

### Continuous demand function
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/demandfunction.png){width=800  height=auto}

### Continuous demand function with one segment
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/demandfunction2.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/demandfunction2solution.png){width=800  height=auto}

### Continuous demand function with two segment
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/demandfunction3.png){width=800  height=auto}

![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/demandfunction4.png){width=800  height=auto}

![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/demandfunction5.png){width=800  height=auto}

## How to segment customers

### Segmentation objectives
- time
- location
- flexibility
- groups
- variants

# Booking Control
There are two approaches, they have a interrealationship:
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/bookingcontrol.png){width=800  height=auto}
When using booking and protection limits the same request are accepted or rejected.Depending on the situation one of them is easier to handle.
It is nested because theoretically premium passegers can afford all seats
## Nested policy implementation
 **Booking limits**
 1. Start
 2. In class k a demand y<sub>k</sub> occurs.
 3. The demand met min(y<sub>k</sub>, B<sub>k</sub>)
 4. Subtract min(y<sub>k</sub>, B<sub>k</sub>) from all booking limits until they reach 0
 5. End
 
**Protection limits** an alternative approach
 ![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/protectionlimits.png){width=800  height=auto}
 
### example
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/bookinglimits.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/unorderedbookinglimits.png){width=800  height=auto}
 
## The optimal booking limits
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/optimalbookinglimits.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/cum.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/normaldist.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/recapnormaldist.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/optimalbookinglimits2.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/optimalbookinglimits3.png){width=800  height=auto}
![demand function](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/optimalbookinglimits4.png){width=800  height=auto}
**Littlewood's Rule: The probability that class 1 demand will be higher than the protection limit of booking class 1 should match the ratio of prices (r2/r1)**

## Expected Marginal Seat Revenue and overbooking

### Booking limits for more than 2 classes
Assumptions:
- K Booking Classes
- Maximal Capacity C given
- Classes are determined so that r1 > r2 applies > ... > rK
- Demand is met according to the sequential order of the booking classes
- Nested protection limits
- At each level, a two-class problem is solved

The solution is to use heuristics:
- **EMSR-a** Expected marginal seat revenue version a, uses aggregated protection limits

![EMSR-a](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/emsra.png){width=800  height=auto}

- **EMSR-b** Expected marginal seat revenue version b, uses aggregated demnad

![EMSR-b](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/emsrb.png){width=800  height=auto}

SUMMARY
- Both approaches are heuristics
- EMSR-a aggregates the protection limits while EMSR-b aggregates the demand
- Calculating the weighted average price is a critical assumption
- In practice, EMSR-b is more widespread
- Experimental studies show that neither method dominates the other

# Overbooking
From the capacity management strategies this topic touches the level capacity, where scarce or
expensive resources are maintained at a constant level, and the organisation must manage the consequential issues for customer satisfaction and operational service quality. 

## Example Lufthansa
Lufthansa has millions of no show passengers (8% of all bookings) this equals to tens of thounsands of empty flights per year. These are mostly busines travellers which book multiple flights.
Solutions are:
- Increase the cost of cancellations
- Automatic cancellations for redundant flights
- Flight reminders via SMS/e-mail
- Advanced payments
- Overbooking (most effective, sell more than avaiable seats because you accomodate for no shows)

### Implementation overbooking
- Prognosis of no shows based on current bookings and time to flight (up to 16 model adjustments)
- Exemplary prognosis features: 
	- General: weekday, departure time, season, events
	- Passenger related: nationality, age etc.
	
**Steps for handling overbooked flights**
- Compensations (upgrades for later flights, money) for voluntary reschedulings
- Terms and conditions for when more ppl show up than expected
	- Children and disabled passengers have priority
	- Premium customers are treated with priority
	- Forced rescheduling by check-in personnel 
	- Compensation payments defined by regulations
	- Only necessary for 11 out of 10,000 passengers
	
## Managing overbooking
Overbooking is especially important if the number of no-shows is high and the cancellation does not entail any costs.
 
Overbooking is applied to
	- Aircraft seats reserved prior to travel
	- Car rental, where the cars are reserved before the day of rental
	- Hotel rooms or concert tickets sold in advance 
Procedure if customers have to be rejected:
	- Hotels: alternative accommodation, compensation 
	- Car rental: Upgrade
	- Airlines: alternative flights
	- Advertising: alternative broadcasting times, discount
Minimize the number of no-shows 
	- require early payment
	- increase cancellation fees
	- increase rebooking fees
	
### Assumptions overbooking model
C Capacity limitation
B Booking limit 
r Price for one unit sold
p Penalties

Other assumptions:
- Each customer who appears pays r, despite potentially idle capacity 
- Number of no-shows is X
- Density function of no shows is h(x) and distribution function of no-shows is H(x)
- Density function of demand Y is f(y) and the distribution function F(y)

![overbooking model](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/overbooking.png){width=800  height=auto}

# Service Process Management

## Definition of process

A sequence of activties to create a performance, with a beginning and end and a goal
 
Example: 
Manufacture PC 

Beginning: Release of a production order

End: Packaging PC 

Goal: Conversion of a production order into a product that can be shipped 

### Process Types 
- **Control processes**: Management of the company and control/management of core processes
- **Coreprocesses**: Focused on external customers with a direct contribution to value creation
- **Support processes**: Targeted at internal customers (core processes) with no direct contribution to value creation
![overbooking model](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/processTypes.png){width=800  height=auto}

### Performance measures 

- capcity: order acceptance or production 
- time: lead Time, delivery period
- cost: staff, maerial, ..
- quality: waste, reliability
- flexibility: load flexibility, product flexibility

### conflicting objectives
example call center: difference between capacity and average latency can be optimized with process design
example central storage: difference between stock and service level can be optimized with process design

## Base for Process mining

Process mining bridges gap between process model analysis (simulation, verfication, optimization, gaming etc.) and data-oriented analysis (data-mining, machine learning, business intelligence).
Process mining can be performance oriented (question, problems and solutions) or compliance oriented (question, problems and solutions)

### Example Order to cash process
OtCP: top level business process for receiving and processing customer orders and revenue recognition.
- essential function in finance
- cycle happens after customer places an order until they pay
- requires an activity/event log with an order (OrderID), activity (step of process), timestamp (start time end time optional)
	- event/ case is a row in the relationship
	- eventlog is the whole table
	- trace a control flow of activities of the process: [<register_order, check_stock,ship_order,handle_payment> & <register_order, check_stock,cancel_order>, ...]
	
### Simplified Event log
- A simplified event log is a multiset of traces (i.e., the same trace can occur multiple times).
- A trace is the activity sequence of a case (i.e. we only look at the order of the activities of each case).	

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/Log.png){width=800  height=auto}

L = Log
L<sub>1</sub>= Log ID
<a,b,c,d>= activity with frequency as exponent
a = trace

**Exercise**
caseID: student name
activity: course name
timestamp: exam date
event: student taking exam on a course on a date

3 different actitvities: Business Information systems, BPM systems, Process Mining
9 cases

4 traces

[\<Business Information systems>, 
<Business Information systems, BPM systems, Process Mining><sup>2</sup>,
<Business Information systems, process Mining>]

## Process Footprint

### relations
- **direct succession** : x>y if for some case x is directly followed by y.
- **casuality**: x --> y if x > y and not y > x
- **parallel**: x||y if x > y and y > x
- **independent/ choice**: x # y if not x > y and not y > x

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/footprint.png){width=800  height=auto}


## Direct follow graphs
- do not show concurrency (Parallelität), activities can happen at the same time

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/dfg.png){width=800  height=auto}

### Exercise
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/exdfg.png){width=800  height=auto}


![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/sol.png){width=800  height=auto}

## Petri network a modeling syntax
- Can handle concurrency (not like DFG) but are not deterministic (multiple traffic lights example)
- It is a static network consisting of **places**, which represent possible states of a proces, and **transitions**, which represent the dynamics/ relationships between states.
- A place and transition are connected by a **directed edge**. A directed edge connect always just one place and transition or vice versa.
- Places can contain **token** which indicate the state of a process. Said tokens are generated and/or consumed by transitions.
- A transition is **enabled** when each input place contains a token.
- A transition can **fire**, when it consumes all tokens from the input places and generates a token for each output place.
	- firing is atomic production and consumption happen at the same time.
- A **marking** is the distributions of token across the places in the petri net.
- The **initial marking** is the state before transitions fire. Starting point before the petri net becomess active.
- **Reachable marking**: Marking that is reachable through firing after the initial marking.
The **final marking** are the distrinuted token after all transitions have fired. There can be no, one or multiple final markings.

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/markings.png){width=800  height=auto}

### multiple transitions
We assume that enabled transitions do not fire synchronoulsly
reachable states = number of  possible tokens in one place <sup>number of transitions</sup> = multiply each reacheable states per places

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/finalmarking.png){width=800  height=auto}
- t1 fires 3 times
- t2 fires 3 times
- t1 fires 2 times t2 fires 1 time
- t1 fires 1 time  t2 fires 2 times

# Application areas for process mining

relating process models and event logs
1. Play In: Use data to produce process models, process discovery, learning process models from observed behaviour.
2. Play out: use models to produce data (simulation, workflow, management games, model checking)
3. Replay: Aligning modeled and discovered behaviour with observed behaviour (conformance checking, prediction, bottleneck analysis). In other words the confrontation between model and reality (used for diagnostics, predictions and recommendations)

## Process Discovery with Alpha Algorithm
Assumption the eventlog contains all possible traces of the model (petrinet) and vice versa.
We have different pattern that emerge through the simplified event log:
- sequence: a->b
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/sequence.png){width=800  height=auto}

- XOR-split pattern: a->b, a->c and b#c
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/xor.png){width=800  height=auto}

- XOR-join pattern: b->d, c->d and b#c
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/xor2.png){width=800  height=auto}

- AND-split pattern a->b, a->c and b||c
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/and.png){width=800  height=auto}

- AND-split pattern b->d, c->d and b||c
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/and2.png){width=800  height=auto}

## Alpa Algorithm
The algo is relativly simple and has the ability to discover:
- loops
- parallel parts
- choices 

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/alphaalg.png){width=800  height=auto}

1. collect all activities from eventlog, They will represent transitions in the petrinet.

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s1.png){width=800  height=auto}

2. collect the set of start activities

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s2.png){width=800  height=auto}

3. collect the set of end actitvities

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s3.png){width=800  height=auto}

Goals from step 4-6 are to find the places between transitions A and B by finding the set A of upstream transitions of a place p(A, B) (token producing) and the set B of downstream transitions (token consuming)of a place p(A, B)

4. Calculate pairs such that:
	- every element of a and b are casually related (->)
	- all elements of A are independent a1#a2
	- all elements in B are independent b1#b2
	1. Form pairs with sets of 1 activity for all casualties and only include activity if it is independent from itself. ({a},{b}), ({a},{e}), ..
	2. Find pairs in which, either first or second set are equal and the other activities (unequal sets) are independent. Then merge these pairs ({a},{b, e}), ...
	3. Merge the pairs with one activity and the merged set pairs {({a},{b}), ..., ({a},{b, e}), ...}
	
	
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s4.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s42.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s43.png){width=800  height=auto}

5. delete from X<sub>L</sub> all non-maximal pairs

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s5.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s52.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s53.png){width=800  height=auto}

				...

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s54.png){width=800  height=auto}

6. determine places p<sub>(A,B)</sub> from pairs (A.B) and add a source and target place

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s6.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s62.png){width=800  height=auto}

7. Connect each place with each element f its set A of upstreamtransitions and with each element of its set B of downstream transitions. Connect the source place to all start transitions and connect all end transitions to the target/sink place.

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s72.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s7.png){width=800  height=auto}

8. Build the etrinet from Y<sub>L<sub>1</sub></sub>
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/s8.png){width=800  height=auto}
## Limitations of the algo

- **Implicit places** 
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/lim1.png){width=800  height=auto}
- **Loops of length 1 or 2**
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/lim2.png){width=800  height=auto}
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/lim3.png){width=800  height=auto}
- **Non local dependencies**
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/lim4.png){width=800  height=auto}
- **Representational bias**
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/lim6.png){width=800  height=auto}
- **deadlocks**
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/lim5.png){width=800  height=auto}

## Process mining
Wil van der Aalst: Process Mining, Data Science in Action
lars reinkemeyer process mining in action, Principles, use cases and outlook
use cases in companies:

## Play out and reachability graph

the play out strategy is user to obtain data from a predefined model (simulation, management games, model checking, workflow automation)

A **reachability graph** is a directed graph that can be obtained from a petri net and an initial marking.
All the markings are determined in a stepwise manners.
The reachability graph is obtained, where the markings(tokens) are represented by nodes and the transitions between a marking and its next marking is represented by a directed edge, annotated with the respective transition.
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/d1.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/d2.png){width=800  height=auto}

--> we can follow the edges and see the possible traces, 

**example traffic lights**

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/d3.png){width=800  height=auto}

**multiple arcs** between place and transition

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/d4.png){width=800  height=auto}

**non finite reachability**

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/d5.png)

## Advances petri net modeling
- Model a circular railway system with four stations (st1, st2, st3, and st4) and one train.
- At each station passengers may "hop on" or "hop off". This is impossible if the train is moving.
- The train has a capacity of 50 persons; if the train is full, no new passengers may hop on.
- Model the above process in terms of a Petri net.

### Petri net of the state of the train

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/d6.png){width=800  height=auto}

### Petri net of the state of the passengers

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/d7.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/d8.png){width=800  height=auto}

The capacity is 50, so the number of occupied seats can be 0,1,…,50 → 51 possibilities.

## Conformance and checking

## Evaluate conformance between traces and process models
**Replay**
Conformance happens through alignment of modeled and observed behaviour. Most important form of process minning.

**Case example**: Optimizing painting process at BMW
- detect irregularities in the paint process in almost real time, analyze their cause and react to them
- downtimes in production and the associated additional costs can be avoided
- compare the “As Is” process with the originally planned process
- identify unplanned deviations as well as requirements to modify production steps. 
- bottlenecks can be identified quickly
- see which process changes really make sense, e.g., if a parallel queue of certain production steps can help to reduce throughput times
--> are there processes that can be parallalized?

## How to evaluate

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r1.png){width=800  height=auto}

Take the trace that happens most. Alone it lacks of fitness because it just represents one trace of them all.

**Fitness**: ability to play through the traces of a model
- perfect fitness if all traces in the log can be replayed by the model from beginning to end.
− Case level: fraction of traces in 
the log that can be fully 
replayed
− Event level: fraction of events in 
the log that are indeed possible 
according to the model

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r2.png){width=800  height=auto}

Next step could be model all the traces. This lacks simplicity as it is overly complex and messy.

**Simplicity**: 
− The simplest model that can explain the behavior seen in the log, is the best model.
− Complexity of the model could be defined by the number of nodes and arcs

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r3.png){width=800  height=auto}

As a next step we could implement the traces as a flower model. This model lacks precision as it is underfitting because we could obtain traces that are not part of the original to be modeled traces. Flower model is too general.

**Precision**:
− A model is precise if it does not allow for “too much” behavior
(“underfitting”).
− fraction of traces in the log to all traces that can be played out from the process model

--> A high quaality model is defined through fitness, simplicity and precision.
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r5.png){width=800  height=auto}




## Use of log and model footprint to measure conformance
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r6.png){width=800  height=auto}
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r4.png){width=800  height=auto}
footprint-based conformance = 1 – (number of differences) / (number of cells in footprint) = 1 – 0/25 = 1 
(1 = perfect match) (0 = worst match possible)
!(pic footprint conformance)

--> **Limitations** of footprint based conformance:
- Frequencies are not used
- Behaviour is only considered indirectly through directly follow relation
- It aims to capture fitness and precision in a single metric

- If there are  traces in the eventlog which are not in the petrinet or vice versa we fill these missing traces with independence relationsships in the corresponding footprint

## Measure trace-level fitness with token based replay
Replay a trace on a model/ petri net

Produce a missing token when we encounter the situation that we otherwise cannot replay a trace because a transition is not enabled. (Track missing and remaining tokens)



![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r7.png){width=800  height=auto}
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r8.png){width=800  height=auto}
--> p and c always at least one since we cannot divide by zero


We can apply this formula on a higher level of the log level. We measure over all traces and sum up. We now consider the frequency of the traces. We measure the proportion of the events that can be replayed correctly.


![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r9.png){width=800  height=auto}
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/r10.png){width=800  height=auto}

**Limitations** of token based replay fitness (problem of token flooding)
- Conformance values sometimes too optimistic due to "token flooding“:
- When the case differs much from the model, a lot of missing tokens are inserted during the replay. 
- As a result of all the added tokens, many transitions become enabled.
- Therefore, also deviating events are likely to match an enabled transition. 
- This leads to misleading diagnostics because unwanted parts of the model may be activated.
- So the fitness value for highly problematic executions may be too high.

**Limitation** of visible/uniquely labeled transitions. If a petrii net contains transitions with the same level, we do not have a definite way to replay and this approach to calculate conformance collapses.


# Organizational Mining

Enhancing Process Models with organizational level data.

Example Compensation request process

Step one Identify roles from data and create resource activity **matrix**
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o1.png){width=800  height=auto}
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o2.png){width=800  height=auto}
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o3.png){width=800  height=auto}

Step 2 Divide absolute frequencies by number of cases (number of rows in event log) to obtain the average number of times a resource performs a case
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o4.png){width=800  height=auto}

--> provides basic insights into who is doing what.

## Construct a social network
- Sociometry: present data on interpersonal relationships in graph or matrix form.
- Arcs: weights or (inverted) distance.
- Metrics to denote importance: 
	− centrality,
	− closeness,
	− betweenness. 
	− …
- Identification of cliques.
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o5.png){width=800  height=auto}

## Calculate vector distances
We want to figure out which worker of the example before are similar?
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o6.png){width=800  height=auto}

For similarity we can invert the obtained distance value.

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o7.png){width=800  height=auto}
- Similarity is the inverse (“Kehrwert”) of distance.
- Resources that execute similar collections of activities are related.
- Self-similarity is ignored.
- 

Social network based on similarity of profiles

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o8.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o9.png){width=800  height=auto}

## How to indentify teams of resources (clusering)
Teams can be also obtained through clustering (kMeans, agglomerative hierarchical clustering)

Step one: Create resource case matrix 
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o10.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o11.png){width=800  height=auto}

Step 2-4 Binarization, Calculate euclidean distances and inver values

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o12.png){width=800  height=auto}

From the similaritiy measure (only th ehigh ones) we can form a resource network

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/o14.png){width=800  height=auto}

# Organizational mining to detect botttlenecks
The following topic is used to identify bottlenecks in respurce matrices or petri nets.

## Handover matrix

If we have a footprint we can use  the casual dependencies > (not -> = direct successor) to identify the handovers.

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b1.png){width=800  height=auto}

If we identified the handovers we can use the formula to calculate the cell values of the handover matrix.

![](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b2_1.png){width=800  height=auto}
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b2.png){width=800  height=auto}

--> Alan |>_L Sara = (1+1)/4 = 1/2

We can build the handover matrix and the resulting network.

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b3.png){width=800  height=auto}

## Degree centrality of a node in a network

As a next step we calculate  how central a node is in a network. The formula calculates the sum over the input weights and the output weights.

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b4.png){width=800  height=auto}

## Betweenness centrality of a node in a newtwork

The betweeness reprsents the assumption that important nodes should connect the other nodes. in other words: it is the fraction of shortest paths between any two nodes passing a particular node

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b5.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b6.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b7.png){width=800  height=auto}

We can obtain the betweenness centrality of resources with the handover matrix.

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b8.png){width=800  height=auto}

# Decision point mining
The decision spot mining can be seen as a XOR-split in a network, where we have a number of cases which go one wax at an XOR-split and a number of cases which go the other way. 
Example accept/reject claim. This can be seen as a classification problem. Maybe there are certain pattern of traces which will have a claim always rejected and other traces where claims can be accepted.

In order to do a decision point mining we assume that the event log and process model have been aligned. So every trace of the log is represented in the model.

One way is to have decision guards at the XOR-split which check for an attribute in the trace in order to decide which way to go

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b9.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b10.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b11.png){width=800  height=auto}

## Decision point mining as a classification problem

We will use the Gini impurity to build the decision tree.

**Definition**: Gini impurity is a way for a decision tree to measure how “mixed” the class labels are in a node. The probability that you would misclassify a randomly chosen sample from the node if you guessed the class at random according to the class distribution in that node.
More concretely:
1. Pick a random sample from the node.

2. “Predict” its class by randomly drawing a class label according to the node’s class proportions.

3. Gini impurity is the probability that this prediction is wrong.

So:
- Lower Gini impurity → node is “purer” (mostly one class).
- Higher Gini impurity → node is “mixed” (many classes with similar proportions).

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b12.png){width=800  height=auto}

5. How decision trees use Gini impurity

In a classification tree (like CART), at each node the algorithm:

1. Considers possible splits (e.g., “feature X ≤ 3.5?”).
2. For each split, it computes the weighted average Gini impurity of the child nodes

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b13.png){width=800  height=auto}
3. Chooses the split that reduces Gini impurity the most (i.e., maximizes impurity decrease).

So Gini impurity is the criterion the tree uses to decide where to split so that nodes become purer and purer.
![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b14.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b15.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/b16.png){width=800  height=auto}


# Customer Lifetime Value

### Definition
- total financial contribution from the current period into the future of a customer over his/her future lifetime with the company – that is, revenues minus costs  
− reflects the future profitability of the customer
− present value of the cumulative cash flows of a customer 
− Comparable to net present value of machines

### Objective
− helps a firm to know how much it can invest in retaining the customer as to achieve a positive return on investment
− focus investments on customers that bring the maximum profit
− deciding on customer-specific communication strategies

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv1.png){width=800  height=auto}

Definition Contribution Margin: The rest of the revenue that remains after paying all the variable const of the revenue. Can be used to pay it towards fix costs
During the customer aquisition the revenue is quite low, therefore the contrivution margin is negative because the variable costs to aquire the customer are higher than the revenue. When the trust with the customer is built ans the customer is retained,the customer will spend more resulting in high revenue and higher/positive contribution margin. If the customer leaves (better offers somewhere else) the company has to spend money to recover the customer therefore revenue and contribution margin sink again.

##  Measure CLV

**simple/basic approach**

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv2.png){width=800  height=auto}

**with retention rate**

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv3.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv4.png){width=800  height=auto}

**with fix aquisition costs**

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv5.png){width=800  height=auto}

Example:
Consider a CLV model with the following variables. What is the acquisition cost threshold, from which on a customer relationship becomes unprofitable?
• Fixed revenues per period: CHF 5
• Fixed cost per period: CHF 3
• Customer retention rate: 0.65 
• Interest rate per period: 0.05

m = 5 - 3 = 2

m * r / (1+i-r) = 2 * 0.65 / (1 + 0.05 - 0.65) = 3.25

## Customer equity

The sum of customer life time values of all customers

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv6.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv7.png){width=800  height=auto}

C * (m * r / (1+i-r) - AC) =5000 * (2 * 0.65 / (1 + 0.05 - 0.65) - 1) = 11250

## Critic of the CLV model from above
Fixed retention rates is not realisitc as it is very subjective to different customer groups or business settings because:
1. Recency effect (intuition here: the more recent the last 
transaction, the higher the transaction probability/retention 
rate)
2. Frequency effect (intuition here: budgetary constrains and 
worn out novelty effect reduce transaction probability/retention 
rate)
3. Customers are not „lost for good“ but might come  back at later 
periods

## Purchase Probability

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv8.png){width=800  height=auto}

## CLV with receny and frequency

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv9.png){width=800  height=auto}

## Loyality effect on churn

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv10.png){width=800  height=auto}

# Markov chain

- A Markov chain is a stochastic process. (e.g. purchase, customer retention)
- The aim is to give probabilities for future events to occur.
- A Markov chain is defined by the fact that knowledge of only a limited prehistory (in this case: only the current state of the system) makes it possible to predict future development. 
- The entire prehistory of the process is not relevant for prediction.
- Modeling with discrete time (e.g. months or years)
- Modeling with finite state set (e.g. customer status as potential, active or lost customer)

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv11.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv12.png){width=800  height=auto}
p_a = aquisition probability
p = retention probability

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv13.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv14.png){width=800  height=auto}

![log](file:///C:/Users/lilli/Documents/Zhaw/25HS/DataServicesProducts/Images/clv15.png){width=800  height=auto}