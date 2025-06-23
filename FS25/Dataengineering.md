# Dataengineering 
## Data Sources
- are nosiey (many errors: data entry, measurement, extraction)
- variety of formats
- typical issues:
	- parsing text into fields (separator issues)
	-  naming conventions: NYC vs New York
	-  missing required field (e.g., no SSN)
	- different representations (2 vs Two)
	- fields too long (get truncated)
	- primary key violation (two people with the same social security 
	number)
	- redundant records (exact match or other)
	- formatting issues – especially dates
	- licensing issues or privacy keep you from using the data as you 
	would like
## Levensthein distance Shortest Edit Distance
- the minimum number of character edit operations needed to turn one string into the other
- operations:
	- copy character from s to t (cost = 0) 
	- delete a character from s (cost = 1) 
	- insert a character into t (cost = 1) 
	- substitute one character for another (cost = 1)
$$
\text{lev}_{a,b}(i,j) = 
\begin{cases} 
\max(i,j) & \text{if } \min(i,j) = 0, \\
\min 
\begin{cases}
\text{lev}_{a,b}(i-1,j) + 1 \\
\text{lev}_{a,b}(i,j-1) + 1 \\
\text{lev}_{a,b}(i-1,j-1) + 1_{(a_i \ne b_j)}
\end{cases} & \text{otherwise}
\end{cases}
$$

Let:
-   `a` and `b` be two strings
-   `i` be the length of the prefix of `a` you're considering (first `i` characters)
-   `j` be the length of the prefix of `b` you're considering
-   `lev_{a,b}(i,j)` be the Levenshtein distance between those prefixes

Base Case:
If either `i = 0` or `j = 0`, the distance is just `max(i, j)`.  
That’s because: If one string is empty, the only way to transform it into the other is by **inserting or deleting all the characters**.

Recursive Case:
If both `i > 0` and `j > 0`, then we look at the **minimum** of the following three operations:
1.  **Deletion**:  
    Delete a character from `a`:
    $lev_{a,b}(i−1,j)+1$
2.  **Insertion**:  
    Insert a character into `a`:
	$lev_{a,b}​(i,j−1)+1$
3.  **Substitution**:  
    Replace the character `a_i` with `b_j`, **only if they're different**:
    $lev_{a,b}​(i−1,j−1)+1_{(ai​\neq bj​)}​$
    
    The $1_{(a_i \ne b_j)}$means:.
    -   Add 0 if the characters are the same
    -   Add 1 if they’re different
## Operational Database vs Data Warehouse
### OLTP
- Online Transaction Processing. 
- System zur Verarbeitung von Datenbanktransaktionen, das in Echtzeit und von vielen Benutzern gleichzeitig durchgeführt wird, typischerweise über das Internet. 
- OLTP-Systeme sind darauf ausgelegt, eine grosse Anzahl kurzer, datenbankbasierter Transaktionen effizient zu verarbeiten, wie z.B. bei Online-Banking oder E-Commerce.

### OLAP
- Online Analytical Processing, 
- Technologie zur Analyse großer Datenmengen, die in Data Warehouses oder anderen Datenspeichern liegen. 
- Ermöglicht eine multidimensionale Sicht auf Daten und unterstützt komplexe Abfragen und Berichte, die für Entscheidungsfindungen relevant sind.
- **Operations**
	- Pivot/Rotation: rotate cube axes
	- Roll-Up: Aggregate data to higher level
	- Drill-Down: Expand to lower-level details
	- Drill-Across: Compare across facts
	- Slice: Filter one dimension
	- Dice: filter multiple dimensions
	- Ranking: Top/Bottom-N
	- Push/Pull: Load comutation vs visualization

|OLTP| OLAP |
|--|--|
|Entity Relationship model| Star/ Snowflake model
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
-   **Data Sources**: Files, XML, DBs, APIs
-   **Staging Area**: Cleansing, transformation, integration  
-   **Integration Layer**: Data unified across systems
-   **Data Marts**: Domain-specific, optimized for fast querying
-   **Presentation Layer**: OLAP, reporting, data mining
    
-   **Metadata Management**: Maintains schema and lineage

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
- most time consuming part of data warehousing, as there is no standard method or system but an abundance of different tools
-  it it time intense because:
	 - different data sources with heterogeneity
	 - imense data volume
	 - the integration is complex, because of data cleaning and creating a schema and instance integration
 - There are two types of ETL
	 - **batch processing**: data is processed in batches o defines size or time values and requires space for buffering
	 - **real time processing**: data is processeed item by item continuously. Every item can only be seen once.
 - a variation of ETL ist ELT where the data transformatoin is done within the warehouse, after loading. 
	 -  Leverages SQL and DB engine
	-   Avoids external ETL tools
	 - The goal is to to do the transformation using sql statements
 
 ### extract (source to staging)
 -  data is collected from one or several sources and held in temporary storage
 - validation test are run on the data to ensure it conforms with its destinations requirements
 - its a task done regularly in order to supply updated data to the data warehouse
 - the data extracted is differentiable through a time setting and defined type of extracted data
	 - **time setting**:
		 - synchronous notification:
			 - upon an update occurence at source the data extraction is triggered
		 - asynchronous notification:
			 - periodic: the sources generates an extraction on a regular basis or the DW extracts the updated data on a regular basis
			 - event-driven: the DW extracts the updates at the end of a year or the sources notifies upon each X updates
			 - query-driven: DW checks for new updates before accessing the data
		 - **type of data**:
			 - snapshots: the source delivers the complete dataset each time, like new pricing list or product catalog
				 - requires an update detection and capturing of the update history
			 - logs: the source logs each update operation on the data through transaction/appplication-driven logging
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
	- setting date patterns, unify currencies, normalize and tokenize text
- deals with missing values on instance level (values, records sub-relations) dealing with NULL values and schema level with missing attributes. 
	- causes distortion and noise (bias) even error in calculations
	- **find the missing values** by/recognition:
		- analysis and comparison with expected values, 
		- check if the values are in an expected range/order
		- truncate values wih certain if/else conditions
	- **handle the missing values**:
		- estimate a missing value by choosing sth which does not change the average and standard deviation
		- through attribute dependencies/relationships
		- statistical techniques (linear regression, neural networks )
	


## Data Warehouse modelling
### Multidimensional Data Model
- Organizes data into facts and dimensions, resembling a data cube.
- Allows users to analyze data from multiple perspectives or dimensions (e.g., time, geography, product).
- designed to support efficient querying and reporting, particularly for OLAP
- Contains measurable, quantitative data
- Usually contains foreign keys to dimension tables and facts (measures).
-  Faster query performance through optimized structures.
-   Intuitive data exploration for business users (e.g., “Show sales by region and month”).
-   Easy aggregation (sum, average, count) across dimensions.
- **Dimension tables**
	- Contain descriptive attributes (context) related to facts (n >=2).
	- Help to slice and dice the data.
	- serve for orthogonal structuring of the dataspace 
	- Example:
		- Time dimension: day, month, quarter, year
		- Product dimension: product name, category brand
		- Location dimension: store, region country
- **Dimension hierarchies**
	- nodes of a classification hierarchy
	- classification level describes granularity
	- representation of dimensions via a classification schema
	- **simple hierarchies**
		- higher hierarchy level contains the aggregated values of exactly one lower hierarchy level 
		- top node (= root): contains a single aggregated value for the entire dimension (= ALL) 
		- country -> city-> store
	- **parallel hierarchies**
		- multiple independent grouping options are possible within the same dimension
	- no hierarchical relationship between parallel branches
	- parallel hierarchy
		- a path in the classification schema
		- a consolidation path 
- **Facts**
	- specific event/ transaction
	- basis measure
- **Measures**
	- aggregated/ calculated quantity by applying arithmetic operation on facts
	- Numeric values in the fact table, used for analysis (e.g., sum of sales, average revenue).
	- **Other properties**
		-  No double counting (**disjointness**)
		- All data levels can be aggregated (**completeness**)
- **Schema/ Model types**
	1. **Star Schema** ⭐
	- Schema is normalized to avoid update anomalies 
    -   Fact table in the center with dimension tables radiating outward.
    - single dimension table per dimension
    -   Simple and fast for querying because of redundancies in the dimension table.
	3.   **Snowflake Schema** ❄️
	- mapping of classifications : separate table for each 
classification level (e.g., product, product group, etc.)
	- dimension table include ID, characteristic attributes, foreign keys
	- fact table include foreign key referencing bottom-level category of each dimension
	- set of all foreign keys produce primary key for fact table
    -   Dimensions are normalized (split into sub-dimensions).
    -   More storage-efficient but slightly slower for querying.
 
|feature| star | snowflake |
|--|--|--|
| structure | denormalized | normalized |
| joins | fewer with simpler queries | more complex queries |
| storage | more space needed | less space needed |
| update safety | less robust | more robust |
| performance | fast querying | slower querying |
| maintenance | easier | more complex |

### Data warehouse modelling
- A data model/centralized system is designed with the needs of analysis in mind. Since the goal is to gain some knowledge for future (business) decisions through:
	- performance indicators
	- measurments of different perspectives/ dimensions
	- structures
- the design is also based upon the **available information**:
	- qualitative data which is used as navigation structure
	- quantitative data which represent the subject of the analysis
 ### dimensions
 needs to be finished (lecture 5)
# Unstructured Data

### Information retrieval IR
The activity of obtaining information resources relevant for an user's information need from a collection of information resources.
The IR process includes:
- information needs (**queries**)
- (mostly **unstructured) information** resources (text images videos)
- a **IR system/model** to identify relevant (re)sources for a given information need (query)

### Information need
- Information need is a desire to locate and obtain information to satisfy a conscious or unconscious need. 
- Information needs (conscious or unconscious) are expressed as queries.
- Such queries are usually words/phrases retrieving text information. --> Text information retrieval
- Most info resources are text based unstructured and big in scale 

### Text representation in info retrieval

- **Unstructured representation (Bag of Words - BoW)** 
	- text represented as bag of words (unordered set of words/terms)
	- syntax, semantics, pragmatics of text are ignored
		- A query like "Revenue of apple" could retrieve a result like  "Apple pencil did xy." and "Microsofts revenue .."
	- Is fast and simple and still yields fairly good results and is the standard of IR represenATION
- **Weakly structured representation**
	- certain groups of terms (e.g. ==nouns, named entities) receive a weight/ importance== and other terms are downgraded or simply ignored like ==stopwords==
	- uses part of speech tagging or named entity recognition 
	- is more costly as it uses additional preprocessing of the information resurce
- **structured representation** 
	- information resource/ terms are represented as ==graphs, terms as nodes and semantic relationships as branches==
	- very costly and virtually not used in IR

### Text preprocessing for unstructured text representations
- text is represented as unoredred set of terms (BoW) and has to be preprocessed:
 1. extracting raw text / pure textual content (e.g., from HTML, PDF, Word) 
2. language detection , Optional – if you’re dealing with multilingual document collections
3.  tokenization (separating text into character sequences) 
4. morphological normalization (lemmatization or stemming, spelling corection, case folding)
5. stopword removal
- after preprocessing the text/document is ready to be indexed

### Tokenization
- A ==token is an instance of a word== or term in a text/ document (numbers, punctuation and special chars are also tokens)
- ==tokenization is the process of breaking down a text into tokens== through a rule based heuristic approach or a ML model approach
	- process is ambiguous and not always clear how to split a string, as possible information loss can occur. 
		- Should you split a birthdate/ phonenumber/ multiword words etc.
		- different languages have different rules of tokenization
### Normalization (of tokens)
- Error/Spelling correction
- making all letters lower case (case folding)
- word disambiguation
- morpholocigal normalization by reducing different forms of the same word into a common representative form 
	- inflectional normalization (houses to house, tried to try,)
	- derivational normalization (destruction to destroy) most IR system do not perform derivational norm.

### Stemming 
- stemming is the procedure of reducing the word to its grammatical (morphosyntactic) root („recognized” -> „recogniz”, „incredibly” -> „incredibl”) by removing prefixes and suffixes
	- most common algorithm for stemming is **Porter's algorithm** which consists of different rules to reduce a word

### Lemmatization
- Reduces a word to its base or dictionary form, known as a lemma. 
- This process considers the word's meaning and context to identify the correct lemma. 
- For example, "running," "ran," and "runs" would all be lemmatized to "run".
### Expansion  of the query
- use alternate form of the query words
	- query: window search: window, Windows, windows 

### Expansion  of the query
- use alternate form of the query words
	- query: window search: window, Windows, windows 

### Stopword removal 
- removal of semantically poor terms such as articles, prepositions, conjunctions, pronouns etc.
- stopwords add nothing to the relevancy/meaning of a document
- the removal reduces the size of the vocabulary and avoids false matches

### General IR model

formally a general retrieval model is a triple of functions
1. $f_d$ is a function that maps documents (raw text) to their representation for retrieval, i.e., $f_d(d) = p_d$ , where $p_d$ is the retrieval representation of the document d
2. $f_q$ is a function that maps queries (raw text) to their representation for retrieval, i.e., $f_q(q) = s_q$ , where $s_q$ is the retrieval representation of the document q
!depending on the IR model, $f_d$ and $f_q$ may be the same function 
3. $r$ is a ranking function which computes a real number indicating the potential relevance of document $d$ for query $q$, using representations $p_d$ and $s_q$: $rel(d,q) = r(f_d(d), f_q(q)) = r(p_d , s_q )$

### Index terms and index weights
- index terms are all unique terms in the vocabulary
- each term $k_i$ for each document $d_j$ is assigned a weight $w_{ij}$ if a term doesn't appear in a document the weight is 0
- a document $d_j$ is a vector of weights for terms  $k_i$:  
	-	If term not present → weight = 0  
	- Function $g(k_i, d_j)$ computes the weight $w_{ij}$

### Boolean retrieval
- queries are boolean expression like “aliens” AND “swords” AND NOT “wizards” 
- search engine returns all documents from the collection that satisfy the Boolean expression
- Simple but lacks:
    -   Ranking
    -   Flexibility
    -   Relevance degrees
- PROs: simple and efficient
- CONS:
	- there is no ranking,
	-  sometimes unintuitive query formations 
	- binary results only
	- Not good for vague/incomplete info needs
	- Doesn't reflect partial matches or term importance

###  Inverted Index
-   Efficient data structure:  
    - For each term → list of documents where it appears (posting list)
	    - `“Frodo” → [1, 2, 7, 210]`
	-  Enables quick Boolean query evaluation
	- space-efficient than a full term-document incidence matrix.
- **Merge Operation**
	- To process queries like `"Sam" AND "Frodo"`:
		1.  Retrieve both posting lists
		2.  **Merge (intersect)** the lists
		3.  Result = documents containing both terms
-   Complexity: **O(x + y)** if lists are sorted, O(x*y) for unsorted posting lists
- For queries with multiple terms (e.g., `"Frodo" AND "Sam" AND "blue"`):
	-   Always start merging from the **shortest posting lists**
	-   Minimizes comparisons and improves speed
	-   Order of operations affects performance
- **Skip pointers**
	- Avoid comparing every entry in long posting lists when no match is possible.
    1. Insert **skip pointers** at intervals within the posting list.
    2. If the pointer jumps beyond the target value, do a normal step-by-step comparison again.
	 - **More skips**: faster skip potential, but more pointer comparisons and memory usage.
	 - **Fewer skips**: less overhead, but reduced skip opportunities.
	- Place √L **evenly spaced** skips in a list of length L (heuristic for read-only indices)
	- 
### Ranked retrieval
 Chosen strategy because:
 - **Feast or famine** problem: too many or too few results
- Users don’t want to write Boolean queries
-   Need ranking to:
    -   Prioritize more relevant documents
    -   Handle large result sets
   - Ranking principles:
	   - RP1: Term occurrence (term exists in document)
	   - RP2: Term frequency (how often term appears)
	   - RP3 Term rarity (rare terms more significant)
	   - RP4: Term proximity: Distance between query terms in document
	   - RP5: Term Position: Position of terms in document
 - **Basic Idea**
-   Represent documents and queries as **vectors** in a high-dimensional space.
-   Each dimension = an index term.
- **Vector Construction**

-   Document = `[w₁, w₂, ..., w_t]`  
    where `wᵢ` is the **weight** of term `kᵢ` in the document 
-   Query = vector in same space
- **Similarity Computation**
-   Use **cosine similarity**:
   $$sim(d, q) = \frac{d \cdot q}{||d|| \cdot ||q||}$$
```python
    from scipy import spatial
doc1 = [3, 2, 3, 0]
doc2 = [3, 1, 2, 0]
similarity = 1 - spatial.distance.cosine(doc1, doc2)
```
-   Smaller angle → higher similarity

### TFF-IDF: Weighting Terms
- **Term Frequency**
$$
tf(t, d) = \frac{\text{Number of occurrences of } t \text{ in } d}{\text{Total number of terms in } d}
$$
- **IDF (Inverse term frequency))**
$$
idf(t) = log(\frac{N}{df_t})
$$
	- N = number of documents
	- $df_t$ number of docs containing t
- **TF-IDF Score**
$$
tfidf(t,d) = tf(t,d)\cdot idf(t)
$$
	- High if `t` is frequent in `d` and rare overall
# Webcrawling
### Crawling for Search Engines
The web is crawled to find new links, which are then analyzed and added to the database. The database can be accessed by a user when searching in a search engine.
An algorithm is used to rank the pages stored in the database according to different factors to determine their importance by a search query. In order to present the pages which the user was most likely searching for
Google, Bing, Duckduckgo are common search engines which crawl for indexing pages and links to further webpages. 

### General workflow
- Input URLS or Sitemaps
- Processing: Crawler + Parser
- Output: Structured data (JSON, DB)

### Creating a search index
- Obtain URL/ Sitemaps
- crawl by following connecting links
- process the contents of the pages (not a public process and unique to each search engine)
- index the processed information / add them to the search engine
- ranking based on relevance according to factors like:
	- backlinks
	- relevance to searchquery
	- freshness, when was it published
	- metatags, keywords
	- locality and language of the user
	- search history

### Process of a search algorithm
- pages are ranked through relevance, backlinks, freshness, metatags/keywords
- pages are connected to a location, language
- search history can also play a role

### Challenges of crawling
- Data is not standardized/ structured. Or there is information missing
- technical problems:
	- long loading time
	- scaling when there are a lot of pages to crawl
	- unstable network connections

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
- Refers to the speed of data generation and processing to meet real-time or near-real-time demands
- High velocity challenges include data ingestion speed, latency, and real-time analytics.
### 4. veracity
- Reflects the accuracy, quality, and reliability a.k.a. the trustworthiness of data sources
- Data may be incomplete, inconsistent, or noisy, affecting downstream analysis
	- data consistency of sources
- results can be mostly only be considered as probable
- Trust in data depends on data lineage, source credibility, and validation techniques
- Poor veracity leads to poor decisions; hence data cleaning, deduplication, and validationare essential steps.
### 5. visibility 
- making data comprehensible and accessible. 
- importance of having a full picture of data in order to make  informative decision
	- enables better monitoring, decision-making, and compliance with regulations
- clarity of data to perform analytic operations on it
	- transforming data into **clear insights** through tools
### 6. value
- The ultimate goal: extracting **meaningful insights** and **business value** from large datasets.
- having access to Big Data is irrelevant if no value can be derived from it
	- processing and analysis are needed to extract useful patterns or predictions

## Scalability
Describes the capability of a system to handle growing amounts of data/ queries
 without losing performance
### vertical scaling (scaling up)
- traditional way of scalining by involving larger more powerful machines/server or chips
- but there are not many vendors of such machines, so the availability can be scarce and pricey. 
	- **higher costs**
	- The machine often only work with special formats
	- if the data grows further it can outgrow the machines (**data growth**)
	- the magnitude of growth is hardly predictable, when starting an application (**proactive provisioning**)
### horizontal scaling (scaling out)
- systems are distributed across different machines/ nodes
- normal performing machine are okay to store the shards of data --> machines are more cost effective
- no limit to just add new machines if dataloads outgrow current system
- data distribution, synchronization of nodes, data consistency and recovery present new issues/challanges in this type of scaling
- false assumption/ fallacies when designing or scaling distributed systems:
	- newtworks are not always reliable, they can fail. 
		- network failures have to be accomodated with retries, timeouts and replication
- Latency (Delay) is not zero. Even on fast networks there is a delay in data transmission
	- batch request, caching and reduced round trips help
- Bandwidth is not infinite. There are limits to how much data can be transferred per second.
	- Moving large data sets can be slow and costly, so data compression and locality matter
- Networks are not secure, as data in motion can be intercepted or tampered with
	- Encryption, firewalls and secure authentication are important between nodes
- Topology is dynamic, nodes can be added removed or fail at any time
	- the system must be adaptable 
- There isn't just one admin, as distributed systems are often managed by teams, departments or different organizations, which means conflicting changes or misconfiguration can happen
- Transport costs are not zero, as moving data across machines or regions cost money and time
- The network is not homogeneous, different nodes can have different hardware, network quality can differ by location which impacts performance 
## Cluster
- a collection of interconnected nodes
- each node (Knoten) has their own CPU, harddrive and memory and OS
- nodes send messages to interact with each other
- data, queries, calculations aand requests are distributed among the nodes within a cluster

## Distribution models
### Sharding
- different data on different nodes in different physical locations
	- goal to have uniform data distribution
	- goal to achieve balance workload (read/write)
	- often combined with replication
- by distributiong increasing data volumes on different nodes can enhance the performance
- different users are accessing different parts of the dataset
- there is no ideal distribution of data, it should be distributed to query needs
- vertical shards: columns are split onto different nodes
- horizontal shards: rows are split
#### sharding strategies
- **mapping structures**
	- data is places on shards in predefined or random fashion
		- example round-robin
		- hard to escale or rebalance shards automatically
	- the mapping on which shard/node the data is stored, has to be maintained, which is usually done with a centralized index structure
		- a centralized index is a single point of failure and can become a performance bottleneck
- **general rules**
	- each shard store a certain type of data with algorithmic rules
		- hash partitioning
			- a hash function is applied to a key, which determines the shards
		- range partitioning
			- shards are responsible for a specific range of values
		- geographic/semantic rules
		- consistent hashing operates independently of the number of servers or objects in a distributed hash table by assigning them a position on an abstract circle or hash ring
	- no need for a centralized index, which makes it easier to rescale shards and optimize query routing
	- its in general more deterministic and scalable
	- but it can lead to uneven distributions, and range based hashing can be imbalanced if the data is skewed
- **difficulties**
	- we need to know on what shard which data is stored, in order to know where new data should be inserted or where to retrieve requested data
	- cluster structures can change and have to be accommodated for, (node sizes, added or removed nodes, failing nodes)
	- nodes may have incomplete cluster knowledge, which could end in network messages not being delivered eventhough they are sent
### Replication
- the same data is stored on different nodes 
	- replica factor = number of such copies
- it helps in case of errors and failures
- replication is mostly used together with sharding
- **master-slave** architecture (leader follower)
	- all the nodes contain identical data
	- requests are only sent to the primary (master) as it bearss all the management responsibility
		- there is a standby master in case the primary fails. read requests can still be processed
		- the rest of nodes are secondary (slaves)
	- read request can be handles by all nodes
		- ideal for read intensive requests
	- all updates are made to the master, which propagates the changes to the slaves
	- there is only one write request processed at once
	- consistency issues with read requests when updates are still propagated to all the slaves
	- combined with sharding:
		- each shard has a master
		- a node can be a master for one record and a slave for another
- **peer-2-peer**
	- requests are sent to all nodes, because they have equal roles /responisbilities
	- all nodes contain identical data
	- all kind of requests can be handles by every node --> no bottleneck
	- read/write requests can be scaled
	- consistency issues with several write requests, hence synchronization is required to avoid conflicts
	- combined with sharding:
		- if a node fails it can be reconstructed from other nodes
		- most complicated to implement
## Consistent hashing
- Instead of mapping keys directly to nodes (which can cause major reshuffling when nodes change), **consistent hashing** maps both **keys** and **nodes** onto a circular **hash ring** (from 0° to 360°).
- **How it works**:
	- **1. Hash the keys and nodes**:
	- Each key (like `"john"`, `"kate"`, etc.) is hashed to a numerical value.
	- This value is converted into a **position on a circle**, measured in degrees (0°–360°).
	- **2. Places nodes on the circle**
	- Nodes (servers) are also hashed and placed on the same ring.
	- **3. Assign keys to nodes**
	- A key is assigned to the **first node found by moving clockwise** or counterclockwise around the circle from its position.
	-  If a key hashes to `58.8°` (like `"john"`), it gets stored on the node that is at or after that point (say, the “John” server if he is at `60°`).
- **Benefits:**
	- Ensure object keys are evenly distributed among servers
	- Minimizes data movement
		- When a node joins or leaves, only a small portion of keys need to be remapped.
		- basic hash variants cause massive shuffling
	- Scalability
	- Supports fault tolerance
		- Nodes can be replicated, and consistent hashing makes it easier to spread and recover data.
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
- **atomicity**: “all or nothing” <-> a transaction is treated as a single, indivisible unit. It either completes fully or not at all.
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
eyJoaXN0b3J5IjpbLTU2MzAwNzUxNCwxMzcxMTM5MDc4LC0xND
g0NDkzOTY2LC04NjM4ODYzOTEsNDExMjgxNjQ2LC03Mzk1MDgw
NzMsLTgwODIwMjA5Myw1MzU4ODcyMzYsMTg4NzY3OTA5NCwtMT
I1NTEwMDM2Miw0MzEyNzc1MTUsLTUxODY0NjY0LDEzMTM3OTQ2
NzUsLTEwMTMyMTMyODcsMTAyOTY1NDM5NiwtNjMzMjA5OTQ4LC
0xNjg3NzE5OTUwLDczMDkyOTg5NiwtOTQ4MzYzOTkyLDU2NTAw
MzUwNV19
-->