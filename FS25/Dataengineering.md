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
|  |  |
|  |  |
|  |  |
|  |  |

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMDg4NTA0MTMsMzI2ODY0NTg4LDE5MD
g3MzE4ODEsMjEzMzk1NDUyMCwyOTgyMzEwODQsNzA5ODM3ODld
fQ==
-->