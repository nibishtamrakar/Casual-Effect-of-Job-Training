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
