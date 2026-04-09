# First NoSQL Database 🗄️

The detailed steps for this lab can be seen clearly in the folder titled **Lab Steps Screenshots**.

## What This Lab Is About

In this lab, I worked with **Amazon DynamoDB**, which is AWS's serverless NoSQL database service. According to AWS, Amazon DynamoDB is a fully managed, serverless database that scales automatically and requires no maintenance windows, patching, or downtime. Unlike traditional relational databases, DynamoDB has a flexible schema, meaning each item in a table can have different attributes without needing to redefine the table structure every time your data changes.

## Creating the Table and Adding Items

I started by creating a DynamoDB table called **UserVideoHistory**. When creating a DynamoDB table, you have to define a **partition key** and a **sort key**, which together form the primary key that uniquely identifies each item. I set `userId` as the partition key (String type) and `lastDateWatched` as the sort key (Number type) and used the default table settings. Once the table status showed as **Active**, I created my first item with the following attributes:

- **userId:** `12345-abcd-6789`
- **lastDateWatched:** `1740086439` (a UNIX timestamp)
- **videoId:** `9875-djac-1859`
- **preferredLanguage:** `en-US`
- **supportedDeviceTypes:** a List attribute containing `Amazon Fire TV` and `Amazon Fire Tablet`

After creating the item, I went back and edited it to add one more attribute called **lastStopTime** with a value of `90`, which represents how many seconds into the video the user stopped watching. This demonstrated one of DynamoDB's biggest strengths, which is that you can add new attributes to existing records at any time without affecting any other items in the table.

## Querying and Scanning the Table

The last part of the lab was about retrieving data from the table using two different operations. First I used a **Query**, which is the more efficient option because it looks for items using a specific partition key value. I queried for `userId = 12345-abcd-6789` with a sort key condition of `lastDateWatched greater than 1740086438` and the correct record was returned. I also tested querying with a partition key that does not exist (`abd5-zxcg-12385`) and nothing was returned, which confirmed that Query only finds exact partition key matches. I then used a **Scan** operation, which reads every single item in the table and returns all of them. According to AWS, Scan is less efficient than Query because it goes through the entire table, but it is useful when you need to retrieve all items regardless of their keys.

## What I Learned

This lab showed me how DynamoDB differs from traditional relational databases. There is no fixed schema to worry about, you only pay for what you use, and the table automatically handles replication across multiple Availability Zones for high availability. The difference between **Query** and **Scan** is also an important concept, because in a real world application with millions of records, always using Scan instead of Query would be very costly and slow. 🎉
