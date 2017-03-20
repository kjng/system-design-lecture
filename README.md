# System Design Lecture Notes

These notes were prepared for a lecture given at **Hack Reactor** on **System Design**. It aims to provide outlines and guidelines for answering system and software architecture-based questions in a coding interview. Most of this information is based on [hiredintech's](https://www.hiredintech.com/classrooms/system-design/) System Design free online course.

## TODOS:
- Create diagrams/images of:
   - Constraints and use cases (bitly?)
   - Abstract design (bitly?)
   - Scalability (bitly?)

## Challenges
- How can I design x in y minutes?
- The point of system design questions are to create a discussion of the problem at hand and the process in which you solve the problem.
- Usually, the outcome is a high-level architecture addressing the goals and constraints of the problem. This may lead to further discussion of bottlenecks.

## Guidelines
- Break down the problem, whether it appears simple but with many underlying layers, or complex and you don't know where to begin.
- There is no right answer, but the interviewer may be guided towards high-level architecture or a few specific areas. Let's go over some strategies...

## System Design Process

- Don't jump in immediately! Knowing the problem at hand is important

- Clarify what the system needs to satisfy. Ask your interviewer for a few minutes on the use cases, constraints, and scope of the system. This is similar to algorithm questions and OICE.

- The interviewer wants to eventually see if you can solve the problem, but before that, whether or not you can gather the requirements of the problem

1. Constraints and use cases
2. Abstract Design
3. Analyze Bottlenecks
4. Scale Your Design

### Quiz

Link [here](system-design-process-quiz.md)

### Example: Design a url shortening service, like bit.ly

- How many users? With a few thousand users, this could amount to millions of URLs. Do you want statistics for each link (clicks, timestamp, etc...)?
- Understand the problem better!

#### Use cases (what it should do, verify with interviewer):
- Shortening a long url to a much shorter version
- Redirecting from a short url to a long url
- Custom url
- Analytics
- Automatic link expiration
- Manual link deletion
- UI vs API

#### Constraints:
- How many URLs per month/per second? (Interviewer: top 10 url shortener site, - but not top 3)
- Twitter was a driver for url shortening (15 billion tweets per month)
- 1.5 billion total shortened (one of the large players, 100 million urls each - month)
- How many requests? Links are created then maybe not clicked on after a couple - weeks. Maybe 1 billion requests per month
- 10% shortening, 90% redirecting
- Don't give up if you don't have the right numbers, demonstrate that you're - thinking about these things and the interviewer will guide you
- Requests per second: 400+
- Total urls in 5 years X 12 months X 100 million = 6 billion
- Urls are 100 to 1000 characters: typical 500 characters => 500 bytes
- Alphabet/number/symbol consideration for url hashes
- Can go more in detail to storage space for all data, data size read per second

#### Abstract design
- Outline all the important components your architecture will need
- Draw a simple diagram with components and the connections
- Don’t deep dive at this point and get some feedback from the interviewer if - this is the right direction
- Justify your ideas from your notes about use cases/constraints
- At this point, don’t decide on the specific technologies, just outline the - high-level components
- Components:
- Application service layer (serves the request)
- Shortening service: generate hashes until one isn’t used the map them, if - given custom url, check that it hasn’t been used and create it
- Redirection service: look up hash and send a redirect
- Data storage layer (keeps track of the hash => url mappings)
- Database to store new mappings and retrieve urls when given a hash
- Hashing
- Use bcrypt to hash the url then take the first 6 characters or so

#### Analyzing Bottlenecks
- Your high-level design will have places of potential overload
- The task is to make your design scalable
- Several buzzwords:
   - Load balancer
   - Distributed data across multiple data stores (or not)
   - Database replication
   - Database partitioning/sharding
   - Etc...
- Remember that solutions almost always have trade-offs, so you should point these out as you’re designing the system

- **Example Thoughts:**
   - Lots of requests a second
   - Requests are small in size and inexpensive
   - How much data is written and read per second
   - How to quickly look up url? We shouldn't scan the entire data store (linear search)

#### Scaling your abstract design
- After all the steps above are OKed by your interviewer, now is the time to make it more detailed. Keep scalability in mind.

#### Summary:
- Scope the problem
- Sketch an abstract design
- Think about bottlenecks
- Address the bottlenecks with scalable system design

#### Scalability
- How do we know what steps need to be taken? Afterall, not many engineers - actually get to work with systems that serve hundreds of millions of users
- Here’s some things to think about:
- Vertical scaling (get more resources/money)
   - CPU
   - RAM
   - Constraints: a limit to how many cores/processor speeds/world hasn’t made a more powerful machine/your money
   - **Example:** One web server your users connect to that handles all of your requests/responses and your database(s)
- Horizontal scaling
   + Since vertical scaling is expensive and has a limit, let's architect a system where we split up one machine into several
   + We can then buy cheaper machines and achieve almost no limits in terms of expandability since we aren't limited by industry technology
   + **Example:**
      + We can buy a machine that has 4 processors in it with 64GB of RAM and hundreds of TB of disk space but buying more speed/storage may not even be possible.
      + We can instead create a system design where we can buy several 1 processor machines with 4GB of RAM and 1TB disk space.
   - There are, of course, tradeoffs. There will be increased latency the more machines you have but if your 1 machine system reaches peak capacity, horizontally scaling is definitely better.
- Load balancing
- Caching
- Database replication
- Database partitioning
- Web hosts, VPS, Amazon EC2
