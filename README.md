# Performance Testing

**Abstract** - An Introduction to Performance Testing. An approach to performance testing is discussed. A case study using 
locustio to perform performance testing on a blog website is presented

**Index Terms** - Software performance testing, performance testing, software testing.

## 1. Introduction:

### a. Performance Testing Definition:

Performance testing is a testing technique, performed to determine the responsiveness and stability of 
a software system under various workload.
Performance testing metrics are scalability, reliability, resource usage. 
There are four primary type of performance testing: Load Testing, Stress Testing, Soak Testing, and Spike Testing. 
Performance testing is a non-functional testing [3].

### b. System Performance Degradation:

According to [1], system performance degradation or problems handling required system
throughput is an extremely significant issue for many large industrial projects. Although the software system has gone through
extensive functionality testing, it was never really tested to assess its expected performance [1].

During an architecture review at AT&T, a group of engineer have found that "performance issues
account for one of the three major fault categories. Performance problems identified might include
such things as the lack of performance estimates, the failure to have proposed plans for data collection, 
or the lack of a performance budget". They also claimed that insufficient planning for performance issues
is the major issues when the software deploy to the field [1].

Major issues are issues that will impact on user satisfaction.

### c. Uneven Distribution of Resource Usage:

Pareto-type distribution is also known as very uneven distribution of resource usage. The main reason for system performance degradation
is claimed distribution of project-affecting issues (Pareto-type distribution). According to [1], it was found that 70 percent of the most severe class of problems 
resided in the weakest 30 percent of the project.

## 2. Previous Work:

According to [1], The author doesn't find any adequate of performance testing knowledge on the Internet. He found out that "there is neither an
existing body of research literature nor an extensive collection of practical or experiential information available
to help testers faced with the prospect of doing software performance testing".

## 3. Performance Testing Tools:
### Locust IO:

Locust is an easy to use, scriptable and scalable performance testing tool. 
Instead of being constrained by a UI or domain specific language, Locust infinitely expandable and very developer friendly due to its code base tools.
Locust IO is required Python programming knowledge, and it is easy to use and develop test case.

**Write user test scenarios in Python code:**
If tester want the users to loop, perform some conditional behaviour or do some calculations. Locust runs every user inside its own greenlet (a lightweight process/coroutine)
which enables tester to write your tests like normal Python code (instead of using callbacks or other methods).
Tester can use any Python IDE, and version control tester's test script as regular code (as opposed to some other tools that use XML or binary formats)

**Distributed & Scalable - supports hundreds of thousands of users:**
Locust makes it easy to run load tests distributed over multiple machines. It is event-based which makes it possible for a single process to handle many thousands concurrent users.

**Locust Features:**
Running in Docker, distributed load generation, running test in a debugger, running Locust distributed with Terraform/AWS, running Locus automation
, retrieved test statistics in CSV format, testing non-HTTP systems, testing request base SDKs, increase performance with a faster HTTP client, event hooks,
logging, using locust as a library.

### Expertus:

Retrieved from [4], Expertus is designed to automate large scale distributed experiment studies in IaaS clouds with the goal of addressing three challenges:

**Experiment challenges:**
Performance testing for enterprise applications consists of multiple closely related scenarios by
varying a few configurable (preferably one) parameters at a time. 

**Application challenges:**
In distributed software testing the applications should start efficiently and in a provably correct order by simultaneously 
enforcing serialization constraints and leveraging the distributed system’s inherent parallelism.

**Cloud challenges:**
Selecting the most appropriate cloud from many cloud offerings is a non-trivial task. Also, migrating an application between
two clouds is a complex, time-consuming and error-prone task. Finally, communication, coordination, synchronization, monitoring and complete management challenges; lastly, the dynamic
nature of the cloud introduces extra complexity

## Testing website (blog) using Locust IO:

### Gather Requirement:
Application was design using Flask Framework, and Jinja Template (Python). 

Blog-Template was original designed by Dr. Angela Yu and implemented by Truc Huynh. 
Application is a blog that required user register to edit or comment on a post. 
Only the admin can create , edit or delete post. Application was host at heroku.com, and the hyperlink is "https://template-blog.herokuapp.com/".

The Blog-Template was designed as a template blog and post on GitHub by Truc Huynh ("https://github.com/jackyhuynh/blog-template").
Anyone can use the blog for any purpose. 

### Test Plan Design:

<img src="images/test-suite.PNG">





### 
```bash
2022-03-10T17:00:41Z
[2022-03-10 12:00:41,483] DESKTOP-J4K30PB/INFO/locust.main: Shutting down (exit code 1)
 Name                                                                              # reqs      # fails  |     Avg     Min     Max  Median  |   req/s failures/s
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 GET //contact                                                                       1095     1(0.09%)  |     120      27   19214     130  |    0.81    0.00
 POST //login                                                                        1000     0(0.00%)  |     144     114    1134     140  |    0.74    0.00
 GET //post/1                                                                        5162     4(0.08%)  |     125      28   25672     140  |    3.83    0.00
----------------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 2                  GET //post/1: ConnectionResetError(10054, 'An existing connection was forcibly closed by the remote host', None, 10054, None)
 2                  GET //post/1: RemoteDisconnected('Remote end closed connection without response')
 1                  GET //contact: ConnectionResetError(10054, 'An existing connection was forcibly closed by the remote host', None, 10054, None)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 Name                                                                              # reqs      # fails  |     Avg     Min     Max  Median  |   req/s failures/s
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 GET //contact                                                                          1     0(0.00%)  |      42      42      42      42  |    0.01    0.00
 POST //login                                                                          10     0(0.00%)  |     162     137     181     160  |    0.05    0.00
 GET //post/1                                                                          18     0(0.00%)  |     106      40     194      66  |    0.09    0.00
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 Aggregated                                                                            29     0(0.00%)  |     123      40     194     150  |    0.15    0.00

Response time percentiles (approximated)
 Type     Name                                                                                  50%    66%    75%    80%    90%    95%    98%    99%  99.9% 99.99%   100% # reqs
--------|--------------------------------------------------------------------------------|---------|------|------|------|------|------|------|------|------|------|------|------|
 GET      //contact                                                                              42     42     42     42     42     42     42     42     42     42     42      1
 POST     //login                                                                               170    170    170    170    180    180    180    180    180    180    180     10
 GET      //post/1                                                                               69    170    170    170    180    190    190    190    190    190    190     18
--------|--------------------------------------------------------------------------------|---------|------|------|------|------|------|------|------|------|------|------|------|
 None     Aggregated                                                                            150    170    170    170    180    180    190    190    190    190    190     29

```

## C. Advantages/Disadvantage
### Advantage:
- Verifies the speed, accuracy, and stability of the software match expectation.
- Assists the system by authenticating the responsiveness and managing the scalability and reliability of software features.
- Retrieved from (14)

### Disadvantage:
- Can be a costly mistake if done haphazardly, leading to inaccurate results and conclusions.
- Carried out on multiple devices in different locations to check whether a user faces difficulties. Hence, this testing can be costly.
- Retrieved from (14)

## D. Applications:
- Performance testing should be performed for any kind of applications since we all want to know how our application is performed. 
We can guarantee the software applications can handle and manage the workload efficiently

## E. Reference:

E. J. Weyuker and F. I. Vokolos, "Experience with performance testing of software systems: issues, an approach, and case study," in IEEE Transactions on Software Engineering, vol. 26, no. 12, pp. 1147-1156, Dec. 2000, doi: 10.1109/32.888628. [1]

D. Jayasinghe et al., "Expertus: A Generator Approach to Automate Performance Testing in IaaS Clouds," 2012 IEEE Fifth International Conference on Cloud Computing, 2012, pp. 115-122, doi: 10.1109/CLOUD.2012.98. [4]

Kumar. K., "Write your first performance/load test in Python.", Retrieved from https://medium.com/@kundan3034/write-your-first-performance-load-test-in-python-e8e2132ef775 [2]

Tutorial Points (n.d.), "Performance Testing", Retrieved from https://www.tutorialspoint.com/software_testing_dictionary/performance_testing.htm [3]
 
Bystron. C.,  Heyman. J., Hamren J., Heyman. H. and Holmberg. L., Locust, Retrieved from https://github.com/locustio/locust [5]

Retrieved from http://docs.locust.io/en/stable/running-without-web-ui.html#