# CPU-Scheduling-Algorithms
A C++ implementation of multiple CPU scheduling algorithms, including First Come First Serve (FCFS), Round Robin (RR), Shortest Process Next (SPN), Shortest Remaining Time (SRT), Highest Response Ratio Next (HRRN), Feedback (FB), and Aging.  

---

## 📚 Table of Contents
- CPU-Scheduling-Algorithms
   - [Algorithms](#algorithms)
        - First Come First Serve (FCFS)  
        - Round Robin (RR)  
        - Shortest Process Next (SPN)  
        - Shortest Remaining Time (SRT)  
        - Highest Response Ratio Next (HRRN)  
        - Feedback (FB)  
        - Feedback with varying time quantum (FBV)  
        - Aging 
   - [Installation](#installation)
   - [Input Format](#input-format)

---

## 🧠 Algorithms

### 1. First Come First Serve (FCFS)
- **Type:** Non-preemptive  
- **Description:** Executes processes in the order they arrive. Can lead to poor performance if long processes block short ones.  
- **Use Case:** Batch systems.

### 2. Round Robin (RR)
- **Type:** Preemptive  
- **Description:** Time-sliced scheduling with adjustable quantum (`q`). Shorter processes can get smaller quanta. Prevents starvation and improves fairness.
- **Use Case:** Time-sharing systems with better flexibility.

### 3. Shortest Process Next (SPN)
- **Type:** Non-preemptive  
- **Description:** Executes the process with the shortest burst time next. Good for minimizing average waiting time.
- **Use Case:** Systems optimizing for average waiting time.

### 4. Shortest Remaining Time (SRT)
- **Type:** Preemptive  
- **Description:** Chooses the process with the shortest remaining time. Can preempt a currently running process.
- **Use Case:** Interactive systems with variable process times.

### 5. Highest Response Ratio Next (HRRN)
- **Type:** Non-preemptive  
- **Description:** Chooses the process with the highest response ratio: = Waiting Time + Service Time / Service Time
- **Use Case:** Fair scheduling without starvation.

### 6. Feedback (FB)
- **Type:** Preemptive  
- **Description:** Uses multiple queues and promotes/demotes processes based on behavior. Higher priority queues are served first.
- **Use Case:** Mixed process types with aging and fairness.

### 7. Feedback with Varying Time Quantum (FBV)
- **Type:** Preemptive  
- **Description:** Similar to FB, but with increasing time quantums for lower queues. Helps balance responsiveness and fairness.
- **Use Case:** Increased control over scheduling fairness and efficiency.

### 8. Aging
- **Type:** Preemptive  
- **Description:** Prevents starvation by increasing the priority of waiting processes over time. Inspired by Xinu OS.
- **Use Case:** Real-time systems needing fairness.
---

## ⚙️ Installation

```bash
# 1. Clone the repository
git clone https://github.com/your-username/CPU-Scheduling-Algorithms.git
cd CPU-Scheduling-Algorithms

# 2. Install required tools
sudo apt-get install g++ make

# 3. Compile the code
make

# 4. Run the program
./scheduler
```

## 📝 Input Format
Line 1: "trace" or "stats" – Mode of execution.

Line 2: Comma-separated list of scheduling policies and their parameters.

Example: 1,2-4,8-1

1 → FCFS

2-4 → RR with quantum = 4

8-1 → Aging with quantum = 1

Line 3: Simulation time (last time instant on timeline).

Line 4: Number of processes.

Line 5 onwards: Process description (one per line).

For Algorithms 1-7 (FCFS to FBV):
Each process line:

``` <ProcessName>,<ArrivalTime>,<ServiceTime> ```

For Algorithm 8 (Aging):
Each process line:

``` <ProcessName>,<ArrivalTime>,<Priority> ```

Processes are sorted by arrival time.
If arrival time matches, the lower-priority process is considered first.
