## Lecture/Topic Index

| Week | Lecture #                                                                                     | Summary                                                 |
| ---- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| 1.1  | [[My Vault/3 - Literature Notes/Courses/CS 134/Lecture 1 (9-30-2024)\|Lecture 1 (9-30-2024)]] | Distributed System definition, examples, types, anatomy |
| 1.2  |                                                                                               |                                                         |
|      |                                                                                               |                                                         |
## Readings

| Week | Reading (required)                                                                                                                                                       | Reading (reference)                                                                 |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| 1    | Vitillo Ch 1                                                                                                                                                             | Steen Ch 1-2                                                                        |
| 2    | MapReduce paper                                                                                                                                                          | Kleppmann Ch 10<br>Steen Ch 3.1, 3.2-3.4 (less important) <br>Steen Chapter 4.1-4.3 |
| 3    | Steen Ch 5.1, 5.2 <br>Vitillo Ch 8                                                                                                                                       |                                                                                     |
| 4    | Steen Ch 7<br>Vitillo Ch 10 (see Raft leader election, Ch 9)<br>[GFS paper](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf) |                                                                                     |

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