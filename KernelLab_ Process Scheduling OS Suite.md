K

**KernelLab**OS Scheduler

Experiment modules

Authors Atharva Shinde (50)\
Bhumi Singh (51)

System Online · Practical OS Suite v2.5

Process Scheduling / **Scheduling Workbench**

👥 Authors: **Atharva (50) & Bhumi (51)**

OPERATING SYSTEMS · PRACTICAL PROJECT

# Interactive Process Scheduling

Designed and developed by **Atharva Shinde (Roll No. 50)** and **Bhumi Singh (Roll No. 51)**. Test custom workloads, configure time quanta, and analyze dispatching behaviors in real time.

STEP 01

## Process Queue & Workload Configuration

**0** processes · edit identifiers, arrival times and CPU bursts directly in the table.

| PROCESS ID | ARRIVAL TIME (AT) | CPU BURST TIME (BT) | WORKLOAD TAG | ACTION |
| --- | --- | --- | --- | --- |

💡 **Rule:** arrival times must be non-negative integers. Burst durations must be ≥ 1 unit.

STEP 02

## Simulation Control & Architecture

Choose a scheduling algorithm.

Time quantum (units) Qmin Qmax

### First Come, First Served (FCFS)

ACTIVE ALGORITHM

QUEUED PROCESSES

TIME QUANTUM

DISPATCH POLICY

🔒 Developed by Atharva Shinde (50) and Bhumi Singh (51). Client-side sandbox execution.

STEP 03

## Execution Output, Timeline & Metrics

Awaiting simulation execution. Configure the workload in Step 01, then run the simulation.

AVG WAITING TIME

0.00

Mean ready queue delay

AVG TURNAROUND TIME

0.00

Arrival to completion span

AVG RESPONSE TIME

0.00

Arrival to first CPU start

CONTEXT SWITCHES

0

Changes between processes

TOTAL CPU TIME

0

Cumulative burst allocation

CPU UTILIZATION

0.0%

Total burst ÷ max completion

### Visual Execution Timeline (Gantt Chart)

Color-coded breakdown of processor time slices. In DTQ-RR each slice shows the quantum (Q) of its round.

### Detailed Process Timing Metrics

Arrival (AT), Burst (BT), Completion (CT), Turnaround (TAT), Waiting (WT) and Response (RT).

| PROCESS | AT | BT | CT | TAT | WT | RT |
| --- | --- | --- | --- | --- | --- | --- |

**📐 Core mathematical formulas used in this lab**

`Turnaround Time (TAT)` = CT − AT

`Waiting Time (WT)` = TAT − BT

`Response Time (RT)` = First CPU Start − AT

`CPU Utilization` = (Total Burst ÷ Max Completion) × 100

`DTQ-RR Quantum` = clamp( round( mean remaining burst of ready queue ), Qmin, Qmax )

THEORY

# Core Concepts

CPU scheduling decides which ready process runs next. The choice of policy changes waiting time, response time and the number of context switches.

Non-preemptive

### First Come, First Served

Processes run in arrival order and keep the CPU until they finish.

- Simple, no starvation, minimum context switches.
- Convoy effect: a long job delays every short job behind it.
- Poor response time for interactive workloads.

Preemptive

### Round Robin

Each process gets a fixed time quantum, then goes to the back of the ready queue.

- Fair sharing and good response time.
- Too small a quantum causes many context switches; too large behaves like FCFS.
- The right quantum depends on the workload, and it is fixed in advance.

Preemptive · Adaptive

### Dynamic Time Quantum RR (DTQ-RR)

Round Robin where the quantum is recalculated at the start of every round.

- Quantum follows the mean remaining burst of the ready queue.
- Clamped between Qmin and Qmax so it never becomes too small or too large.
- As processes finish and remaining work shrinks, the quantum adapts, which reduces unnecessary preemptions.

```
Q = clamp( round(mean(rem)), Qmin, Qmax )
Qmin = 2, Qmax = 6

each round:
  Q = compute from ready queue
  for every process in the queue:
    run min(Q, remaining)
    if remaining > 0: requeue
```

ANALYSIS

# Comparative Analysis

Runs FCFS, Round Robin and DTQ-RR on the current workload from the Workbench, using the quantum settings you configured there.

| ALGORITHM | QUANTUM | AVG WT | AVG TAT | AVG RT | CONTEXT SWITCHES | UTILIZATION |
| --- | --- | --- | --- | --- | --- | --- |

### Average waiting time

PRESENTATION

# Presentation Deck

Use the arrow keys or buttons to move between slides.

Process Scheduling · Atharva Shinde (50) & Bhumi Singh (51) · Operating Systems Practical Lab