# Effect of Job Training on Future Earnings

**Course:** Foundations of Data Science  

**Group Members:** Nibish Tamrakar, Karthik Subramanium, Zubair Ali L

---

## 1. Introduction

### 1.1. The Question / Estimand

*What is the causal effect of participating in a job training program on future earnings, after adjusting for prior earnings?*

---

### 1.2. Data Description

- **Data Source:**  
  The analysis uses data from the National Supported Work (NSW) job training experiment compiled by LaLonde (1986), available via the NBER repository:  
  <https://users.nber.org/~rdehejia/data/.nswdata2.html>

- **Rows:**  
  Each row corresponds to one individual participant in the study *(722 individuals total)*.

- **Columns:**  
  The dataset includes indicators for program participation and earnings outcomes, along with background measures. Key variables used in our causal analysis are:
  - **treat:** Binary indicator of participation in the job training program  
    *(1 = treated, 0 = control)*
  - **re75:** Earnings in 1975 (pre-treatment), representing baseline economic status
  - **re78:** Earnings in 1978 (post-treatment), representing the outcome of interest

- **Relevance to the Causal Question:**  
  This dataset is well suited for estimating the causal effect of job training on future earnings because it originates from a randomized training program, providing credible treatment assignment. Crucially, it includes prior earnings (**re75**) measured before treatment, which plausibly influences both participation and later earnings. Adjusting for this confounder allows us to isolate the causal impact of training on post-program earnings (**re78**). Additionally, the clear temporal ordering — *baseline earnings → training participation → future earnings* — aligns directly with our estimand.

___
## 2. Causal Model

<img src="job_training_dag.png" style="display:block; margin:auto;" width="450">

*The Directed Acyclic Graph (DAG) consists of three nodes and three directed edges:*

- **re75 → treat**
- **re75 → re78**
- **treat → re78**

*This DAG is connected and acyclic, representing our assumptions about how prior earnings, job training participation, and future earnings are causally related.*

### 2.1. Variables

*(Clearly label and describe your three variables (Treatment, Outcome, Confound). Do not use T, Y, Z. Use symbols that reflect the names of the variables from your dataset.)*

- **Treatment (treat):**  
  Binary indicator of participation in the job training program  
  *(1 = participated in training, 0 = did not participate)*

- **Outcome (re78):**  
  Individual earnings in 1978, measured after the job training period

- **Confound (re75):**  
  Individual earnings in 1975, measured before treatment and used as a proxy for baseline economic status, skill level, and employability

### 2.2. Assumed Causal Relationships

*The causal model assumes that prior earnings (**re75**) influence both job training participation (**treat**) and future earnings (**re78**). Individuals with lower or unstable earnings before the program may be more likely to enroll in job training, creating a causal path from **re75 → treat**. At the same time, prior earnings strongly predict later earnings due to persistent differences in skills, work experience, and labor market opportunities, forming the path **re75 → re78**.*

*The primary causal effect of interest is the direct impact of job training participation on future earnings, represented by **treat → re78**. Because **re75** affects both treatment assignment and the outcome, it acts as a confounder. Adjusting for **re75** blocks the backdoor path between **treat** and **re78**, allowing us to identify the causal effect of job training on future earnings under the assumptions encoded in the DAG.*


