# Lecture 7
Recommend some papers
What is good list of papers? Canonical 
- 2024 - most important list
- Hackernews list older
- Consensus
- Industrial papers vs original maybe easier for you to understand, more practical

All Cloud service have some Data processing library (i.e. mapreduce ) 
- distributed replicated file system (GFS, HDFS/Hadoop, Azure’s, AWS) 
  - In all large companies ,  distrib. Replicated file sys, databases, storage, querying layers, cluster manager, job scheduler, etc.
  - Workflow essential to grasp
- Data processing
  - Batch processing
  - Stream processing (not on disk too fast)
  - Storage layer
  - Orchestration layer

Previously : reliable delivery ORDER (total order, causal, etc.)
- now we focus on if delivered at all
- Enforce properties how? Causal examples tedious (1. Hr vector clocks)
- Total order delivery - for future
- RELAIBLE delivery:
  - a liveness property: what needs guaranteeing
  - Crash failure: specific omission failure 
    - Process/node crashes forever, what to do? 
  - Omission failure: A —> B,  B never sends response to A
    - Either Ack from B to A lost
    - Or B never got it (can’t tell which)
    - Or B crashed/stops responding entirely
- not all ___ fail so we can lose transmission but not message and eventually deliver upon retries 9:40 if neither node crashes and not all msgs lost
- Keep retrying until get Ack —> then unbuffer the msg (like a commit)
  - What is the timeout period? We need to learn it eventually over time from experience? Realistically just fixed value
  - If timeout period too small: tons of msgs but minuscule difference as to outcome (if not receive email reply in 1 hr, unlikely in 2 hr etc)
  - Too long: very little progress lots of blocking less working 
- If Acks from B lost
  - Keep retrying - problem? Depends if idempotent
  - Considering two generals ex. “Attack at dawn” received twice no problem
  - Idempotent operation: “write x=2”. Vs not (increment x)
    - F(x)==f(f(f(f(f(…f(x)))))
    - I.e. abs value, x, sign(x) identity matrix, etc.
- Cannot assume reliable like in FIFO example
- Reliable = at-least-once delivery (so needs to be idempotent)
- At-most-once: only sends it once no matter what happens don’t retry
- Exactly once: unrealistic on real async system i.e. latent
  - Some however guarantees this: LIE marketing hopefully get away with it
  - Tradeoffs too or trackings in wording KAFKA (msg broker), BEAM
  - Actually: assume 2 things to guanrantee these
    - Msgs are idempotent (at-least-once)
    - Server de-duplicates messages (drop the rest), at most once
    - Combined: exactly once SIMULATION not exactly.          

Broadcast: to everyone. Including itself (ignore) 
- Causal broadcast to avoid order anomaly (use buffer to avoid showing out of order message first carol dumb bob example )
- Reliable delivery: crash model = as long as no crash okay, not care message model. Omission model: cares about message model 
- Byzantine model: corruption. Snooping etc man middle attacks  safety definition depends on threat model

Crash model—>reliable broadcast
- If a broadcasts to b and c and c crashes at any time, a is “correct”, b is “correct”, c is not because it crashed
- Reliable 