# Questions a Data Engineer has to answer
Some data engineering interview prep questions and scenarios. Answers might come later :)

Any PRs are welcome.

## Questions

* MapReduce
  * What is map-reduce programming model?
  * When and why would you use and? When and why not?
  * Is it limited to some specific programming frameworks?
  * If there're no libraries or frameworks implementing this model are currently available, provide a high-level description, how would you implement it for a case of processing of several hundreds of thousands files of 10MB on average. Feel free to use a development stack you are familiar with (Python/NodeJS/Java/etc).
  * What are considerations of acquiring data from an sql database (take PostgreSQL or MySQL for reference) with an MR approach?
  * What are the approaches you use to test your MR-oriented code?

* Relational databases
  * What are OLTP and OLAP databases?
  * Your query runs for too long, what are the first steps to take?
  * Under which circumstances can indexes slow down your queries?
  * You have to migrate lots of data from some data source into your relational DB (take MySQL or PostgreSQL for reference). What things should you consider when preparing the migration?

* NoSQL databases
  * Why and when to use NoSQL? 
  * What are the common NoSQL database types?
  * Explain the difference between K/V and Document databases? Bring some examples from your knowledge or experience.
  * Sharding and replication? Common scenarios?
  

## Scenarios

### Customer data processing

Your company has to store and process customer document. Each customer usually has between 1 and 100 documents. Overall volume of data is around 300TB. The documents are stored in S3 (what changes if we use HDFS? Windows share? FTP?). The keys of the documents look like `/<creation_year>/<creation_month>/<creation_day>/<document_id>`. The `document_id<->customer_id` mapping is stored in a separate relational database. This naming scheme was chosen due to an internal process working on files in date-split chunks. Eventually the business representative comes with a request to enable per-customer data processing. The code to process customer data is provided to you by the business representative, it requires the files to be delivered to a local drive into a folder and it takes about an hour to process. How would you approach orchestrating of running of the customer processing code?
