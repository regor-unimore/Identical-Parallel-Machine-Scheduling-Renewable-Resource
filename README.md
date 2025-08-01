# Energy-Constrained-Identical-Parallel-Machine-Scheduling

This dataset contains instances for the study of parallel machine scheduling with a single renewable resource constraint. Two different sets of instances are provided. The first set includes the original instances from [1]. For our case of identical machines, we consider only the processing times and resource requirements corresponding to machine 0. The second set consists of adapted instances based on the exact methods studied in [2], where the fixed energy consumption of idle machines has been removed.

## 1. INSTANCE NAMING

### FIRST SET OF INSTANCES
Files are named as: NxM_Progr_Proc_R_Res.txt, where:
- N: indicates the number of jobs;
- M: indicates the number of machines;
- Progr: is a progressive index identifying the instance;
- Proc: identify the original method used to set processing times;
- R;
- Res: identifies the original method used to set the amount of resources used. 

Example: 8x6_4_JobCorre_R_inter_.txt corresponds to 8 jobs, 6 machines, is the 4th instance of the group, processing times are beign set to be correlated and resources are set in the inter way.

### SECOND SET OF INSTANCES
Files are named as: NxM_Energy_Progr.txt, where:
- N: indicates the number of jobs;
- M: indicates the number of machines;
- Energy: identifies whether the maximum level of energy available is hig or low; 
- Progr: is a progressive index identifying the instance.
  
Example: 5x2_high_3.txt corresponds to 5 jobs, 2 machines, high energy limit, and is the 3rd instance of the group.


## 2. INSTANCE FILE FORMAT
Instances of both set are built the same way. Each instance file is organized as follows:
- int number of jobs;
- int number of machines;
- int number of stages (always equal to 1);
- int number of machines (repeated);
- matrix [N][2M] Processing times: There is one row per job, which contains:
  - int machine index;
  - int processing time on that machine.
  Example:
  0 72 1 72
  Means that the job can be assigned to machine 0 with processing time 72, and to machine 1 with processing time 72.
- string Resources;
- int number of resources (always 1);
- string resource name (always R0);
- int resource limit (maximum available amount);
- matrix [N][2M] Resource requirements: There is one row per job, which contains:
  - int machine index;
  - int resource requirement on that machine.
  Example:
  0 12 1 12
  Means that the job can be assigned to machine 0 with resource consumption 12, and to machine 1 resource consumption 12.

## 3. PREREQUISITES 
### EXTERNAL SOLVERS
1. Google OR-Tools (version ≥ 9.9). Required for the ORTools() method (CP-SAT solver). OR-Tools C++ package must be installed.
2. Gurobi Optimizer (version ≥ 10 recommended). Required for the MILP_2mach() method. A valid Gurobi license is required.
3. IBM ILOG CPLEX Optimization Studio (CP Optimizer module) (version ≥ 22 recommended). Required for the CPOpt() method. A valid CPLEX/CP Optimizer license is required.

## 4. EXECUTING THE CODE
To execute the code, run the following command from the terminal, providing the required arguments in the specified order:
./executable_path instance_file_path results_file_path solution_file_path threshold time_limit
Where:
- executable_path: path to the compiled executable;
- instance_file_path: path to the input instance file;
- results_file_path: path where the results will be saved;
- solution_file_path: path where the solution details will be saved;
- threshold: threshold value (problem-dependent);
- time_limit: maximum computation time in seconds.

## 5. OUTPUT FILE FORMAT
The results file contains the following fields (semicolon-separated values):
- Instance name: name of the instance;
- Optimal: optimality status (1 if optimal, 0 otherwise);
- LB: final lower bound;
- UB: final upper bound;
- Time: total solution time in seconds;
- BB iter: number of branch-and-bound iterations;
- BB Nodes: number of nodes explored in branch-and-bound;
- BB Time: time spent in branch-and-bound in seconds;
- UB: best upper bound found;
- Time UB: time to find the best upper bound in seconds;
- LB0: maximal lower bound from the literature;
- LB3: lower bound calculated with column generation;
- Time LB: time spent computing lower bounds in seconds;
- Lifting Time: time spent in lifting procedures in seconds.

## 6. REFERENCES
[1] Fanjul-Peyro, L., Perea, F., and Ruiz, R. (2017). Models and matheuristics for the unrelated parallel
machine scheduling problem with additional resources. European Journal of Operational Research,
260(2):482–493.

[2] Min, S.-H., Lee, S.-W., and Kim, H.-J. (2024). Parallel machine scheduling with peak energy consumption
limits. IEEE Transactions on Automation Science and Engineering.
