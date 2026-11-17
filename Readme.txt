## 12. Steps to Reproduce the Experimental Evaluation

The following steps describe the experimental workflow used to evaluate the TRACER framework.

### Step 1: Set Up the Kubernetes Environment
- Configure one Kubernetes control-plane node and four worker nodes.
- Install Ubuntu 22.04 LTS.
- Install Kubernetes v1.28 and containerd 1.7.
- Configure the worker nodes with 8 vCPU and 16 GB RAM each.

### Step 2: Configure Monitoring
- Install Prometheus 2.48.
- Configure node and container resource monitoring.
- Set the metrics collection interval to 5 seconds.

### Step 3: Configure the TRACER Controller
- Implement the external controller using Python.
- Configure the scheduling cycle to 1 second.
- Set the prediction, trust, and utility parameters using `tracer_parameters.csv`.

### Step 4: Deploy the Workloads
Deploy the following workload types:
- AI inference using DistilBERT.
- Planning using LangChain.
- Containerized tool execution.
- Multi-stage agentic workflows.

Refer to `workload_configuration.csv` for the reported resource requests and limits.

### Step 5: Configure Experimental Scenarios
Prepare the following scenarios:

1. Normal workload.
2. Resource contention using stress-ng.
3. Burst workload.
4. Node and container failures using Chaos Mesh.

Refer to `scenario_configuration.csv` for the scenario details.

### Step 6: Configure Baseline Schedulers
Evaluate TRACER against:
- Default Kubernetes Scheduler.
- Resource-Based Scheduler.

Use the same experimental conditions and random seeds for each scheduler.

### Step 7: Execute the Experiments
For each scenario and scheduler:
- Perform a 5-minute warm-up period.
- Run the measurement period for 10 minutes.
- Conduct 10 independent experimental runs.

### Step 8: Evaluate Performance Metrics
Evaluate the following metrics:
- Task Completion Rate.
- P95 Latency.
- SLA Violation Rate.
- Failure Rate.
- Resource Utilization.
- Migration Frequency.
- Recovery Time.

The SLA threshold is 4.0 seconds.

### Step 9: Analyze the Results
- Use `scenario_results.csv` to inspect the reported scenario-wise performance.
- Use `ablation_results.csv` to compare the prediction-only, trust-only, and full TRACER configurations.
- Compare the results of TRACER with both baseline schedulers.

### Step 10: Interpret the Results
The reported results indicate that TRACER achieves improved task completion, lower P95 latency, fewer SLA violations, reduced failures, and faster recovery compared with the baseline schedulers.

**Reproducibility Note:** The repository provides summary experimental results and configuration details. 