Credits to: [hiredintech](https://www.hiredintech.com/classrooms/system-design/lesson/96)

------

**1. Imagine a system in which many users request various files with source code to be executed against a set of test cases and want to see the results in real time. The system has a few servers to serve web pages through which users send their source code. There is a load balancer in front of these machines. The servers also use very quick queries to a database to store the source code execution results for each user. Each server sends requests to a single machine executing the source code files from a queue. What is the biggest bottleneck in this high-level design that needs to be addressed?**

* The one single machine executing source code solutions

Explanation:
The question description tells us that the database doesn't seem to be loaded by the queries and a good load balancer should be able to distribute a lot of queries to a few servers. A more major concern is the single machine that will perform relatively heavy work - compiling and executing source code against many test cases.

------

**2. Let's say that you were given the following question at an interview: "Design a system which allows its users to find web pages matching search terms that the user types. It must be able to handle sets of pages that have up to 10,000,000 pages in them". Considering that this design question is quite vague in its description what are suitable clarification questions to ask the interviewer? Check all answers that are true.**

* What kinds of web pages will the system search through - with text, images, video, etc?
* What are the expected load and distribution of the search queries?
* Should the search terms match exactly terms in the web pages or we will need some sort of fuzzy matching, too?

Explanation:
When asking clarification questions you should be getting information about the requirements for the problem. Try not to ask questions, which you should give the answers to. For example, in this question, you will probably have to suggest the algorithm for matching search terms to web pages. Also, the structure of the data is something that you will have to come up with.

------

**3. Let's say that you are in the middle of a system design interview and you have outlined a high-level design solution for the problem you were given. In such a situation which of the following things are RED FLAGS that something is not right with this design and that it must be reconsidered?**

* With the current design the system would need to use tons of memory in order to be able to handle the number of requests defined by the interviews. This is a trade-off that the interviewer does not want to make.
* The system would NOT be able to guarantee data consistency for all expected users while this is a critical requirement from the interviewer.

Explanation:
If your high-level design has bottlenecks or other problem that can be overcome without making impossible trade-offs then the design is probably solid. However, if it has issues that violate some of the problem constraints and you cannot come up with a good way to resolve them then perhaps you should look for another high-level design solution.

------

**4. Once you feel like you have all the information needed to start working on a system design question at an interview which of the listed things is a suitable way to continue?**

* Try to sketch out the main components of the system at the high level. Maybe draw some diagrams but without too many details.

Explanation:
In the system design process that we describe in this course you will see that first we suggest to start with the high-level design, talk over it with the interviewer, make sure it looks good and only then delve into more details.