## Lecture/Topic Index

| Week | Lecture #                                                                            | Summary                                                         |
| ---- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------- |
| 1.1  | [[3 - Literature Notes/Courses/CS 134/Lecture 1 (9-30-2024)\|Lecture 1 (9-30-2024)]] | Distributed System definition, examples, types, anatomy         |
| 1.2  | [[3 - Literature Notes/Courses/CS 134/Lecture 2 (10-2-2024)\|Lecture 2 (10-2-2024)]] | Fallacies, thought experiments, practicality                    |
| 2.1  | [[Lecture 3 (10-7-2024)]]                                                            | P2P architectures, Go, Concurrency, Race conditions             |
| 2.2  | [[Lecture 4 (10-9-2024)]]                                                            | RPC, failure-handling schemas, MapReduce                        |
| -    | [[Project 1]]                                                                        | MapReduce wc                                                    |
| 3.1  | [[Lecture 5 (10-14-2024)]]                                                           | Time sync, physical vs logical clocks, Lambert vs Vector clocks |
| 3.2  | [[Lecture 6 (10-16-2024)]]                                                           | ===clocks, execution delivery properties===                     |
| 4.1  | [[Lecture 7 (10-21-2024)]]                                                           | reliable, Replication, CDNs                                     |
| 4.2  | [[Lecture 8 (10-23-2024)]]                                                           | consistency models, GFS vs HDFS                                 |
| 5.1  | [[Lecture 9 (10-28-2024)]]                                                           | consensus, Paxos                                                |
| 5.2  | [[Lecture 10 (10-30-2024)]]                                                          | Paxos, replication, ==Raft==                                    |
| -    | Project 2                                                                            |                                                                 |
| 7.2  | [[Lecture 11 (11-13-2024)]]                                                          | ==Consensus, zookeepe=r=                                        |
| 8.1  | [[Lecture 12 (11-18-2024)]]                                                          | ==Containers and Docker, Kubernetes, GKE==                      |
| 8.2  | [[Lecture 13 (11-20-2024)]]                                                          | ==Transactions, Distributed Transactions: Two-Phase Commit==    |
| -    | Project 3                                                                            | Paxos                                                           |
## Readings

| Week | Reading (required)                                                                                           | Reading (reference)                                                                                                                                                                                                                                                                                                                                                                                                                             |     |
| ---- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| 1    | Vitillo Ch 1                                                                                                 | Steen Ch 1-2                                                                                                                                                                                                                                                                                                                                                                                                                                    |     |
| 2    | MapReduce paper                                                                                              | Kleppmann Ch 10<br>Steen Ch 3.1, 3.2-3.4 (less important) <br>Steen Chapter 4.1-4.3                                                                                                                                                                                                                                                                                                                                                             |     |
| 3    |                                                                                                              | Steen Ch 5.1, 5.2 <br>Vitillo Ch 8                                                                                                                                                                                                                                                                                                                                                                                                              |     |
| 4    | <br>[GFS paper](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf) | Steen Ch 7<br>Vitillo Ch 10 (see Raft leader election, Ch 9) Note that replication can be achieved many different ways. We are going to discuss Primary Backup and a couple of others for now. Vitillo requires assumes knowledge of Raft leader election (Chapter 9) which we have not discussed yet (it is in the Consensus lectures). It might give you some additional background but isn't directly related to the method we will discuss. |     |
| 5    |                                                                                                              | Steen Ch 8.1-8.2.4                                                                                                                                                                                                                                                                                                                                                                                                                              |     |

## Office Hours

|               | M   | T       | W      | R                                                | F           | Email                | Office        |
| ------------- | --- | ------- | ------ | ------------------------------------------------ | ----------- | -------------------- | ------------- |
| Prof. Rosario |     |         | 3:30-5 | [5:30-6:30](https://ucla.zoom.us/my/ryanrosario) |             | rrosario@cs.ucla.edu | Boelter 3531A |
| Jack          |     |         |        |                                                  | 10:15-12:15 | yiyaoyu@cs.ucla.edu  | Boelter 3278  |
| Arjun         |     | 12:30-2 |        |                                                  |             | arjuna5@g.ucla.edu   | Boelter 3286  |

## Grading
55% project
1. scratch MapReduce (low-lvl) in Go (intro)
2. primary/backup key-value service (not lose key-vals in nodes)
3. paxos-based key-value service (each node votes stale/new/ multi write version)
4. sharded key-value service (full distributed key-value service)
20% **open-note** midterm (Mon Nov 4 in class)
25% **open-note** final exam (Wed Dec 11, 8-11am)
## Textbooks
- course-boring-verbose (AFTER lecture): [Distributed Systems v4.02](https://www.distributed-systems.net/index.php/books/ds4/ds4-ebook/)
- high-lvl understanding (BEFORE lecture): [[Roberto Vitillo - Understanding Distributed Systems - 2nd Edition (2022).pdf | Understanding Distributed Systems]]
- future research papers (BEFORE lecture)
	popular, timeless fundamentals not newest cutting edge tech
- highly recommend for app-lvl data job: [Designing Data-Intensive Applications](https://learning.oreilly.com/videos/designing-data-intensive-applications/9781663728289/)
## Background Knowledge
- learn Go in this class, so python knowledge helps
- application lvl - http
- transport layer - TCP
- DNS - name resolution