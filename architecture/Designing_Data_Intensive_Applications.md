Designing Data Intensive Applications by Martin Kleppmann
In this book, we focus on three concerns that are important in most software systems:

# Part I: Foundation of Data Systems

## Chapter 1: Reliable, Scalable, and Maintainable Applications

**Reliability**
The system should continue to work correctly (performing the correct function at the desired level of performance) even
in the face of adversity (hardware or software faults, and even human error).

**Scalability**
As the system grows (in data volume, traffic volume, or complexity), there should be reasonable ways of dealing with
that growth.

**Maintainability**
Over time, many different people will work on the system (engineering and operations, both maintaining current
behavior and adapting the system to new use cases), and they should all be able to work on it productively.

Operations teams are vital to keeping a software system running smoothly. A good operations team typically is
responsible for the following, and more:
• Monitoring the health of the system and quickly restoring service if it goes into a bad state
• Tracking down the cause of problems, such as system failures or degraded performance
• Keeping software and platforms up to date, including security patches
• Keeping tabs on how different systems affect each other, so that a problematic change can be avoided before it causes
damage
• Anticipating future problems and solving them before they occur (e.g., capacity planning)
• Establishing good practices and tools for deployment, configuration management, and more
• Performing complex maintenance tasks, such as moving an application from one platform to another
• Maintaining the security of the system as configuration changes are made
• Defining processes that make operations predictable and help keep the production environment stable
• Preserving the organization’s knowledge about the system, even as individual people come and go

## Chapter 2: Data Models and Query Languages

NoSQL databases have been adopted quickly and easily because:

* It provided a better scaling mechanism, including very high write throughput than relational databases
* It was free and open source
* It supported few specific query operations better than relational databases
* It provided more dynamic and expressive data model than relational databases

Relational databases deal with the one-to-many relationship in one of three ways:

* The common normalized way is to put the many values in a separate table, with foreign key reference to the one
* Later versions of SQL allowed multi-valued data be stored in a single row, with support for querying inside them
* The least favorable option is to store them as encoded JSON or XML, and let the application do the internal query

Document-oriented databases on the other hand supports one-to-many relationship natively, and provides better locality
for the data object, thanks to the self-contained nature of JSON.

Query Languages

* SQL is attractive to people due to its declarative nature, it specifies the pattern of the resulted data instead of
  the way of querying it. Also, declarative code is easier to parallelize across multiple machines.
* MapReduce is fairly low-level programming model for distributed execution, but it doesn't have a monopoly on
  distributed query execution.
* Graph data model is usually the most suitable model for data with a lot of many-to-many relationships. There are many
  well-known algorithms which can operate on graphs, and some good declarative query languages such as Cypher for
  efficient querying.
* Graph data model is different from network model in the way it gives much greater flexibility for applications to
  adapt.

One thing that document and graph databases have in common is that they typically don’t enforce a schema for the data
they store, which can make it easier to adapt applications to changing requirements. However, your application most
likely still assumes that data has a certain structure; it’s just a question of whether the schema is explicit (
enforced on write) or implicit (handled on read).

## Chapter 3: Storage and Retrieval

Comma-separated values (**CSV**) is a text file format that uses commas to separate values, and newlines to separate
records.

A **Bloom filter** is a memory-efficient data structure for approximating the contents of a set. It can tell you if a
key does not appear in the database, and thus saves many unnecessary disk reads for nonexistent keys.
Answers strict NO or probably yes.

Businesses usually have two types databases, online transaction processing (OLTP) for every-day transactions, and online
analytic processing for analytics purposes (Also known as Data Warehouse).

## Chapter 4: Encoding and Evolution
