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
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |

### Operational Database vs Data Warehouse
|OLTP| OLAP |
|--|--|
| day2day processing | historical processing |
| used to run a business | used to analyze a business |
| focus on data in | focus on information out |
| based on Entity Relationship Model | based on Star Schema or Snowflake Schema |
| provides, primitive/ highly detailed/ flat relational view of data | provides summarized/ consolidated/ multidimensional view of data  |
| thousand of active users on the system | hundreds of users on the system |
| database size: 100MB-100GB | database size: 100GB-100TB |

### Data Warehouse Architecture
| Input:Data Sources | **Staging** | **Integration** | **Enrichment** | **Analysis** | 
|--|--|--|--|--|--|--|--|
|  | *Staging Area* | *Data Universe* | *Data Universe* | *Data Marts* | *Analysis Services* | *Presentation* | *Front End* |
|  | Structure the data in some form like a file, a database, XML or thelike |  | Applications: Aggregation, Calculations, Event detection, Reus |  |  |  |
| Meta | data | man | age | ment |




<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE0NjM5OTIzNiw3MTk1MzYxMTgsMzI2OD
Y0NTg4LDE5MDg3MzE4ODEsMjEzMzk1NDUyMCwyOTgyMzEwODQs
NzA5ODM3ODldfQ==
-->