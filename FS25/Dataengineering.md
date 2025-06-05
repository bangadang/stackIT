# Dataengineering 

## Operational Database vs Data Warehouse
|OLTP| OLAP |
|--|--|
| Many transactions|Few transactions|
|latency sensitive|throughput sensitive|
|small payloads|large return payloads|
|balanced read/writes, ensures ACID| heavy read workloads|
| day2day processing (INSERT, UPDATE, DELETE) | historical processing (complex queries with aggregation and joins) |
| used to run a business (money transfer in banking systems, point of sales systems, order processing, inventory management) | uses ETL to analyze a business with data warehousing (marekt research, sales forecasts, financial planing) |
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
- Traditional databases do not scale for big data and adding faster or larger hardware does not suffice. 
- Most data is unstructured but databases store them structured. 
- A new solution is to use NOSQL solutions, where horizontal scalability is possible as only limited relational database system operations are supported. 
- Rather than storing the data in tables, data is stored as key value pairs.

### Why should we a databsse instead of files?
- files are only easy to access sequentially,
- there is no optimized access in files
- there is no consistency
- there is no efficient way to only access a subset of information in a file without reading everything first

### advantages of databases:
- well defined sql interfaces
- well organized and structured
- multiple users can access the DB at the same time
- synchronization among many users
- optimized query processing engines
### disadvantages of databases:
- only scales to medium-sized data sets
- does not scale out well
- problems handling semi structured data

## the basic 4 V's + 2 V's
### 1. volume
- refers to the sheer scale and dimension of data, which is enormous and often measured in tera/petabytes
	- these volumes introduce challanges in data transfer, indexing & retrieval speed
- need of the ability to process large amounts of data at once
- requires scalable storage and distributed processing systems
- the data comes from different sources
### 2. variety 
- data comes in multiple formats of different complexity
	- structured: databases
	- semi-structured: JSON, XML
	- unstructured: videos, images, emails, text
- there is no fixed structure 
- data is not immediately ready to be processed
- heterogenity <-> no uniformity or monotony
	- makes integration complex
	- flexible tools needed for ingestion and transformation
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

### Replication/ replica set
A database and its replicas can have only one primary and if this primary becomes unavailable, a process called **election** selects a primary. If there is no primary no write request are accepted.
- **write**
	1. MongoDB applies write operations on the primary 
	2. MongoDB records the operations to the primary’s oplog 
	3. secondary members replicate oplog + apply the operations to their data sets
- **read**
	- all members of the replica set/nodes accept read requests
	- all read requests are directed to the primary by the application. It guarantees lastest version and decreases read throughput
### Election
**criteria**
- heartbeat: Constant pings every set time check if all nodes are accessible
- priority comparison: nodes with high priorities can be selected primary. primary has highest priority score. every node has score 1 by default
- connection: primary has to be able to connect to the most nodes

**mechanism**
- the replica set (several nodes/server instances) elects an eligible member with the highest priority value as primary
- the first member to receive the majority of votes becomes primary
- all members of a replica set can veto an election, e.g., 
	- if the member seeking an election is not up-to-date with the most recent operation accessible in the replica set 
	- if the member seeking an election has a lower priority than another member in the set that is also eligible for election
	- **arbiters** are special nodes which do not contain any data but have voting power in case of an election is the replica set has an equal amount of members (can never be primary)
	- **secondaries** are a standby instance of a node whit a certain delay. They are used as a historical snapshot to recover from errors (unintentional databases). They do not have read access and have priority 0/ can never be primary
### Sharding
Its a databse architecture technique to scale out a db by  **horizontally partitioning data** across multiple **servers** or **nodes**. It split a big DB into smaller more managable pieces which are stored on separate servers(shard)

Sharding is used when a **single server can't handle**:
-   The **data volume** (too much data to store)
-   The **query load** (too many reads/writes)
-   The **performance requirements** (slow responses due to bottlenecks)

**components**
- **shard**: each shard is a subset of the data which is a replica set which store the data. (can be a single node for testing purposes)
- **shard key**: determines how data is split/partitioned into chunks within a shard. Choosing a good key is critical so the data can be split evenly.
	- **Chunk**: unit of migration, 64MB by standard
	- **partitioning** can be range or hash based and when a chunk exceeds its size it is split up again. Small chunks support even distribution but cause a greater expense with more frequent migration(=splitting=moving the data across shards to maintain shard size)
		- **range**:  documents with “close” shard key values are likely to be in the same chunk. Can result in an uneven distribution of data.
		- **hash**: hash of a field’s value is comuted to ensure a more random ditribution of the data. A range query may target all/many shards
	- **balancer**: handles the migration process when the distribution is uneven.
		1. during migration operations work with the original shard
		2. destination shard captures and applies all changes made to the data during migration
		3. destination shard updates the metadata regarding the location on config server
- **query routers**: interface with client application, which direct the queries or operations to the appropriate shard and return the result to the user. Usually also more than one to divide the request load
- **config servers**: Store metadata about which shard holds which piece of data. MongoDB requires three config servers in a sharded cluster.
### data modification
**journaling**: before write operations are performed on the data, they are stored in memory and in a journal, in order to bring the DB to a consisten state after a hard shutdown. The journal files (stored in the journal directory) are append only files and are deleted when all writes are completed. 
**document insertion** into an existing collection. If _id is not specified or nonexistent a new entry is created
`db.collectionName.save({document})`
**remove (all/ first) document** which have a the same key-value pair of the filter
`db.collectionName.remove({key: value})`
`db.collectionName.remove({key: value}, 1)`
**update documents**
finds all documents with filter key-value pair, modifies alls keys according to set operation and operation value
```python
db.collectionName.update(
		{key: value}, #filter
		{$operator: { key: operator_value}}, 
		{multi: true})
```
**replace existing document**
```
db.collectionName.save(
	{
	_id: int,
	rest of doc
	})
```
**queries**
```
db.collectionName.find({query criteria/filer}, {projection}).#modifier()
# all docs where key field has said value
db.collectionName.find({key: value})
#all docs where key field has one of many values
db.collectionName.find(
	{key: { $in: [value1, .., value_n]}})
#all docs wher key1 has certain value and other key is lt
db.collectionName.find(
	{key1: value,
	 key2: {$lt : value})
```
**logical query: _or_**
```
db.collectionName.find(
	{$or: [
			{key1: {$gt: value}},
			{key2: {$lt: value}}
			]
	})
```
**logical query: _and_**
```
db.collectionName.find( {key1: value, #and
						$or: [
							{key2: {$gt: value}}, 
							...
							]
						})
```
**indexes**
indexes store a portion of a collection in an easy traversable form. They are stored at collection level and speed up queries. There are:
- default _id index
- single field index defined by user
- compound index on multiple fields defined by user
- multikey index to index content stored in arrays, indexes every element of an array
- geospatial field index for 2 dimensional data
- text index for searching for string content
- hash index (supports only equality matches, as it hashes the value)
## BaseX, XPath, XQuery

## Graph Databases
These DB store entities and relationships between these entities. They consist of nodes and edges. 
- A node is an instance of an object and has properties (e.g. name)
- Edges have a directional significance and have a type describing the relationship (e.g. friend, married). 
- The nodes are usually organized by relationships, which allow us to find interesting pattern. (Can be traversed by DFS, BFS)
- Common GraphDB are Neo4j, FlockDB, ArangoDB

**Example** 
((Person({name: Alice, ..}) --[loves]-->(Person({name: Bob, ..})))
RDBMS can only store a single type of relationship unlike GraphDB. In order to add another the schema has to change and data has to be moved. GraphDB can dynamically add and delete relationships. RDBMS are design with the data able to be retrieved in mind otherwise we work with a lot of join operations. GraphDB can be traversed with different algos from different sources to retrieve the data wanted. Since the relationships are stored within the DB they speed up the queries.

|  | RDB | Key-Val-DB | Graph DB |
|--|--|--|--|
| Schema | rigid | not needed/highly fluid | flexible |
| high transaction performance for | normal transactions | simple transactions | complex transaction |
| deep analytics performance | poor | poor | high |

**use cases**:
- connected data (social networks, link rich domains) 
- routing, dispatch, location-based services (delivery systems)
- recommendation engines
**unsuitable use cases**:
- if all entities/ a property of all entities have to be updated on a regular basis (no straight forward operation)
- big loads of data 

### Graph Theory
G = (V, E)
n = |V|
m = |E|
(weighted) Graphs can be visualized through:
- adjacency matrix
	- easy to add remove edges or check if vertices are connected.
	- they take a lot of storage space $O(n^2)$ and usually have a lot of sparse space
	- retrival of neighbouring nodes takes linear time $O(n)$
- adjacency list
	- a set of lists where each accounts for the neighbors of one node (a vector of n pointers to adjacency lists)
	- easy to obtain neighbours of a node or add a node to the structure. 
	- more compact that the matrix
	- it takes a long time to check if there is an edge between two nodes (can be optimized with sorted lists)
{v_1: [[v_i, w_i], ...,],
...,
v_n: [[v_j, w_j], ...,]}

## NEO4j
**main features**
- intuitive when data needs to be represented visually
- reliable as it conforms with ACID transactions
- durable and fast as it is disk based
- scalable, embeddable and fast
- highly available for request when distributed across multiple machines
- easy readable query language

**data model**
- **entities** = nodes/vertices
	- can have property as key value pair
	- null is not a valid property
- **relationship** = directed edges
	- can have a not null property as key value pair
	- are well traversed in both directions no need to model undiercted graphs with extra effort/ direction can be ignored when not needed
	- alwas have a start end node
	- can be recursive
- **path**: one or more nodes with a connectin relationship

**example**
```java
CREATE (alice:Person {name: 'Alice', age: 30, email: 'alice@example.com'})
CREATE (bob:Person {name: 'Bob', age: 32, email: 'bob@example.com'})
CREATE (carol:Person {name: 'Carol', age: 29, email: 'carol@example.com'})

CREATE (alice)-[:FRIENDS_WITH]->(bob)
CREATE (bob)-[:FRIENDS_WITH]->(carol)

START user=node(1,2,3)
/* or 
START p = node:node_auto_index(key=value)*/
// find alices friends
MATCH (a:Person {name: 'Alice'})-[:FRIENDS_WITH]->(friend)
RETURN friend.name, friend.email

// find all frinds of friends
MATCH (a:Person {name: 'Alice'})-[:FRIENDS_WITH]->(friend)-[:FRIENDS_WITH]->(fof)
WHERE NOT (a)-[:FRIENDS_WITH]->(fof) AND a <> fof
RETURN DISTINCT fof.name
```
### transaction management
- ACID conform
- all operation must be performed in a transaction, where nested transaction are possible
	- rollback of a nested transaction invokes a rollback of the whole transaction
- steps:
	1. begin transaction create read lock
	2. operating on the graph performing write operations
	3. mark the transaction a successful or not
	4. finish the transaction, by releasing locks and save the transaction in memory
- read operations read the last commited value
- reads do not create an locks only writes do
	- can be set explicitly
- non repeatable reads can occur
- all transactions are stored in memory
- locks are created for:
	- adding/changing/removing a property of a node/relationship
	- creating/deleting a node (lock on a specific node)
	- creating/deleting a relationship (lock on relationship an all its nodes)
- deadlocks can occur and throw an exception

### indexing
- nodes and edges are indexed with a user-specific name
- index = any number of properties of a node/edge
- automatic index can be turned on
- index can be quried as well

### high availability of Neo4j
- caues fault-tolerant architecture
	- ability of a system to continue operating correctly even when part of it fails.
- Replication several (slave/ follower) databases can be configured to be exact replicas of a single (master/leader) database. 
- There is always one leader and 0 or more followers
	- write on leader propagates to followers
	- write on followers synchronizes immediately with master
- enables a horizontally scaling read-mostly architecture. more than a single instance could handle--> replicas needed
- transactions are still atomic, consistent and durable, but eventually propagated out to other slaves
- easy to transition from single to multi machine
- failure on a slave is recognized by other instances
- failure on master causes an election

### sharding
-   Multiple graph databases run independently (called **shards** or **subgraphs**).
-   A **"Fabric" layer** sits on top and enables **global queries** across these shards.
- example : `user-db-eu`, `user-db-us`, `user-db-asia` as separate databases (shards).

### distributed architectue
Neo4j was originally a **single-node** graph database but now supports a **distributed architecture** using **Causal Clustering**, which includes:
-   **Leader** node: Handles all writes.
-   **Followers**: Replicate the leader's data; can handle reads
-   **Read Replicas**: Only read, not part of consensus group.

### eventual consistency
updates will **eventually** reach all nodes, but **no guarantees on order** or timing.

### casual consistency
 -   Guarantees that **effects follow causes**.
-   A client sees changes **it has made or been told about** before seeing later updates.
-   Ensures **stronger guarantees** than eventual consistency, without sacrificing too much availability.
- example: If you write "Alice likes Bob" and then query for Alice’s likes, **you’ll see that result**—even on a different replica.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY4ODgzNTc3OCw3MjAyNjkzNzEsLTE1Nz
M5NDIyMTUsMjI1MTc2ODk5LDIxODI1NDcxMCwtNTQ5OTMzMDk3
LC05NDE4NzQyMDgsMTkzODI1ODQ5NSwtOTY3Njg0MjU5LDg3OT
A1NzE3Nyw0NDMxMzA5NTgsLTE5MDk4MjM3NiwtNzY3NTkxODg3
LDYzMTE1NTUyLC0xNDAxOTY5MjcyLDc0MDcxMjE2NiwxNzEyMj
gwNTQ5LC0zOTA4OTI4LDIxMTk1NDg0Myw4ODQ0NTYzMzldfQ==

-->