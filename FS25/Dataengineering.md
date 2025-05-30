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
 - a variation of ETL ist ELT where the data transformatoin is done withing the warehouse, after loading. the goal is to to do the transformation using sql statements
 
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

## Data Warehouse modelling
- A data model is designed with the needs of the analysis in mind. Since the goal is to gain some knowledge for future (business) decisions through:
	- performance indicators
	- measurments of different perspectives/ dimensions
	- structures
- the design is also based upon the available information
	- qualitative data which is used as navigation structure
	- quantitative data which represent the subject of the analysis
 ### dimensions
 needs to be finished (lecture 5)
# Unstructured Data
### information retrival
is the activity of obtaining information resources relevant for an user's information need from a collection of information resources.
the information retrival process includes:
- information needs (queries)
- (mostly unstructured) information resources 
- a system to identify relevant (re)sources for a given information need (query)

### information need
Information need is a desire to locate and obtain information to satisfy a conscious or unconscious need. Information needs (conscious or unconscious) are expressed as queries
Such queries are usually words/phrases retireving text information. --> Text information retrival
Most info resources are text based unstructured and big in scale 

### Text representation in info retrieval

- **unstructured representation**
	- text erpresented as bag of words (unordered set of words)
	- syntax, semantics, pragmatics of text are ignored
		- A query like "Revenue of apple" could retrieve a result like  "Apple pencil did xy." and "Microsofts revenue .."
	- Is fast and simple and still yields fairly good results and is the standard of IR represenATION
- **weakly structured representation**
	- certain groups of terms receive a weight/ importance, like nouns or named entities and other terms are downgraded or simply ignored like stopwords
	- uses part of speech tagging or named entity recognition 
	- is more costly as it uses additional preprocessing of the information resurce
- **structured representation** 
	- information resource represented as graphs, terms as nodes and semantic relation as branches
	- very costly and virtually not used in IR

### Text preprocessing for unstructured text representations
- text is represented as unoredred set of terms (BoW) and has to be preprocessed:
 1. extracting pure textual content (e.g., from HTML, PDF, Word) 
2. language detection , Optional – if you’re dealing with multilingual document collections
3.  tokenization (separating text into character sequences) 
4. morphological normalization (lemmatization or stemming)
5. stopword removal
- after preprocessing the text/document is ready to be indexed

### Tokenization
- A token is an instance of a word or term in a text/ document (numbers, punctuation and special chars are also tokens)
- tokenization is the process of breaking down a text into tokens through a rule based heuristic approach or a ML model approach
- process is ambiguous and not always clear how to split a string, as possible information loss can occur. 
	- Should you split a birthdate/ phonenumber/ multiword words etc.
	- different languages have different rules of tokenization
### Normalization (of tokens)
- Error/Spelling correction
- making all letters lower case (case folding)
- word disambiguation
- morpholocigal normalization by reducing different forms of the same word into a common representative form 
	- inflectional normalization (houses to house, tried to try,)
	- derivational normalization (destruction to destroy) most IR system do not erform derivational norm.

### Stemming 
- stemming is the procedure of reducing the word to its grammatical (morphosyntactic) root („recognized” -> „recogniz”, „incredibly” -> „incredibl”) by removing prefixes and suffixes
	- most common algorithm for stemming is **Porter's algorithm** which consists of different rules to reduce a word

### Expansion  of the query
- use alternate form of the query words
	- query: window search: window, Windows, windows 

### Stopword removal 
- removal of semantically poor terms such as articles, 
prepositions, conjunctions, pronouns etc.
- stopwords add nothing to the relevancy/meaning of a document
- the removal reduces the size of the vocabulary

### general IR model
1. representation of a raw **query** text to be used for matching against documents in the collection 
2. representation of a raw **document** text to be used for matching against the query. May be the same representation as the one used for query 
3. a function for determining the relevance of documents for the query taking as input document and query representations from (1) and (2)

formally a generalretrival model is a triple of functions
1. $f_d$ is a function that maps documents (raw text) to their representation for retrieval, i.e., $f_d(d) = p_d$ , where $p_d$ is the retrieval representation of the document d
2. $f_q$ is a function that maps queries (raw text) to their representation for retrieval, i.e., $f_q(q) = s_q$ , where $s_q$ is the retrieval representation of the document q
!depending on the IR model, $f_d$ and $f_q$ may be the same function 
3. $r$ is a ranking function which computes a real number indicating the potential relevance of document $d$ for query $q$, using representations $p_d$ and $s_q$: $rel(d,q) = r(f_d(d), f_q(q)) = r(p_d , s_q )$

### Index terms and index weights
- index terms are all unique terms in the vocabulary
- each term $k_i$ for each document $d_j$ is assigned a weight $w_{ij}$ if a term doesn't appear in a document the weight is 0
- a document $d_j$ ist represented by a term vector of the weights

### Boolean retrieval
- queries are boolean expression like “aliens” AND “swords” AND NOT “wizards” 
- search engine returns all documents from the collection that satisfy the Boolean expression


# Webcrawling
### Crawling for Search Engines
The web is crawled to find new links, which are then analyzed and added to the database. The database can be accessed by a user when searching in a search engine.
An algorithm is used to rank the pages stored in the database according to different factors to determine their importance by a seaarch query. In order to present the pages which the user was most likely searrching for
Google, Bing, Duckduckgo are common search engines which crawl for indexing pages and links to further webpages. 

### Creating a search index
- Obtain URL/ Sitemaps
- crawl by following connecting links
- process the contents of the pages (not a public process and unique to each search engine)
- index the processed information / add them to the search engine

### Process of a search algorithm
- pages are ranked through relevance, backlinks, freshness, metatags/keywords
- pages are connected to a location, language
- search history can also play a role

### Crawling with Scrapy
Scrapy is an open source tool for webcrawling which allows customization
Workflow:
The data flow in Scrapy is controlled by the execution engine, and goes like this:

1.  The  [Engine](https://docs.scrapy.org/en/latest/topics/architecture.html#component-engine)  gets the initial Requests to crawl from the  [Spider](https://docs.scrapy.org/en/latest/topics/architecture.html#component-spiders).
    
2.  The  [Engine](https://docs.scrapy.org/en/latest/topics/architecture.html#component-engine)  schedules the Requests in the  [Scheduler](https://docs.scrapy.org/en/latest/topics/architecture.html#component-scheduler)  and asks for the next Requests to crawl.
    
3.  The  [Scheduler](https://docs.scrapy.org/en/latest/topics/architecture.html#component-scheduler)  returns the next Requests to the  [Engine](https://docs.scrapy.org/en/latest/topics/architecture.html#component-engine).
    
4.  The  [Engine](https://docs.scrapy.org/en/latest/topics/architecture.html#component-engine)  sends the Requests to the  [Downloader](https://docs.scrapy.org/en/latest/topics/architecture.html#component-downloader), passing through the  [Downloader Middlewares](https://docs.scrapy.org/en/latest/topics/architecture.html#component-downloader-middleware) 
    
5.  Once the page finishes downloading the  [Downloader](https://docs.scrapy.org/en/latest/topics/architecture.html#component-downloader)  generates a Response (with that page) and sends it to the Engine, passing through the  [Downloader Middlewares](https://docs.scrapy.org/en/latest/topics/architecture.html#component-downloader-middleware) 
    
6.  The  [Engine](https://docs.scrapy.org/en/latest/topics/architecture.html#component-engine)  receives the Response from the  [Downloader](https://docs.scrapy.org/en/latest/topics/architecture.html#component-downloader)  and sends it to the  [Spider](https://docs.scrapy.org/en/latest/topics/architecture.html#component-spiders)  for processing, passing through the  [Spider Middleware](https://docs.scrapy.org/en/latest/topics/architecture.html#component-spider-middleware) 
    
7.  The  [Spider](https://docs.scrapy.org/en/latest/topics/architecture.html#component-spiders)  processes the Response and returns scraped items and new Requests (to follow) to the  [Engine](https://docs.scrapy.org/en/latest/topics/architecture.html#component-engine), passing through the  [Spider Middleware](https://docs.scrapy.org/en/latest/topics/architecture.html#component-spider-middleware) 
    
8.  The  [Engine](https://docs.scrapy.org/en/latest/topics/architecture.html#component-engine)  sends processed items to  [Item Pipelines](https://docs.scrapy.org/en/latest/topics/architecture.html#component-pipelines), then send processed Requests to the  [Scheduler](https://docs.scrapy.org/en/latest/topics/architecture.html#component-scheduler)  and asks for possible next Requests to crawl.
    
9.  The process repeats (from step 3) until there are no more requests from the  [Scheduler](https://docs.scrapy.org/en/latest/topics/architecture.html#component-scheduler).

### Scrapy Engine[¶](https://docs.scrapy.org/en/latest/topics/architecture.html#scrapy-engine "Permalink to this heading")

The engine is responsible for controlling the data flow between all components of the system, and triggering events when certain actions occur. See the  [Data Flow](https://docs.scrapy.org/en/latest/topics/architecture.html#data-flow)  section above for more details.

### Scheduler[¶](https://docs.scrapy.org/en/latest/topics/architecture.html#scheduler "Permalink to this heading")

The  [scheduler](https://docs.scrapy.org/en/latest/topics/scheduler.html#topics-scheduler)  receives requests from the engine and enqueues them for feeding them later (also to the engine) when the engine requests them.

### Downloader[¶](https://docs.scrapy.org/en/latest/topics/architecture.html#downloader "Permalink to this heading")

The Downloader is responsible for fetching web pages and feeding them to the engine which, in turn, feeds them to the spiders.

### Spiders[¶](https://docs.scrapy.org/en/latest/topics/architecture.html#spiders "Permalink to this heading")

Spiders are custom classes written by Scrapy users to parse responses and extract  [items](https://docs.scrapy.org/en/latest/topics/items.html#topics-items)  from them or additional requests to follow. For more information see  [Spiders](https://docs.scrapy.org/en/latest/topics/spiders.html#topics-spiders).

### Item Pipeline[¶](https://docs.scrapy.org/en/latest/topics/architecture.html#item-pipeline "Permalink to this heading")

The Item Pipeline is responsible for processing the items once they have been extracted (or scraped) by the spiders. Typical tasks include cleansing, validation and persistence (like storing the item in a database). For more information see  [Item Pipeline](https://docs.scrapy.org/en/latest/topics/item-pipeline.html#topics-item-pipeline).

 # Big Data
Traditional databases do not scale for big data and adding faster or larger hardware does not suffice. Another probem is that most data is unstructured but databses store them structured. A new solution is to use NOSQL solutions, where horizontal scalability is possible as only limited relational database system operations are supported. Rather than storing the data in tables, data is stored as key value pairs.

Why should we a databse instead of files?
- files are only easy to access sequentially,
- there is no optimized access in files
- there is no consistency
- there is no efficient way to only access a subset of information in a file without reading everything first

advantages of databeses:
- well defined sql interfaces
- well organized and structured
- synchronization among many users

## the basic 4 V's + 2 V's
### 1. volume
- scale and dimension of data is enormous
- need of the ability to process large amounts of data at once
### 2. variety 
- data is in many forms of different complexity
- there is no fixed struture 
- data is not immediately ready to be processed
- no uniformity or monotony
- data can be highly, semi- or unstructured
### 3. velocity
- constantly new incoming data
### 4. veracity
- trustworthiness of data sources
- data consistency of sources
- results can be mostly only be considered as probable
### 5. visibility 
- importance of having a full picture of data in order to make 
informative decision
- clarity of data, so as to perform analytic operations on it
### 6. value
- having access to Big Data is irrelevant if no value can be derived from it

## Scalability
## Sharding
## Replication
## consistent hashing

# NoSQL
NoSQL systems (like Cassandra, MongoDB, Couchbase, DynamoDB) are often designed to:
- Run across many servers and locations
- Scale horizontally (add more machines easily)
- Handle massive amounts of data with low latency
- store data with key-value pairs rather than tables.
- to have low software costs
- achieve faster insight into the data after the data acquisition
- have an efficient use of distributed indexes and RAM for data storage
- have the ability to dynamically add new attributes to data records
- It's a flexible data model as it doesn't require the design of a schema first and there is no need for data cleansing/ ETL or loading.
- relaxed consistency models CAP (trade consistency for availability and eventual consistency)
## Consistency Models
### ACID
traditional relational database systems typically implement ACID transactions 
- **atomicity**: “all or nothing” 
- **consistency**: transactions never observe or result in inconsistent data 
- **isolation**: transactions are not aware of concurrent transactions 
- **durability**: once committed, the state of a transaction is permanent

### CAP
 **CAP theorem** states that in a distributed data system, you can only guarantee two of the following three properties at the same time:
	1.  **Consistency** – Every read receives the most recent write (like in traditional relational databases). Clients will see the same data at the same time. Achieved by data in a write to one node is isntantly forwarded or replicated across all other nodes
	2.  **Availability** – Every clients request gets a response even if it’s not the most recent data or the nodes are down. Achieved by replicating data across different servers.
	3.  **Partition Tolerance** – The system continues to function despite network partitions (partition:=communication failures between nodes). Data is replicated across nodes and networks to maintain the system during an outage.
		
- Example: Suppose a write happens on Node A, and a read comes to Node B before the data is replicated:
		-   **In a strongly consistent system**: Node B would wait (or fail) until it has the latest data.
		-   **In an eventually consistent system** (like most NoSQL DBs): Node B responds immediately with the latest data _it knows_, even if it’s slightly outdated.

| available-partition-tolerant | consistent-available | consistent-partition-tolerant |
|--|--|--|
| CouchDB, Cassandra | RDBMS | MongoDB, Redis |
- critisism of the CAP theorem
	- C is a property of the system in general
	- A is a property of the system only when there is a partition (=> CA=CP)
	- overhead of synchronization schemes
		- **extra time, resources, and complexity required** to keep multiple copies of data perfectly in sync across nodes or data centers.
	- C & A are not "all or nothing" because how long does it take to achieve consistency or respond to a request? -> Latency
		-**Strong consistency** increases **latency**, because:
	    - The system must coordinate between multiple nodes before confirming a write or read.
	    - This can be slow, especially over wide-area networks (e.g. across data centers).
		- **High availability** systems tend to respond quickly (low latency), but may return **stale data** (eventual consistency).
		- **Strong Consistency = Higher Latency**  
		-  **Eventual Consistency = Lower Latency**

| strong c | weak c | eventual c |
|--|--|--|
| after an update is committed, each subsequent access will return the updated value | the systems does not guarantee that subsequent accesses will return the updated value | if no new updates are made, eventually all accesses will return the last updated values (specific form of weak c) | 
|  |inconsistency window: period between update and the point in time when every access is guaranteed to return the updated value|in the absence of failures, the maximum size of the inconsistency window can be determined based on: communication delays, system load, number of replicas etc.|
### BASE
leads to levels of scalability that cannot be obtained with ACID, at the cost of (strong) consistency. High **availability** and **scalability** are prioritized over strict **consistency**. Relaxed version of ACID which is used in NoSQL and distributed systems
- **basically available**: the system works basically all the time with possible partial failures occuring, but there is never a complete system failure. (ACID may deny a request in order to preserve consistency)
- **soft state**: the system is flux and non deterministic, so changes occur all the time, even without new input. This happens because different parts of the system converge to a consistent state asynchronously.
- **eventual consistency**: at some point in the future the system will be in a consistent state
### Write (update) consistency
- problem: write-write conflict, two user want to update the same record
- pessimistic solution: prevent any such conflicts from occuring at all
- optimistic solution: detects and sorts out this conflict, after letting it happen
### Read consistency
- problem: read-write conflict, one user reads while the other writes
- Relational databases solve this using **ACID transactions**:
	- Transactions **isolate** reads and writes to prevent inconsistent views.
    - A reader either:
    - Sees **the data as it was before the write** (snapshot isolation), or
    -   Waits until the write is **fully completed**.
	 - This ensures **strong read consistency**.
 - NoSQL databases often **relax consistency** to improve scalability and availability. NoSQL systems use the idea of **aggregates** (e.g., a self-contained JSON document or row), where updates can be atomic.
	 - if an update affects **multiple aggregates** (e.g., updating two documents), there is no cross-aggregate transaction and no guaranteed read consistency between them. So during this update there is an inconsistency window where clients might read one updated/stale document.
	 - results in an misleading view
### Replication consistency
- Many NoSQL systems **replicate data** across multiple nodes (for availability/fault tolerance).
- problem: different values from different replicas/nodes because of delayed replication, stale replicas or eventual consistency policies.
## Different NoSQL Systems
### key value data model (Redis)
- data is stored based on programmer-defined keys
- queries are expressed in terms of keys
- indexes are defiend over keys
	- some systems support secondary indexes over (parts of) the value
### Document data model (MongoDB, CouchDB)
- documents (data) is stored based on programmer defined keys
- system is aware of the document structure (json, xml etc)
- queries are expressed  in terms of keys
- suppoort key-based indexes and secondary indexes
### Column-Family model (Cassandra, Google Cloud Bigtable)
- documents are stored based on a column family and key
- system is aware of the structure of the column family
- system uses column family information to replicate and distribute data
- queries are expressed with keys and column family
- secondary indexes per column are supported
### Graph data model (Neo4j, ArangoDB)
- data is stores in terms of nodes and (typed) edges and both of them can have attributes
- queries are expressed with system id, when no indexes exist
	- nodes are retrieved through attributes and edges through start/end node and/or attributes
- secondary indexes for nodes and edges are supported
## Document Stores
- Documents are hierarchical tree data structures, which can consist of maps, collections, scalar values, nested documents etc.
- Documents in a collection have similar structure
- the schema of documents can differ
	-  One document might have a `"phone"` field, another might not
    
	- Field types can differ across documents (`"price"` might be a string in one, a number in another)
- document databases store documents in the value of the key-value store, which is examinable
	- The **key** identifies the document (e.g., a unique ID)
	- The **value** is the document itself — and it's **examinable**, meaning:
    -   It can be **parsed, queried, and indexed**
 - usecases:
	 - event logging
	 - content management systems, blogging platforms
	 - web/ real-time analytics
	 - e-commerce application
 - unsuitable database solution everything that requires atomic cross-document oerations or queries aganst varying aggregate structures
## MongoDB
### Fundamental
- uses json stored as bson (binary)
- features:
	- high performance – indexes 
	- high availability – replication + eventual consistency + automatic failover 
	- automatic scaling – automatic sharding across the cluster 
	- MapReduce support
- each MongoDB instance has multiple databases 
- each database can have multiple collections 
- when we store a document, we have to choose database and collection
- documents have a flexible schema
	- collection do not enforce a specific structure of data
### Document design/ Data models
- To design document structure one need balance:
	- application needs (how is data used, what data needs to be grouped together)
	- database performance (size of documents, indexing, how should a collection be stored)
	- retrieval patterns (is data fetched together or separately? how many joins are needed)
- key decision:
	- ***References***, split data into different documents and reference them via id
		- **pros**: flexible especially for reused data, easier to update, smaller documents
		- **cons**: requires manual joins within application, more queries and aggregation lookups are needed, slower read performance for related data
	- ***Embedded documents***, related data is stored in a single document
		- **pros**: fast reads for related data (all in one), no joins needed
		- **cons**: document size limit, data duplication if reused elsewhere, harder to update frequently
```
{
  "_id": 1,
  "name": "Alice",
  "orders": [
    { "item": "Book", "qty": 1 },
    { "item": "Pen", "qty": 3 }
  ]
 }
```
Most real-world MongoDB designs use a **mix**:

-   **Embed** if the relationship is **1:1** or **1:few** and always accessed together
    
-   **Reference** if the relationship is **1:many** or **many:many**, or if the related data is large or frequently updated separately
### data modification
- update, create, delete
- modify data of single collection
- 
## BaseX, XPath, XQuery


 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3NjE2MjIyMiw2MzExNTU1MiwtMTQwMT
k2OTI3Miw3NDA3MTIxNjYsMTcxMjI4MDU0OSwtMzkwODkyOCwy
MTE5NTQ4NDMsODg0NDU2MzM5LC04MzI0NDczMTcsLTIwODUwND
EzMjksLTExMjQxODMzNTEsLTYwNzE5ODcwLDE4ODU1ODAwMTUs
MTgyNjc0NzUxMSwtMTE3MjExOTg0NywyMDk2NzIzNjAsMTc4Nz
Q5OTY5MCwyMDExMDYxNTYzLDI0NjQyMzk3NywtMTEwMzEzMDAx
M119
-->