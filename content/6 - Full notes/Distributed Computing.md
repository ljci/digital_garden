---
tags:
  - distributed_comp
date created: Sun, Aug 18th 2024, 10:02 pm
date modified: Sun, Nov 3rd 2024, 1:36 am
---

# Causal Procedure Relations

  ![[slide3.png]]
![[slide4.png]]

# Singhal–Kshemkalyani’s differential technique

![[slide2.png]]
{(1,1)} ->{{process index(p1),values=1}}, sent this value to $p_{2}$
When a process pi sends a message to a process pj , it piggybacks only those
entries of its vector clock that differ since the last message sent to $p_{j}$.

[Parallel Programming with MPI For Python - Research Computing in Earth Sciences](https://rabernat.github.io/research_computing/parallel-programming-with-mpi-for-python.html)

# MPI command

Run sample.py in localhost with 4 processors only
`mpirun -np 4 python3 ./sample.py`

copy sample.py to billy
`scp ./sample.py 73985@billy:C:/Users/73985/`

Run sample.py with 4 processors in localhost and 4 in billy
`mpirun -np 8 --host localhost:4,billy:4 python3 ./sample.py`

this one doesn't work on my mac
But we can also create `hosts` file with specified slots of processors