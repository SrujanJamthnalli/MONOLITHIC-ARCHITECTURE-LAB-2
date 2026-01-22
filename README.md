# MONOLITHIC-ARCHITECTURE-LAB-2
# CC LAB 2 – Monolithic Architecture

**SRN:** PES1UG24AM814  
**Course:** Cloud Computing Laboratory  

---

## 1. Description
This repository contains the implementation of a monolithic FastAPI application designed to explore the characteristics, failure points, and optimization strategies inherent to monolithic architectures. 

The lab focuses on identifying performance bottlenecks—specifically "artificial" and inefficient loops—that mimic technical debt or poor logic in a real-world system. By using **Locust** for load testing, we observe how these bottlenecks degrade system performance and how targeted refactoring restores efficiency.

---

## 2. Optimizations Performed

The core of this lab involved refactoring three critical routes to eliminate unnecessary CPU overhead and reduce response latency.

### `/checkout`
* **The Problem:** Used a repetitive, loop-based approach to calculate total fees, leading to $O(n)$ complexity.
* **The Fix:** Optimized the logic by removing the loop and using a direct calculation method.
* **The Result:** Faster transaction processing and improved average response times.

### `/events`
* **The Problem:** Contained an artificial CPU-intensive loop that consumed resources without providing any functional value.
* **The Fix:** Completely removed the redundant computation, leaving only essential database operations.
* **The Result:** Drastic reduction in response time and increased throughput.

### `/my-events`
* **The Problem:** Included an artificial computation loop that increased CPU utilization unnecessarily.
* **The Fix:** Excised the loop to ensure the route only handles data retrieval and template rendering.
* **The Result:** Noticeable improvement in route performance and system stability under load.

---

## 3. Load Testing & Performance
To validate these optimizations, the application was subjected to load testing using **Locust**. 
* **Baseline:** High latency and CPU saturation due to inefficient loops.
* **Post-Optimization:** Significant decrease in average response time (ms) and a higher number of Requests Per Second (RPS) handled successfully.

---

## 4. How to Run

Follow these steps to set up and execute the monolithic application:

### Environment Setup
```bash
# Create a virtual environment
python -m venv .venv

# Activate the environment
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt
