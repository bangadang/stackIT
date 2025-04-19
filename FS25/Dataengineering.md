# Dataengineering 

## Lessons Learned
|Date| Sumamary |
|--|--|
| 20.02.25 | Data engineering is an essential step in order to train models (Big Data) |
| |5V of Big Data (Volume, Velocity, Variety, Veracity, Value)  |
| |Challenges (heterogenity, inconsistency/-completeness/ scaleability, timeliness, data ownership) |
| |intro to pandas |
| 27.02.25 | reasons for data quality issues : a lot of different data sources, data can be falsely measured, extracted or entered etc., variety of formats (export errors) |
|  | to avoid issues: domain knowledge, clean data |
|  | RegEx Intro: match, extract, find, replace with patterns |
|06.03.25  | Reminder Relations and comparison to nested datastructres like json |
|  | Data Processing |
|  | Record Linkage: Ausgangslage: Wie findet man Duplikate in einem oder verschiedenen Datasets ohne key?[andere common names:fuzzy match, entitty resolution, entitity clustering usw.] --> create join condition which is not too specific, too inclusive but matches approximating |
|  | levensthein distance: the minimum number of character edit operations needed to turn one string into the other. 
||- copy character from s to t (cost = 0) - delete a character from s (cost = 1) 
||- insert a character into t (cost = 1) 
||- substitute one character for another (cost = 1)|
| 13.03.25 | **advantages of storing data in relational systems**: |
|  | interfaces are well defined, data is well organized and structured |
|  | schema provide meta-data |
|  | synchronized multi-user support |
|  | query processing engines do efficient preprocessing and deliver data as wanted/needed |
|  | **disadvantages**: |
|  | only scales to mediuim sized datasets |
|  | limited functions for analytics |
|  | problems occur for semi-/unstructured data |
|  | **data warehousing** |
|  | Definition: a data warehouse is a collection of data in support of management’s decision-making process |
|  | stores **subject-oriented** information rather than processes (subjects like product, customer, sales etc.) |
|  | **integrates** data from heterogenous sources |
|  | **time-variant**: stored data is associatted with a time period, provides information from the historical point of view |
|  | **non-volatile**: a data warehouse is kept separate from the operational database and new added data does not erase old data |
|  | data warehouses support business executives to organize, analyze, and use their data for decision making |
|  | data warehouses are commonly used in: financial/ banking services, consumer goods, retail sector, controlled manufacturing |
|  | types of data warehouses: |
|  | **information processing**: DW allow to process data stored within by means of querying, simple statistical analysis, table, charts, graphs |
|  | **analytical processing**: data can be processedd by means of basic OLAP operations including slice-and-dice, drill down/up, pivoting |
|  | **data mining**: knowledge discovery by finding patterns and associations, performing classification and prediction through construced analytical models |
|  | Differences between operational DB and DW |
|  | DW architecture |
|  | Data Marts |
|  | ETL from source to staging area |
| 20.03.25 |  |
|  |  |
|  |  |
|  |  |
|  |  |

### Operational Database vs Data Warehouse
|OLTP| OLAP |
|--|--|
| day2day processing | historical processing |
| used to run a business | usedETL to analyze a business |
| focus on data in | focus on information out |
| based on Entity Relationship Model | based on Star Schema or Snowflake Schema |
| provides, primitive/ highly detailed/ flat relational view of data | provides summarized/ consolidated/ multidimensional view of data  |
| thousand of active users on the system | hundreds of users on the system |
| database size: 100MB-100GB | database size: 100GB-100TB |

### Data Warehouse Architecture
| Input:Data Sources | **Staging** | **Integration** | **Enrichment** | **Analysis** | Analysis | Analysis | Analysis|
|--|--|--|--|--|--|--|--| --|--|--|
|  | *Staging Area* | *Data Universe* | *Data Universe* | *Data Marts* | *Analysis Services* | *Presentation* | *Front End* |
|  | Structure the data in some form like a file, a database, XML or thelike |  | Applications: Aggregation, Calculations, Event detection, Reusable Entities | Selection, Aggregation, Calculation | Reporting OLAP Mining | Web/App Servers | GUI|
| product data from different origins, like Singapore, New York and Zürich  | Each source is being structured in the same format like a relation/ database | integrate separate relations into a new dimension combining thee different sources |  |  |


### Data Marts
- is a data model, which is optimised for fast and efficient queries
- does domain specific operations
- presents views of the whole data warehouse
- provides interfaces for analyzing and data mining tasks

## ETL (extract, transform, load)
most time consuming part od data warehousing, as there is no standard method or system but an abundance of different tools
 it it time intense because:
 - different data sources with heterogeneity
 - imense data volume
 - the integration is complex, because of data cleaning and creating a schema and instance integration
 - There are two types of ETL
	 - **batch processing**: data is processed in batches o defines size or time values and requires space for buffering
	 - **real time processing**: data is processeed item by item continuously. Every item can only be seen once.
 
 ### extract
 -  data is collected from one or several sources and held in temporary storage
 - validation test are run on the data to ensure it conforms with its destinations requirements
 - its a task done regularly in order to supply updated data to da data warehouse
 - the data extracted is differentiable through a time setting and defined type of extracted data
	 - **time setting**:
		 - synchronous notification:
			 - upon an update occurence at source the ddata extracton is triggered
		 - asynchronous notification:
			 - periodic: the sources generates an extraction on a regular basis or the DW extracts the updated data on a regular basis
			 - event-driven: the DW extracts the updates at the end of a year or the sources notifies upon each X updates
			 - query-driven: DW checks for new updates before accessing the data
		 - **type of data**:
			 - snapshots: the source delivers the complete dataset each time, like new pricing list or product catalog
				 - requires an update detection and capturing of the update history
			 - logs: the ource logs each update operation on the data through transaction/appplication-driven logging
				 - requires efficient update execution
			 - netlogs: the source delivers net updates though catalog updates, snapshot deltas
				 - source cannot offer a complete history but updating can be done efficiently
### transform
- the data is then processed. So its structures and values conform with its intended use case
	- problem:
		- data is not in the target format of the DW or structured differently. Either the schema is close to thee source or the DW has a multidimensional schema --> data and schema heterogeneity
		- aspects of the transformation: data and schema has to be transformed
	- **heterogeinity**:
		- primary (OLTP systems) and secondary sources provide either un-/semistructured data
		- various data models which require mapping
		- same reality is modeled differently (design autonomy, subjective modeling perspectives)
### load 
- moves the transformed data into a permanent target database efficiently
	- critical point:
		- load routines can block the entire DB
		- active triggers have to be managed
		- integrity constraints have to be upheld
		- Indicies have to be maintained
		- update and inseration operations 
	- **record basedd laoding**:
		- uses standard interfaces
		- triggers, indices ad constraints can remain active all the time
		- no longlasting locks
	- **bulk loading**: standard of irl practice
		- reuires DB specific extensions for loading large volumes
		- runs in special context and loads complete tables or DB blocks
		- ignores triggers and contraints
		- indices are updated upon completion
		- requires checkpoints for resuming

### profiling
- a task within the ETL process which analyzes:
	-  the content and structure of single attributes
		- data ytpe, value, range, distribution/varinances, if attribute has NULL values, pattern occurences (date patterns)
	- dependencies between attributes (of a relation):
		- unsharp keys: a potential or candidate key in a dataset that **almost uniquely identifies** records — but **not perfectly**. It looks like a key, acts like a key in most cases, but breaks the rule in some edge cases.
			- For example First + Lastname (breaks in case there are two people with the same name)
		- unsharp dependiencies:  (or **approximate functional dependencies**) are relationships between columns that hold **most of the time**, but not always.
			- For example a column with zip codes and one with city names. Eventhough often a case a zip code doesn't always represent a specific city. Like Zurich there are different zip codes representig different districts.
	- functional dependencies: One attribute (or a set of attributes) uniquely determines another attribute.
	- primary key candidates
	- necessity: 
		-    **Measure how trustworthy a dependency is** : High necessity = good candidate for a business rule or constraint
    
		-   **Detect anomalies or data quality issues**: Low necessity might mean dirty or inconsistent data
    
		-   **Help build schema or transformations** :  You might use a dependency with high necessity to deduplicate, normalize, or infer missing values
	- overlap bewtween attributes of different relations, in order to determine redundancies and possible foreign keys
- the process of profiling can be used to find:
	-  missing or invalid values
	- actual vs expected cardinality (like number of stores, customers genders)
	- number of nulls as well as keyfigures like min/max, variance etc.
	- if a data or input error occured through sorting/ similarity tests or manual checking
	- deduplicate the data/ attributes

### data cleansing
- part of the ETL process, which recgonizes and eliminiates inconsistencies, contradictions and errors in the data in order to improve quality
- takes up about 80% of the total workload in data warehouse projects
- standardization and normalization of the data
	- setting datepatterns, unify currencies, normalize and tokenize text
- deals with missing values on instance level (values, records sub-relations) dealing with NULL values and schemalevel with missing attributes. 
	- causes distortion and noise (bias) even error in calculations
	- find the missing values by:
		- analysis and comparison with expected values, 
		- check if the values are in an expected range
		- truncate values wih certain if/else conditions
	- handle the missing values:
		- estimate a missing value by choosing sth which does not change the average and standard deviation
		- through attribute dependencies/relationships
		- statistical techniques (linear regression, neural networks )
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkxNTA1ODU4MSwtMjYyMzU2ODI0LDcwND
g4NTg0NiwxNDg4NTA3Nzg5LC0xMDg1NDQ3MTU3LC0xMTc3NzIw
OTY2LDIyMjg4NDA1OSw3MTk1MzYxMTgsMzI2ODY0NTg4LDE5MD
g3MzE4ODEsMjEzMzk1NDUyMCwyOTgyMzEwODQsNzA5ODM3ODld
fQ==
-->