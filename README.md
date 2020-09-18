# Data-warehousing-concepts

**1. [ Introduction to Data warehousing ](#introduction-to-datawarehousing)   
2. [OLTP ( Online Transactional Processing ) and OLAP ( Online Analytical Processing )](#oltp-and-olap)  
3. [Datamart and Metadata](#data-mart-and-metadata)  
4. [Data modelling](#data-modelling)    
5. [Entity Relational ( ER ) model](#er-model)    
6. [Dimensioanl model](#dimensional-model)  
7. [ Schemas ](#schemas)    
8. [Indexes](#indexes)  
9. [Data integration and ETL](#data-integration-and-etl)    
10. [Data warehouse Implementation Approach](#dwbietl-implementation-approach)**


## Introduction to Data warehousing
***

##  What is Data Warehousing?
Data Warehousing (DW) is a process for collecting and managing data from varied sources to provide meaningful business insights.
It is a process of transforming data into information

A Data warehouse is typically used to connect and analyze business data from heterogeneous sources.
The data warehouse is the core of the BI system which is built for data analysis and reporting.
 
## What is Data Mining?
 Data mining is looking for patterns in the data that may lead to higher sales and profits.

##  Why We Need Data Warehouse?

- Data warehouse allows users to access critical data from the number of sources in a single place.
 Therefore, it saves the user's time of retrieving data from multiple sources.
 
- Data warehouse stores a large amount of historical data. 
 This helps users to analyze different time periods and trends to make future predictions.
 
##  Characteristics of Data warehouse:

**Subject-Oriented**    
A data warehouse is subject-oriented as it offers information regarding a theme instead of companies ongoing operations. 
These subjects can be sales, marketing, distributions, etc.

**Integrated**  
Data is collected from multiple sources and integrated in one place with proper formats, naming conventions, etc

**Time-variant**    
Information stored in DW should be available within the  prescribed stipulated timeline

**Non-volatile**    
The previous data is not erased when new data is entered in it.

##  What is Business Intelligence?
- BI (Business Intelligence) is a set of processes, architectures, and technologies that convert raw data into meaningful information 
  that drives profitable business actions.
- It is a suite of software and services to transform data into actionable intelligence and knowledge.

- BI has a direct impact on an organization's strategic, tactical and operational business decisions.
--BI supports fact-based decision making using historical data rather than assumptions and gut feeling.

- BI tools perform data analysis and create reports, summaries, dashboards, maps, graphs, and
charts to provide users with detailed intelligence about the nature of the business.

##  Some of the tools used for BI:

* Excel

* Reporting tool    
    - Tableau
    - Qlik view
    - SAP Business Objects
    - IBM Cognos
 
* OLAP Tool
    - Hyperion Cubes
    - SQL server reporting services
 
* Data Mining tools 
 
 
##  Data warehouse architecture:

**Three-Tier Data Warehouse Architecture**  
Generally, a data warehouse adopts a three-tier architecture.

![Datawarehouse architecture](https://panoply.io/uploads/versions/diagram1---x----750-1087x---.jpg)

**Bottom Tier** −   
 The bottom tier of the architecture is the data warehouse database server. 
              It is the relational database system. We use the back end tools and utilities to feed data into the bottom tier.
              These back end tools and utilities perform the Extract, Clean, Load, and refresh functions.

**Middle Tier** −   
In the middle tier, we have the OLAP Server that can be implemented in either of the following ways.

  * By Relational OLAP (ROLAP), which is an extended relational database management system.  
  The ROLAP maps the operations on multidimensional data to standard relational operations.

  * By Multidimensional OLAP (MOLAP) model, which directly implements the multidimensional data and operations.

**Top-Tier** −  
    This tier is the front-end client layer. This layer holds the query tools and reporting tools, analysis tools and data mining tools.


##  Purpose of Staging area:

A data staging area (DSA) is a temporary storage area between the data sources and a data warehouse.
The staging area is used to combine data from multiple data sources and apply transformations, validations, data cleansing.

## OLTP and OLAP
***
**OLTP ( Online Transactional Processing )**  
OLTP (Online Transactional Processing) is a category of data processing that is focused on transaction-oriented tasks.  

 OLTP typically involves inserting, updating, and/or deleting small amounts of data in a database.  

 It is often used for financial transactions, order entry, retail sales and CRM.

**OLAP ( Online Analytical Processing )**   
It is a technology that enables analysts to extract and view business data from different points of view. 

At the core of the OLAP, concept is an OLAP Cube. The OLAP cube is a data structure optimized for very quick data analysis.

Some of the analytical operations of OLAP:

**ROLL UP**   
Known as 'aggregation'

!['Rollup example](https://www.guru99.com/images/1/022218_1238_WhatisOLAPO2.png)

* In this example, cities New jersey and Lost Angles and rolled up into country USA
* The sales figure of New Jersey and Los Angeles are 440 and 1560 respectively. They become 2000 after roll-up
* In this aggregation process, data is location hierarchy moves up from the city to the country.
* In the roll-up process at least one or more dimensions need to be removed. In this example, the Quarter dimension is removed.

**DRILL DOWN**  
In drill-down data is fragmented into smaller parts. It is the opposite of the rollup process.

![Drill-Down example](https://www.guru99.com/images/1/022218_1238_WhatisOLAPO3.png)

* Quarter Q1 is drilled down to months January, February, and March. Corresponding sales are also registers.
* In this example, dimension months are added.  

**SLICE**   
Here, one dimension is selected, and a new sub-cube is created.

![Slice example](https://www.guru99.com/images/1/022218_1238_WhatisOLAPO4.png)

* Dimension Time is Sliced with Q1 as the filter.
* A new cube is created altogether.

**DICE**    
This operation is similar to a slice. The difference in dice is you select 2 or more dimensions that result in the creation of a sub-cube.

![Dice example](https://www.guru99.com/images/1/022218_1238_WhatisOLAPO5.png)   

**PIVOT**   
In Pivot, you rotate the data axes to provide a substitute presentation of data.

In the following example, the pivot is based on item types.

![Pivot example](https://www.guru99.com/images/1/022218_1238_WhatisOLAPO6.png)

**Types of OLAP**

ROLAP :  
* Relational OLAP (ROLAP), which is an extended relational database management system. 
* The ROLAP maps the operations on multidimensional data to standard relational operations.

MOLAP :
* Multidimensional OLAP (MOLAP) model, which directly implements the multidimensional data and operations.

HOLAP :
* In HOLAP approach the aggregated totals are stored in a multidimensional database while the detailed data is stored in        the relational database

DOLAP :
* In Desktop OLAP, a user downloads a part of the data from the database locally, or on their desktop and analyze it.

**OLTP vs OLAP**

| OLTP ( Online Transactional Processing )                                                                                | OLAP ( Online Analytical Processing )                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| OLTP is a type of data processing that executes transaction-focused tasks.                                            | A category of software tools that provide analysis of data for business decisions.                                       |
| It involves inserting, deleting, or updating small quantities of database data.                                       | The primary objective here is data analysis and not data processing.                                                      |
| It is often used for financial transactions, order entry, retail sales, and CRM.                                       | OLAP creates a single platform for all type of business analytical needs which includes planning, budgeting, forecasting, |
| OLTP uses traditional DBMS.                                                                                           | OLAP uses the data warehouse.                                                                                             |
| Tables in OLTP database are normalized.                                                                               | Tables in OLAP database are not normalized.                                                                               |
| Allow read/write operations.                                                                                          | Mostly select operations                                                                                                  |
| Queries in this process are standardized and simple.                                                                  | Complex queries involving aggregations.                                                                                   |
| Complete backup of the data combined with incremental backups                                                         | OLAP only need a backup from time to time. Backup is not important compared to OLTP                                       |
| DB design is application-oriented. Example: Database design changes with industry like Retail, Airline, Banking, etc. | DB design is subject-oriented.  Example: Database design changes with subjects like sales, marketing, purchasing, etc.    |

## Data Mart and Metadata
***
#### What is Data Mart?

A data mart is focused on a single functional area of an organization and contains a subset of data stored in a Data Warehouse.

- A data mart is a condensed version of Data Warehouse and is designed for 
    use by a specific department, unit or set of users in an organization. 
    E.g., Marketing, Sales, HR or finance. It is often controlled by a single department in an organization.
- Data Mart usually draws data from only a few sources compared to a Data warehouse.
- Data marts are small in size and are more flexible compared to a Datawarehouse.

####    Why do we need Data Mart?

- Data Mart helps to enhance the user's response time due to reduction in the volume of data
- It provides easy access to frequently requested data.
- Datamart are simpler to implement when compared to corporate Datawarehouse. 
- Data is partitioned and allows very granular access control privileges.


![Datawarehouse and datamarts](https://panoply.io/uploads/versions/diagram8-1---x----750-376x---.jpg)
#### Difference between Data Warehouse and Datamart
| Data Warehouse                                                                                                                | Data Mart                                                                                                     |
|----------------------------------------------------------------------------------------------------------------------------   |-------------------------------------------------------------------------------------------------------------- |
| A data warehouse is a large centralized repository of data that contains information from many sources within an organization.    | A data mart is an only subtype of a Data Warehouse. It is designed to meet the need of a certain user group.  |
| The designing process of Data Warehouse is quite difficult.                                                                   | The designing process of Data Mart is easy.                                                                   |
| Data warehousing is broadly focused in all the departments. It is possible that it can even represent the entire company.     | Data Mart is subject-oriented, and it is used at a department level.                                          |
| The size of the Data Warehouse may range from 100 GB to 1 TB+.                                                                | The Size of Data Mart is less than 100 GB.                                                                    |
| The implementation process of Data Warehouse can be extended from months to years.                                            | The implementation process of Data Mart is restricted to few months.                                          |                   |

## Metadata   
Metadata is simply defined as data about data. 

- The data that is used to represent other data is known as metadata. For example, the index of a book serves as a metadata for the contents in the book. 
- In other words, we can say that metadata is the summarized data that leads us to detailed data.
- In terms of data warehouse, we can define metadata as follows.
    * Metadata is the road-map to a data warehouse.
    * Metadata in a data warehouse defines the warehouse objects.
    * Metadata acts as a directory. This directory helps the decision support system to locate the contents of a data warehouse.
    
**Categories of Metadata**

**Technical Metadata**   

This will store technical data such as tables attributes, their data types, size, primary key attributes, foreign key attributes, and any indexes.

Intended for developers/testers/analysts/DBAs to build (or) maintain the system.

**Business Metadata**  

Data will be stored in business terms for the benefit of end-users/analysts/managers/ any users.

It can be derived from any business documents and business rules.

**Operational Metadata**   

As we know the data into the DW system is sourced from many operational systems with diverse data types and fields.     

DW extracts transform such data into the unique type and load all this data into the system.    

At the same time, it must be able to link back the data to its source system data. 

The metadata that stores all these operational data sources information is known as Operational metadata.

## Data Modelling
***
### What is Data Modelling?
Data modelling is the process of creating a data model for the data to be stored in a database. 

- This data model is a conceptual representation of Data objects, the associations between different data objects and the rules.
- Data modeling helps in the visual representation of data and enforces business rules, regulatory compliances, and government policies on the data.
- Data Models ensure consistency in naming conventions, default values, semantics, security while ensuring the quality of the data.

- Data model emphasizes on what data is needed and how it should be organized instead of what operations need to be performed on the data.

Data Models techniques are:

1.Entity Relationship (E-R) Model   
2.Multidimensional modeling

**Why use Data Model?**

* A data model helps design the database at the conceptual, physical and logical levels.
Data Model structure helps to define the relational tables, primary and foreign keys, and stored procedures. 

* It provides a clear picture of the base data and can be used by database developers to create a physical database.
    
**Types of Data Models**

**Conceptual**  
This Data Model defines WHAT the system contains.   
A conceptual data model identifies the highest-level relationships between the different entities. 

Features of the conceptual data model include:

* Includes the important entities and the relationships among them.
* No attribute is specified.
* No primary key is specified.

The figure below is an example of a conceptual data model.

![Conceptual model](https://www.1keydata.com/datawarehousing/conceptual-data-model.jpg)

From the figure above, we can see that the only information shown via the conceptual data model is the entities that describe the data and the relationships between those entities. No other information is shown through the conceptual data model.

**Logical**     
Defines HOW the system should be implemented regardless of the DBMS.    
A logical data model describes the data in as much detail as possible, without regard to how they will be physically implemented in the database.
    
Features of a logical data model include:
* Includes all entities and relationships among them.
* All attributes for each entity are specified.
* The primary key for each entity is specified.
* Foreign keys (keys identifying the relationship between different entities) are specified.
* Normalization occurs at this level.

The figure below is an example of a logical data model.

![Logical model](https://www.1keydata.com/datawarehousing/logical-data-model.jpg)

***Conceptual vs Logical data model***

- In a logical data model, primary keys are present, whereas, in a conceptual data model, no primary key is present.
- In a logical data model, all attributes are specified within an entity. No attributes are specified in a conceptual data model.
- Relationships between entities are specified using primary keys and foreign keys in a logical data model. 
In a conceptual data model, the relationships are simply stated, not specified, so we simply know that two entities are related, 
but we do not specify what attributes are used for this relationship.
    
**Physical**    
This Data Model describes HOW the system will be implemented using a specific DBMS system.

Physical data model represents how the model will be built in the database. 

A physical database model shows all table structures, including column name, column data type, column constraints, primary key, foreign key, and relationships between tables.
    
Features of a physical data model include:

* Specification all tables and columns.
* Foreign keys are used to identify relationships between tables.
* Denormalization may occur based on user requirements.
* Physical data model will be different for different RDBMS. For example, the data type for a column may be different between MySQL and SQL Server.
        
***Logical vs Physical Data model***

- Entity names are now table names.
- Attributes are now column names.
- Data type for each column is specified. Data types can be different depending on the actual database being used.
  
Comparison between different data models
        
| **Feature**          | **Conceptual** | **Logical** | **Physical** |
|:--------------------:|:--------------:|:-----------:|:------------:|
| Entity Names         | ✓              | ✓           |              |
| Entity Relationships | ✓              | ✓           |              |
| Attributes           |                | ✓           |              |
| Primary Keys         |                | ✓           | ✓            |
| Foreign Keys         |                | ✓           | ✓            |
| Table Names          |                |             | ✓            |
| Column Names         |                |             | ✓            |
| Column Data Types    |                |             | ✓            |

## ER model
***

ENTITY RELATIONAL (ER) MODEL is a high-level conceptual data model.     
ER modeling helps you to analyze data requirements systematically to produce a well-designed database.      
The Entity-Relation model represents real-world entities and the relationship between them.  
It is a GUI representation of the logical structure of a Database

##  Why use ER Diagrams?
- Provide a preview of how all your tables should connect, what fields are going to be on each table
- Helps to describe entities, attributes, relationships
- ER diagrams are translatable into relational tables which allows you to build databases quickly
- ER diagrams can be used by database designers as a blueprint for implementing data in specific software applications
- The database designer gains a better understanding of the information to be contained in the database with the help of ER diagram

### Components of the ER Diagram

* Entities
* Attributes
* Relationships
    
**Entity**

An Entity may be an object with a physical existence    
An entity can be a place, person, object, event or a concept, which stores data in the database   

In the ER model, an entity can be represented as rectangles.

Entity Types:
 * Strong Entity  
    * An entity which does not depend on any other entity.     
    * It has a key attribute that uniquely identifies it.     
    * Strong entity is represented by a single rectangle
    
    ![Strong entity](https://static.javatpoint.com/dbms/images/dbms-er-model-concept2.png)

 * Weak Entity    
    * An entity that depends on another entity called a weak entity.  
    * The weak entity doesn't contain any key attribute that uniquely identifies it. 
    * The weak entity is represented by a double rectangle.
  
    ![Weak entity](https://static.javatpoint.com/dbms/images/dbms-er-model-concept3.png)

**Attributes**

The attribute is used to describe the property of an entity.    
Attributes of a student can be id, age, contact number, name, etc.
    
Eclipse is used to represent an attribute.
    
Attribute Types:
    
* Key Attribute

    * The attribute which uniquely identifies each entity in the entity set is called key attribute.
    * For example, Roll_No will be unique for each student. 
    * In ER model, key attribute is represented by an oval with underlying lines.
    ![Key attribute](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-3.png) 
    
* Composite Attribute

    * An attribute composed of many other attributes is called a composite attribute.
    * For example, Address attribute of student Entity type consists of Street, City, State, and Country. 
    * In ER model, composite attribute is represented by an oval comprising of ovals.
     
  ![Composite attribute](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-4.png)
    
* Multivalued Attribute

  * An attribute consisting of more than one value for a given entity.
  * For example, Phone_No (can be more than one for a given student).
  * In ER model, a multivalued attribute is represented by a double oval.
    
    ![Mutlivalued attribute](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-5.png)

* Derived Attribute

    * An attribute that can be derived from other attributes of the entity type is known as derived attribute.
    * For example,  Age (can be derived from DOB).
    * In ER diagram, derived attribute is represented by a dashed oval.

        ![Derived attribute](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-6.png)

**Relationships**

A relationship is used to describe the relation between entities.

A diamond or rhombus is used to represent the relationship.

A relationship type represents the association between entity types.    
For example,‘Enrolled in’ is a relationship type that exists between entity type Student and Course.    

In ER diagram, relationship type is represented by a diamond and connecting the entities with lines.

![Relatioship](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-8.png)

Degree of a relationship set:   

The number of different entity sets participating in a relationship set is called a degree of a relationship set.

Unary Relationship – only ONE entity set participating in a relation    
For example, one person is married to only one person.
![](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-10.png)

Binary Relationship –TWO entities set participating in a relation   
For example, Student is enrolled in Course.
![](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-8.png)
    
n-ary Relationship –n entities set participating in a relation

**Cardinality**     
    The number of times an entity of an entity set participates in a relationship
    
***One-to-One***    
One entity from entity set X can be associated with at most one entity of entity set Y and vice versa.  
For example, A male can marry to one female and a female can marry to one male
![](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-12.png)

***One-To-Many***   
One entity from entity set X, and more than one entity from entity set Y associates with the relationship   
For example, one class is consisting of multiple students.

    
***Many-To-One***   
More than one entity from entity set X, and only One entity from entity set Y associates with the relationship  
For example, multiple students can enroll in the same course.

![](https://static.javatpoint.com/dbms/images/dbms-er-model-concept12.png)

***Many-To-Many***  
One entity from X can be associated with more than one entity from Y and vice versa.    
For example, a student can take more than one course and one course can be taken by many students. 

![](https://media.geeksforgeeks.org/wp-content/uploads/Database-Management-System-ER-Model-16.png)

## Dimensional model
***
**What is Dimensional Model?**

A dimensional model is a data structure technique optimized for Data warehousing tools. 

- A Dimensional model is designed to read, summarize, analyze numeric information like values, balances, counts, weights, etc. in a data warehouse.     
In contrast, relation models are optimized for addition, updating and deletion of data in a real-time Online Transaction System.

- These dimensional and relational models have their unique way of data storage that has specific advantages.

    For instance, in the relational model, normalization and ER models reduce redundancy in data.    
    On the contrary, the dimensional model arranges data in such a way that it is easier to retrieve information and generate reports.

Hence, Dimensional models are used in data warehouse systems and not a good fit for relational systems.

**Elements of Dimensional Data model**

**Fact**    
Facts are the measurements/metrics or facts from your business process.     
For a Sales business process, a measurement would be quarterly sales number

### Types of Facts:
***Additive***  
Measures that can be added across all dimensions.    
A sales fact is a good example for additive fact.

***Semi Additive***     
Measures that can be added across a few dimensions and not with others    
Daily balances fact can be summed up through the customers dimension but not through the time dimension.
    
***Non Additive***  
Measures that cannot be added across all dimensions     
Facts that have percentages, ratios calculated.
    
***Factless facts***    
Fact table that contains no measures or facts.  
Fact table which has only product key and date key is a factless fact.


**Dimension**   
Dimension provides the context surrounding a business process event (facts). In simple terms, they give who, what, whereof a fact.  
In the Sales business process, for the fact quarterly sales number, dimensions would be

Customer, Products, Location

A dimension table consists of the attributes about the facts. 

**Types of Dimensions**

***Conformed Dimension***   
A dimension that is used in multiple locations is called a conformed dimension.     
Conformed dimension has exactly the same meaning and content when being referred from different fact tables     
 A conformed dimension may be used with multiple fact tables in a single database or across multiple data marts or data warehouses.    
It helps in creating consistency so that the same can be maintained across the fact tables.

**Why is conformed dimension important?**   
This goes back to the definition of data warehouse being "integrated." Integrated means that even if a particular entity had different meanings and different attributes in the source systems, there must be a single version of this entity once the data flows into the data warehouse.

The time dimension is a common conformed dimension in an organization.


Here in the below schema LOCATION and DATE are conformed dimensions

![](https://wisdomschema.com/wp-content/uploads/2015/06/Conformed_Dim_1.png)


***Junk Dimension***

In data warehouse design, frequently we run into a situation where there are yes/no indicator fields in the source system. Through business analysis, we know it is necessary to keep such information in the fact table. However, if keep all those indicator fields in the fact table, not only do we need to build many small dimension tables, but the amount of information stored in the fact table also increases tremendously, leading to possible performance and management issues.

Junk dimension is the way to solve this problem. 

A junk dimension is a collection of random transactional codes flags and/or text attributes that are unrelated to any particular dimension. The junk dimension is simply a structure that provides a convenient place to store the junk attributes.

In a junk dimension, we combine these indicator fields into a single dimension. This way, we'll only need to build a single dimension table, and the number of fields in the fact table, as well as the size of the fact table, can be decreased.

Let's look at an example. Assuming that we have the following fact table:

| Fact\_Product |
|---------------|
| Prod\_id      |
| Customer\_id  |
| Order\_id     |
| Date          |
| Location      |
| Qty           |
| Amount        |
| Picked        |
| Packed        |
| Shipped       |
| Delivered     |
| Received      |
| Returned      |
| Refunded      |
| Restocked     |




In this example,  Picked, Packed, Shipped, Delivered, Received, Returned, Refunded and Restocked  are all indicator fields. In this existing format, each one of them is a dimension. Using the junk dimension principle, we can combine them into a single junk dimension, resulting in the following fact table:

| **Fact_Product** |
|------------------|
| Prod_id          |
| Customer_id      |
| Order_id         |
| Date             |
| Location         |
| Qty              |
| Amount           |
| JunkKEY         |

The content of the junk dimension table would look like the following:

![](https://3.bp.blogspot.com/-lqMa_YA710U/UBlE8lbEGMI/AAAAAAAAADg/vn2EpXQGlI0/s1600/junk.jpg)


**Degenerate dimensions**   
A degenerate dimension is when the dimension attribute is stored as part of fact table, and not in a separate dimension table. These are essentially dimension keys for which there are no other attributes.    

In a data warehouse, these are often used as the result of a drill through query to analyze the source of an aggregated number in a report.
You can use these values to trace back to transactions in the OLTP system.
Ex : Sales transaction number in Sales fact table

**Slowly Changing Dimensions ( SCD )**

Attributes of a dimension that would undergo changes over time. It depends on the business requirement whether particular attribute history of changes should be preserved in the data warehouse. This is called a slowly changing attribute and a dimension containing such an attribute is called a slowly changing dimension.

There are in general three ways to solve this type of problem, and they are categorized as follows:

**Type 1**  
SCD type 1 methodology is used when there is no need to store historical data in the dimension table.   
This method overwrites the old data in the dimension table with the new data.   
It is used to correct data errors in the dimension.

As an example, i have the customer table with the below data.
```
surrogate_key customer_id customer_name Location
------------------------------------------------
1             1           Marspton       Illions
```
Here the customer name is misspelled. It should be Marston instead of Marspton. If you use type1 method, it just simply overwrites the data. The data in the updated table will be.

```
surrogate_key customer_id customer_name Location
------------------------------------------------
1             1           Marston       Illions
```
* The advantage of type1 is ease of maintenance and less space occupied.    
*  The disadvantage is that there is no historical data kept in the data warehouse.

**Type 2**  
 SCD type 2 stores the entire history of the data in the dimension table.   
 With type 2 we can store unlimited history in the dimension table.
 
In type 2, you can store the data in three different ways. They are
* Versioning
* Flagging
* Effective Date

***Versioning***    
 In versioning method, a sequence number is used to represent the change. The latest sequence number always represents the current row and the previous sequence numbers represents the past data.

```
surrogate_key customer_id customer_name Location Version
--------------------------------------------------------
1             1           Marston       Illions  1
```
The customer moves from Illions to Seattle and the version number will be incremented. The dimension table will look as

```
surrogate_key customer_id customer_name Location Version
--------------------------------------------------------
1             1           Marston       Illions  1
2             1           Marston       Seattle  2
```
Now again if the customer is moved to another location, a new record will be inserted into the dimension table with the next version number.

***Flagging***  
 In flagging method, a flag column is created in the dimension table. The current record will have the flag value as 1 and the previous records will have the flag as 0.
 ```
 surrogate_key customer_id customer_name Location flag
--------------------------------------------------------
1             1           Marston       Illions  1
```
Now when the customer moves to a new location, the old records will be updated with flag value as 0 and the latest record will have the flag value as 1.
```
surrogate_key customer_id customer_name Location Version
--------------------------------------------------------
1             1           Marston       Illions  0
2             1           Marston       Seattle  1
```
***Effective Date***    
 In Effective Date method, the period of the change is tracked using the start_date and end_date columns in the dimension table.
 ```
 surrogate_key customer_id customer_name Location Start_date   End_date
-------------------------------------------------------------------------
1             1           Marston       Illions  01-Mar-2010  20-Fdb-2011
2             1           Marston       Seattle  21-Feb-2011  NULL
```
The NULL in the End_Date indicates the current version of the data and the remaining records indicate the past data. 

**Type 3**  
In type 3 method, only the current status and previous status of the row is maintained in the table. To track these changes two separate columns are created in the table.  

The customer dimension table in the type 3 method will look as
```
surrogate_key customer_id customer_name Current_Location previous_location
--------------------------------------------------------------------------
1             1           Marston       Illions          NULL 
```
Let say, the customer moves from Illions to Seattle and the updated table will look as
```
surrogate_key customer_id customer_name Current_Location previous_location
--------------------------------------------------------------------------
1             1           Marston       Seattle          Illions
```
Now again if the customer moves from seattle to NewYork, then the updated table will be
```
surrogate_key customer_id customer_name Current_Location previous_location
--------------------------------------------------------------------------
1             1           Marston       NewYork          Seattle
```
The type 3 method will have limited history and it depends on the number of columns you create.

**Rapidly Changing Dimension**  
A dimension attribute that changes frequently is a rapidly changing attribute. If you don’t need to track the changes, the rapidly changing attribute is no problem, but if you do need to track the changes, using a standard slowly changing dimension technique can result in a huge inflation of the size of the dimension.     
One solution is to move the attribute to its own dimension, with a separate foreign key in the fact table. This new dimension is called a rapidly changing dimension.

Example: Take a look at the following dimension attributes of customer
```
C_Id
Name
Location
Age_band
Salary_band
```
The age band and salary band are going to change frequently. So create a separate small dimension table with only these attributes. 
The new tables are :
```
Table name : customer
C_Id
Name
Location

Table name: customer_mini
M_id
Age_band
Salary_band

Fact table:
Id
C_Id
M_Id
----
```
## Schemas
A schema is a collection of database objects, including tables, views, indexes, and synonyms.

There is a variety of ways of arranging schema objects in the schema models designed for data warehousing.

### Types of schemas

**Star schema**

A star schema is the one in which a central fact table (which is in 3NF) is surrounded by denormalized dimensional tables.     
It has simple structure and most widely used schema in data warehouse


Characteristics:    
* The dimension table is joined to the fact table using a foreign key
* The dimension table are not joined to each other
* Greater query efficiency
* The Star schema is easy to understand and provides optimal disk usage.

Example of star schema

![](https://media.geeksforgeeks.org/wp-content/uploads/Untitled-drawing-3-2.png)

**Snowflake schema**    
A Snowflake Schema is an extension of a Star Schema, and it adds additional dimensions.  
Snowflake schemas normalize dimensions to eliminate redundancy. ie the dimension data has been grouped into multiple tables instead of one large table. 

Characteristics:
* The main benefit of the snowflake schema it uses smaller disk space.
* Due to multiple tables query performance is reduced

Example of Snowflake schema

![](https://media.geeksforgeeks.org/wp-content/uploads/Capture-163.png)


**Star schema vs Snowflake schema**


 **Basis for comparison**         | **Star Schema**                            | **Snowflake Schema**                                                 
----------------------------------|--------------------------------------------|----------------------------------------------------------------------
 Structure of schema              | Contains fact and dimension tables\.       | Contains sub\-dimension tables including fact and dimension tables\. 
 Use of normalization             | Doesn't use normalization\.                | Uses normalization and denormalization\.                             
 Ease of use                      | Simple to understand and easily designed\. | Hard to understand and design\.                                      
 Data model                       | Top\-down                                  | Bottom\-up                                                           
 Query complexity                 | Low                                        | High                                                                 
 Foreign key join used            | Fewer                                      | Large in number                                                      
 Space usage                      | More                                       | Less                                                                 
 Time consumed in query execution | Less                                       | More comparatively due to excessive use of join\.                    


**Fact constellation schema or Galaxy schema**

Data warehouse fact constellation schema is viewed as a collection of many star schemas. For each star schema or snowflake schema it is possible to create Fact Constellation schema.   
Sophisticated application requires the Fact constellation schemas.

Example of Fact Constellation schema

![](https://cdn.buttercms.com/hDC8gYTwRLqAwSYUFxw6)

Characteristics:

* This schema is more complex than star or snowflake schema architecture design because it contains multiple fact tables. 
* Dimensions can be shared among multiple fact tables ( Conformed Dimensions ).
* Fact constellation solution is hard to maintain and support
* Galaxy Schema is completely normalized
* As the system and querying process is multifaceted, the speed of Data Retrieval from the database systems is by very slow.

## Indexes

Data Structures hold field values and pointers to the related indexes which are sorted to quickly find the record.

Use indexes when have a large data set, In most cases, the database can efficiently select all the information from table. But if we notice that a particular retrieval operation is taking time then analyze it and add the index to check if the performance is optimal.
Most of the time in early stages the tables won't require any index, but as more data is added we may find the need to add indexes.

Indexing the data warehousing can reduce the amount of time it takes to see the query results.

***Bitmap Index***          
For datawarehouse that have large amount of data and ad hoc queries and low-level concurrent DML Transactions.

***Bitmap Indexing provides:***

+ Reduced response time                
+ Reduced storage requirements        
+ Performance gains           
+ Efficient maintenance during parallel DML and loads.

 Bitmap indexes are only a fraction of the size of the indexed data in the table.

Each bit in the bitmap corresponds to a possible rowid, a possible mapping function will converts the bit into rowid so that the bitmap provides the same functionality as normal index.

Most effective for queries that contain multiple conditions in the where clause. These indexes are primarily intended for applications where users query the data rather than update it. Not suitable for OLTP applications with large number of concurrent transactions modifying the data.

A bit map can be considered for any non-unique column (low cardinality index) and majority of the indexes in the warehouse should be bitmaps. Bitmap indexes are ideal to the columns which have low cardinality columns.

Cardinality is ratio of number of distinct values to the number of rows in the table

For example, consider the EMP table with two new columns: gender and marital status:

![](https://logicalread.com/media/394194/0490_001.jpg)

The bitmaps stored may be the following 

![](https://logicalread.com/media/394199/0490_002.jpg)

Click [here](https://www.programmerinterview.com/database-sql/what-is-a-bitmap-index/) to get detailed information on bitmap index  

***B-Tree Index***      
B-Tree index is organized like an upside-down tree. The bottom level of the index holds the actual data values and pointers to the corresponding rows. B-Tree indexes are most commonly used in a data warehouse to index unique columns.

Use B-Tree indexes when you know that your typical query refers to the indexed columns and retrieves a few rows. If looking for retrieving more rows in the table you might want to read or scan the table.


In general bitmap indexes are more common than B-Tree indexes in most data warehouse environments.

***B-Tree Vs Bitmap***  
+ Bitmap are always stored in compressed manner without the need of any user intervention. B-Tree can be stored specifically in a compressed manner to enable huge space savings which leads to less I/O and better performance.

+ Bitmap index is generally for columns with lots of duplicate values(low cardinality) while B-Tree indexes are best for high cardinality columns.

+ Internal structure is quite different. A B-tree index has index nodes, it is a tree form. A Bitmap index looks like a two-dimensional array with zero and one values.


## Data Integration and ETL 

Data Integration involves combining data from several disparate sources, which are stored using various technologies and provide unified view of the data.

Integration begins with the ingestion process and includes steps such as discovery, cleansing, ETL Mapping, and transformation. Data integration ultimately enables analytics tools to produce effective, actionable intelligence.

With the increase in the volume, variety, and velocity of data integration has become the crucial step for many enterprises to be successful.


Data integration can be performed on several organization levels. As we go down the level of automated integration increases.

Types of Integration:

+ Manual Data Integration 
+ Application Based Integration 
+ Middleware Data Integration
+ Uniform Data Access or Virtual Integration
+ Common Storage Integration 
  
Businesses are using data integration for a deeper understanding of their business data. Below are some common use cases of data integration in business operations.

+ Data Warehouses
+ ETL and Business Operations
+ Centralized Business Intelligence
+ Data Lakes

## ETL (Extract - Transform - Load )
Type of data Integration which refers to three steps (extract, transform, load) used to blend data from multiple sources. During the process data is taken from source (extract) and convert into a required format (transformed) which can be analyzed and stored(loaded) into a data warehouse or other system.

ELT is an alternate but related approach designed to push processing down to the database for improved performance.

Businesses are relied on ETL process for many years to get a consolidated view of the data that drives better business decisions. This method of integrating data from multiple systems and sources is still a core component of an organization's data integration toolbox.


+ ETL provides deep historical context for the business. 
+ By Consolidated view ETL makes it easier for business users to analyze and report on data relevant to their initiatives.
+ ETL reuses purposes that move data without requiring to write any scripts.

+ ETL has evolved over time to support emerging integration requirements for things like streaming data.

+ Organizations need both ETL and ELT to bring data together, maintain accuracy and provide the auditing typically required for data warehousing, reporting and analytics

Few ETL Tools for data warehouses are Amazon Redshift, Oracle, CloverETL, Talend.

Extraction methods in data warehousing:

+ Full Extraction 
+ Periodic Extraction
  

**Full Extraction:**            
This type of extraction is used when the data needs to be extracted and loaded for the first time. In this the data is extracted completely. This extraction reflects the current data available in the source system.

**Periodic Extraction or Incremental:**    
In incremental extraction, the changes in source data need to be tracked since the last extraction. Only these changes will be extracted and then loaded and these can be detected from the source which have last-changed timestamp. A change table is created which is keeps track of the changes in the source data.


**ETL VS ELT**

In the Begining there was ETL. Later came ELT a contemporary method.

In ELT approach, after extracting data from source we immediately starts the loading phase moving all the date into single and centralized data repository and then uses processing power of source system to conduct transformations. This speeds data processing because it happens where the data lives.

In this way, ELT approach provides a modern alternative to ETL. This approach is still evolving. This approach enables unlimited access to all of your data at any time.

+ ETL uses Staging area and system, extra time to load data. In ELT it is all in one system, load only once.

+ ETL needs to wait especially for big data sizes and in ELT speed is not dependent on size.

+ ETL requires high maintenance because we need to again load and transform if data is deleted or want to enhance the main data repository. All data is available in ELT.



ELT is more efficient than ETL for development. ELT is much more flexible than ETL. With ELT, users can run new transformations, test and enhance queries directly on the raw data as it is required without time and complexity that is with ETL.


## DW/BI/ETL Implementation Approach ##

Below are the phases in implementation of Datawarehouse:
+ Knowledge capture sessions
+ Requirements
+ Architecture 
+ Data Model
+ ETL Phase
+ Data Access
+ Deploy.
  

**Knowledge Capture Sessions:**

In this phase all the main members of the company come together and share their views about the new applications.

So the knowledge capture sessions can range from collecting innovative ideas from your employees to only to a particular application within your enterprise out of thousands of applications it can be only focused on certain application where you just talk per person whose there in the application or who knows the application from past 10 years or 15 years right now and they might be still using the legacy systems and now the business wants to go to the latest open source technologies of big data.

**Requirements:**       
Collecting requirements which is the criteria for successful implementation of data warehouse. The requirements for analysis and reporting, as well as hardware, software, implementation should be specified. The organization’s long-term business strategy should be as important as current business and technical requirements.

After outlining the business and technical strategy, the next step is to determine how an organization will backup the data from the warehouse and how to recover the system in the event of a failure

**Architecture:**       
Next step is to determine the physical environment of the data warehouse. There should separate physical application servers and databases, as well as separate ETL / ELT, OLAP processes and reports configured for development, testing, and production. By building separate physical environment one must ensure that all the changes can be tested before moving into production. Development and testing should be done without stopping the production environment.

**Data Model:**     
After identifying the business data we can create conceptual model of the data. Determine the subjects that will be expressed as the fact tables and dimensions that will relate to the facts. Identify the key performance indicators for each business process and decide the format to store facts in. Because the facts will ultimately be aggregated together to form OLAP cubes, the data needs to be in a consistent unit of measure.

**ETL:**        
The purpose of ETL (Extract, Transform and Load) is to provide optimized data loading processes without losing data quality. The ETL process takes the most time during development and consumes the most time during implementation. Identifying data sources during the data modeling phase can help reduce ETL development time. Failure at this stage of the process may lead to poor performance of the ETL process and the entire data warehouse system.


**Data Access phase:**          
In this we need to identify where the critical information is and how to move it into the data warehouse structure. Identify the different data sources and move it into the target. Need to move the data into a consolidated, consistent data structure. Transform the data as it move from one data structure to another. Need to plan when data movement will occur. While the system is accessing the data sources, the performance of those databases will decline.

Different Access Types are Selection, Drilling Down, Exception Reporting, Calculations, Graphics and Visualization, Data entry options, Customization, WebBased Reporting, BroadCasting.

**Deploy:**

Once the data is clean and approved and to have it available to final users we need to deploy it to further environments right from testing which use as the acceptance test and make it into the production. This is where we use latest versions to be considered to be deployed from one environment to another.



