1. Imagine a system in which many users request various files with source code to be executed against a set of test cases and want to see the results in real time. The system has a few servers to serve web pages through which users send their source code. There is a load balancer in front of these machines. The servers also use very quick queries to a database to store the source code execution results for each user. Each server sends requests to a single machine executing the source code files from a queue. What is the biggest bottleneck in this high-level design that needs to be addressed?

* The database storing the source code executions
* The load balancer in front of the servers serving web pages
* The one single machine executing source code solutions

------

2. Let's say that you were given the following question at an interview: "Design a system which allows its users to find web pages matching search terms that the user types. It must be able to handle sets of pages that have up to 10,000,000 pages in them". Considering that this design question is quite vague in its description what are suitable clarification questions to ask the interviewer? Check all answers that are true.

* What kinds of web pages will the system search through - with text, images, video, etc?
* What are the expected load and distribution of the search queries?
* How should I structure the data needed to match pages to search queries?
* Should the search terms match exactly terms in the web pages or we will need some sort of fuzzy matching, too?
* What will be the algorithm, which matches search terms to web pages?

------

3. Let's say that you are in the middle of a system design interview and you have outlined a high-level design solution for the problem you were given. In such a situation which of the following things are RED FLAGS that something is not right with this design and that it must be reconsidered?

* The solution has a bottleneck, which could be resolved by adding a load balancer that handles the incoming user requests and distributes them to a number of machines
* With the current design the system would need to use tons of memory in order to be able to handle the number of requests defined by the interviews. This is a trade-off that the interviewer does not want to make.
* The system would NOT be able to guarantee data consistency for all expected users while this is a critical requirement from the interviewer.
* The database used in the design won't be able to respond as quickly as needed to all incoming queries. However, the requirements are such that allow you to cache the responses to most of the queries and this would alleviate the load on the database significantly.

------

4. Once you feel like you have all the information needed to start working on a system design question at an interview which of the listed things is a suitable way to continue?

* Take the most challenging part of the system and try to design every important aspect of it. Perhaps even consider writing some code to illustrate your ideas.
* Try to sketch out the main components of the system at the high level. Maybe draw some diagrams but without too many details.
* If there is a database involved think about what type of technology you will use and design the schema that will be used to store your data.