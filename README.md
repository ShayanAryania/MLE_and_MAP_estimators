# MLE_and_MAP_estimators
### **Maximum Likelihood Estimation (MLE) vs. Maximum A Posteriori (MAP) Estimation**

Both **MLE** and **MAP** are methods used for estimating parameters of a probability distribution, but they differ in how they incorporate prior information.

---

### **1. Maximum Likelihood Estimation (MLE)**  
**MLE finds the parameter θ that maximizes the likelihood function** \( P(D | \theta) \), given the observed data \( D \). It assumes no prior knowledge about \( \theta \).

\[
\hat{\theta}_{MLE} = \arg\max_{\theta} P(D | \theta)
\]

#### **Example of MLE**  
Suppose we have a biased coin, and we want to estimate the probability \( \theta \) of getting heads. We flip the coin 10 times and observe 7 heads.

- The likelihood function is:

  \[
  P(D | \theta) = \theta^7 (1 - \theta)^3
  \]

- Taking the **log-likelihood**:

  \[
  \log P(D | \theta) = 7 \log \theta + 3 \log (1 - \theta)
  \]

- Differentiating and solving for \( \theta \):

  \[
  \hat{\theta}_{MLE} = \frac{7}{10} = 0.7
  \]

---

### **2. Maximum A Posteriori (MAP) Estimation**  
**MAP finds the parameter \( \theta \) that maximizes the posterior probability** \( P(\theta | D) \), incorporating prior knowledge \( P(\theta) \).

\[
\hat{\theta}_{MAP} = \arg\max_{\theta} P(\theta | D) = \arg\max_{\theta} P(D | \theta) P(\theta)
\]

By **Bayes' theorem**:

\[
P(\theta | D) \propto P(D | \theta) P(\theta)
\]

#### **Example of MAP**  
Using the same coin-flipping example, suppose we have prior knowledge that \( \theta \) is likely around **0.6** (e.g., a Beta prior \( \text{Beta}(9,6) \), meaning we’ve observed 8 heads and 5 tails before this experiment).

- The prior is:

  \[
  P(\theta) \propto \theta^{8} (1 - \theta)^{5}
  \]

- The posterior is:

  \[
  P(\theta | D) \propto \theta^{(7+8)} (1 - \theta)^{(3+5)}
  \]

  \[
  P(\theta | D) \propto \theta^{15} (1 - \theta)^8
  \]

- The **MAP estimate** is:

  \[
  \hat{\theta}_{MAP} = \frac{7 + 8}{10 + 8} = \frac{15}{18} \approx 0.833
  \]

---

### **Key Differences**
| Feature  | MLE | MAP |
|----------|------|------|
| **Formula** | \( \hat{\theta}_{MLE} = \arg\max P(D | \theta) \) | \( \hat{\theta}_{MAP} = \arg\max P(D | \theta) P(\theta) \) |
| **Prior Involvement** | No prior | Uses prior \( P(\theta) \) |
| **Bias** | Unbiased (but high variance) | Biased towards prior (lower variance) |
| **Application** | Large data, no prior info | Small data, prior knowledge available |

**Conclusion:**  
- **MLE** is useful when there is **no prior information** and when we have **large amounts of data**.
- **MAP** is better when we have **prior beliefs** or **limited data**, as it regularizes the estimate.
