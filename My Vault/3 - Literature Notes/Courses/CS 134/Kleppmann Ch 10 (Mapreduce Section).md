## 
- not assume.1 database in sys
- Cache, data store, index, etc. all kinds of data systems models optimizations into 1 cohesive structure
- Systems of record (source of truth)
  - Authoritative, first written and resolver of disparate
  - Exactly-once (normalized)
  - 
- Derived data systems
  - Transforming original data in some way
  - Recreatable from original source
  - I.e. cache
  - Redundant in nature
  - Denormalized, diff POV 
- Most systems not strictly one or another, just a tool used for either

CH10: batch-oriented principles for large-scale data systems
- ask for something, system responses (web servers, caches, etc.)
- Assumes human request so reduce wait time
- Services - waits for client request and handles asap, perf=response time, availability essential
- Batch-processing sys - periodically scheduled not human request. Perf=thruput 
- Stream-processing: near resl-time, like batch in not response but short time not fixed predefined set of data, so lower latency

- batch-processing essential teaching tool
- Very old form of computing (punch-card tabulating machines) for aggregate stats on large data
- ruby vs Unix implementation: ruby hashes occurrences, Unix sorts. 
  - Ruby: hash table only scales to # of distinct urls even 1k occurrences
  - Unix: sort advantage of disks, sort segments and merge (spill to disk if > men by default in Unix)
Unix philosophy
- Pipe philosophy of garden hose, I/O 
- Each program does one thing well
- Expect output of one program to be concise enough for versatile input to another unknown program
- Try simple building quickly
- Rebuild if necessary, automation
- sort is great example, better than most other programming language libraries
  - Only powerful when paired with other tools
- Uniform interface for seamless input/outputs 


