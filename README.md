# Identical-Parallel-Machine-Sceduling-Renewable-Resource

The dataset contains instances used for the study of parallel machine scheduling with one renewable resource. Two different sets of instances are provided. The first set is the adaptation to the idential parallel machine case of instances provided in [1]. The second set is the adaptation of the instances studied with exact methods in [2], adapted by removing the fixed energy consumption of idle machines.

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



## 2. FILE FORMAT
Instances of both set are built the same way. Each instance file is organized as follows:
- int number of jobs
- int number of machines
- int number of stages (always equal to 1)
- int number of machines (repeated)
- matrix [N][2M] Processing times: There is one row per job, which contains:
  - int machine index
  - int processing time on that machine
  Example:
  0 72 1 72
  Means that the job can be assigned to machine 0 with processing time 72, and to machine 1 with processing time 72.
- string Resources
- int number of resources (always 1)
- string resource name (always R0)
- int resource limit (maximum available amount)
- matrix [N][2M] Resource requirements: There is one row per job, which contains:
  - int machine index
  - int resource requirement on that machine
  Example:
  0 12 1 12
  Means that the job can be assigned to machine 0 with resource consumption 12, and to machine 1 resource consumption 12.



[1] Fanjul-Peyro, L., Perea, F., and Ruiz, R. (2017). Models and matheuristics for the unrelated parallel
machine scheduling problem with additional resources. European Journal of Operational Research,
260(2):482–493.

[2] Min, S.-H., Lee, S.-W., and Kim, H.-J. (2024). Parallel machine scheduling with peak energy consumption
limits. IEEE Transactions on Automation Science and Engineering.
