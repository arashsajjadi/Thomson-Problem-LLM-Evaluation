# My Homemade Research on Evaluating LLM Responses for the Thomson Problem

*This document details my research—conducted in less than half a day—where I prompted various large language models (LLMs) with a single, detailed query regarding the Thomson problem (n = 100). The results, while at times shocking, reveal significant differences in response quality. However, it is important to note that these conclusions are based on a single prompt. For a more reputable and comprehensive evaluation, multiple prompts and iterations would be necessary.*

---

## 1. Introduction

The **Thomson problem** involves arranging *n* identical point charges on the surface of a unit sphere so that their total electrostatic potential energy is minimized. For *n = 100*, no closed-form solution is available; hence, numerical optimization techniques (e.g., simulated annealing, gradient descent, or hybrid approaches) are employed to approximate the minimal energy, typically around **1745.18** (in relevant energy units).

In this research, I provided a detailed prompt to various LLMs and collected their responses. The evaluation focused on several dimensions:
- **Lingual Clarity:** How clearly the response is written.
- **Way of Thinking:** The demonstration of a structured, step‑by‑step reasoning process.
- **Logical Reasoning:** The coherence and logical flow of the explanation.
- **Mathematical Rigor:** The correctness and depth of the underlying math and derivations.
- **Final Output Accuracy:** How closely the reported minimal energy (_Eₘᵢₙ_) aligns with the literature.
- **Methodology Transparency:** The extent to which the algorithm, parameters, and convergence criteria are explained.
- **Local Minima Handling / Robustness:** The approach’s ability to overcome the nonconvex, multimodal landscape.
- **Parameter Specification/Tuning:** Whether parameter choices are clearly stated and justified.
- **Literature Awareness & Justification:** How well the answer references known research and expected values.
- **Overall Coherence & Feasibility:** The integrated quality of the response.

This document not only presents the final evaluation table but also critically discusses the evidence and academic rationale behind the ratings.

---

## 2. Methodology

### 2.1 Experimental Setup

I sent the following (paraphrased) prompt to all selected LLMs:

> **Prompt:**  
> "Solve the Thomson Problem for n = 100. Develop an optimization strategy (e.g., using simulated annealing, gradient‑based methods, or hybrids) to find a near‑optimal configuration of points on a unit sphere. Report the minimal energy (_Eₘᵢₙ_) with as much precision as possible and provide a detailed, step‑by‑step explanation of your methodology. Compare your result with the best‑known literature value (~1745.18) and justify your approach, including parameter tuning, handling of constraints, and convergence criteria."

The responses were then collected from the following models:
1. **deepseek‑r1 offline 14b**
2. **ChatGPT‑4o mini**
3. **Llama‑3.1‑405B**
4. **Llama‑3.1‑70B**
5. **deepseek‑r1 offline 32b**
6. **deepseek‑r1 offline 70b**
7. **deepseek‑r1 online (regular)**
8. **ChatGPT O3 mini**
9. **Llama 70b**
10. **Gemini 2.0**
11. **ChatGPT‑4o**
12. **deepseek‑r1 online (deepthink)**

### 2.2 Evaluation Criteria

Each model was judged on:
- **Lingual Clarity:** Precision, readability, and fluency.
- **Way of Thinking:** The extent of a structured, systematic approach.
- **Logical Reasoning:** How well ideas are linked in a logical sequence.
- **Mathematical Rigor:** The depth and correctness of mathematical explanations and derivations.
- **Final Output Accuracy:** How close the final numerical value is to the known literature value (~1745.18).
- **Methodology Transparency:** Clarity in explaining the algorithm, parameter settings, and convergence checks.
- **Local Minima Handling:** Strategies for overcoming nonconvex optimization challenges.
- **Parameter Specification/Tuning:** Explicitness and appropriateness of parameter choices.
- **Literature Awareness & Justification:** Evidence of academic grounding and comparison with published work.
- **Overall Coherence & Feasibility:** The integrated quality of the explanation, ensuring that each step logically leads to a feasible solution.

The evaluation also critically examined whether the models were generating placeholder numbers (i.e., “hallucinating”) or actually performing justified calculations.

---

## 3. Results and Critical Analysis

### 3.1 Overview of Model Responses

- **deepseek‑r1 online (deepthink):**  
  This model produced a detailed, hybrid approach (using simulated annealing combined with Riemannian gradient descent). It explained every step—from initialization to convergence—and reported a final energy of **1745.19 ± 0.03**, which closely aligns with the literature. Its clarity, rigorous derivation, and complete parameter specification make it the strongest overall.

- **ChatGPT‑4o:**  
  This response offered a well-structured explanation and clear methodological segmentation. However, its final numerical output (~4851.38) was significantly off from the literature value. Despite its strong reasoning, the inaccurate final result lowered its overall effectiveness.

- **Gemini 2.0:**  
  Gemini 2.0 showed good integration of theory and practice, discussing key challenges and parameter tuning. Nevertheless, its final energy value lacked the precision of deepseek‑r1 online (deepthink), leading to a moderate penalty in “Final Output Accuracy.”

- **ChatGPT O3 mini:**  
  The response from ChatGPT O3 mini provided a reasonable outline but was less detailed in its parameter specifications and overall methodology. Although it demonstrated acceptable clarity, the depth of reasoning was not as extensive as in the top-performing models.

- **deepseek‑r1 offline (regular, 32b, 70b):**  
  These versions employed code-style explanations and iterative methods. Their methodological transparency was decent; however, they reported final energy values (e.g., ~6691 or ~2790.60) that deviated markedly from the target value. The results appear more like placeholders than rigorous numerical calculations.

- **Llama-based Models (Llama‑3.1‑405B, Llama‑3.1‑70B, Llama 70b) and ChatGPT‑4o mini:**  
  These responses generally provided superficial outlines. They frequently generated placeholder numbers (e.g., ~8.5, or values in the 500-range) and lacked the detailed, step‑by‑step derivation seen in the best responses.

- **deepseek‑r1 offline 14b:**  
  This model’s output was the least detailed and produced very poor numerical results. It scored low across almost all categories.

### 3.2 Final Evaluation Table

Below is the final, consolidated evaluation table:

| **Aspect**                            | **(1) DS1‑off 14b** | **(2) CG4o‑mini** | **(3) Llama‑3.1‑405B** | **(4) Llama‑3.1‑70B** | **(5) DS1‑off 32b** | **(6) DS1‑off 70b** | **(7) DS1‑online reg** | **(8) ChatGPT O3 mini** | **(9) Llama 70b** | **(10) Gemini 2.0** | **(11) ChatGPT‑4o** | **(12) DS1‑online deepthink** |
|---------------------------------------|:-------------------:|:-----------------:|:---------------------:|:-------------------:|:-------------------:|:-------------------:|:----------------------:|:-----------------------:|:-----------------:|:-------------------:|:------------------:|:----------------------------:|
| **Lingual Clarity**                   | ★★                  | ★★★              | ★★★                  | ★★★                | ★★★                | ★★★                | ★★★                  | ★★★★                  | ★★★              | ★★★★                | ★★★★              | **★★★★★**                   |
| **Way of Thinking**                   | ★★                  | ★★               | ★★                   | ★★                 | ★★★                | ★★★                | ★★★                  | ★★★                   | ★★★              | ★★★★                | ★★★★              | **★★★★★**                   |
| **Logical Reasoning**                 | ★★                  | ★★               | ★★                   | ★★                 | ★★★                | ★★★                | ★★★                  | ★★★                   | ★★★              | ★★★★                | ★★★★              | **★★★★★**                   |
| **Mathematical Rigor**                  | ★★                  | ★★               | ★★                   | ★★                 | ★★★                | ★★★                | ★★★                  | ★★★                   | ★★★              | ★★★★                | ★★★★              | **★★★★★**                   |
| **Final Output Accuracy**             | ★                   | ★                | ★                    | ★                  | ★★                 | ★★                 | ★                    | ★★                    | ★                  | ★★★                 | ★★                | **★★★★★**                   |
| **Methodology Transparency**          | ★★                  | ★★               | ★★                   | ★★                 | ★★★                | ★★★                | ★★★                  | ★★★                   | ★★★              | ★★★★                | ★★★★              | **★★★★★**                   |
| **Local Minima Handling / Robustness**| ★★                  | ★★               | ★★                   | ★★                 | ★★★                | ★★★                | ★★★                  | ★★★                   | ★★★              | ★★★                 | ★★★★              | **★★★★★**                   |
| **Parameter Specification/Tuning**    | ★★                  | ★                   | ★★                   | ★★                 | ★★★                | ★★★                | ★★★                  | ★★★                   | ★★★              | ★★★★                | ★★★★              | **★★★★★**                   |
| **Literature Awareness & Justification**| ★★                 | ★                   | ★                   | ★                  | ★★★                | ★★★                | ★★★                  | ★★★                   | ★★               | ★★★                 | ★★★★              | **★★★★★**                   |
| **Overall Coherence & Feasibility**   | ★★                  | ★                   | ★                   | ★                  | ★★★                | ★★★                | ★★★                  | ★★★                   | ★★               | ★★★★                | ★★★★              | **★★★★★**                   |

*Legend:*  
- **DS1‑off 14b**: deepseek‑r1 offline 14b  
- **CG4o‑mini**: ChatGPT‑4o mini  
- **Llama‑3.1‑405B**: Llama‑3.1‑405B  
- **Llama‑3.1‑70B**: Llama‑3.1‑70B  
- **DS1‑off 32b**: deepseek‑r1 offline 32b  
- **DS1‑off 70b**: deepseek‑r1 offline 70b  
- **DS1‑online reg**: deepseek‑r1 online (regular)  
- **ChatGPT O3 mini**: ChatGPT O3 mini  
- **Llama 70b**: Llama 70b  
- **Gemini 2.0**: Gemini 2.0  
- **ChatGPT‑4o**: ChatGPT‑4o  
- **DS1‑online deepthink**: deepseek‑r1 online (deepthink)

---

## 4. Discussion & Academic Comparison

### 4.1 Critical Analysis

The evaluation results are, at first glance, somewhat shocking. Some models (e.g., Llama‑based versions and ChatGPT‑4o mini) produced final numerical values (such as ~8.5 or ~524–544) that are drastically inconsistent with the expected literature value of approximately 1745.18. This discrepancy suggests that many models generated placeholder numbers rather than performing a genuine calculation based on the detailed prompt.

In contrast, **deepseek‑r1 online (deepthink)** delivered a response that was both methodologically robust and numerically accurate:
- **Evidence of Logical Depth:** Its explanation was replete with detailed reasoning, including a discussion of hybrid optimization techniques (combining simulated annealing and Riemannian gradient descent).  
- **Mathematical Evidence:** The response provided clear derivations and parameter tuning evidence that justified its final result.  
- **Literature Alignment:** Its reported energy value of _Eₘᵢₙ ≈ 1745.19 ± 0.03_ is nearly identical to the best‑known literature value, lending strong credence to its methodology.

Other models like **ChatGPT‑4o** and **Gemini 2.0** demonstrated commendable linguistic clarity and reasoning but fell short in the precision of their final numerical outputs. This divergence highlights the importance of not only presenting a well‐structured explanation but also of performing accurate, reproducible computations.

### 4.2 Limitations and Need for Further Evaluation

It is important to emphasize that these evaluations are based on a single prompt.  
- **Limited Prompt Scope:** A single prompt does not capture the full capability of any LLM. For a fair, reputable conclusion, multiple prompts and diverse problem scenarios should be tested.  
- **Reproducibility:** Repeating this experiment with additional, varied prompts would help validate these results.  
- **Potential Bias:** The observed discrepancies may be influenced by the specific wording of the prompt; different formulations might yield different strengths and weaknesses in the models.

Thus, while the results presented here are comprehensive for this one experiment, they are not necessarily indicative of the overall reliability or academic robustness of these LLMs.

---

## 5. Conclusion

This research—a rapid, less-than-half-day experiment—revealed striking differences in the outputs of various LLMs when tasked with solving the Thomson problem (n = 100). The final evaluation table, detailed above, reflects a rigorous, academic comparison across multiple criteria including clarity, logical reasoning, mathematical rigor, methodology transparency, and final output accuracy.

The key takeaway is that **deepseek‑r1 online (deepthink)** emerged as the strongest performer, while many other models produced results that are not numerically or methodologically reliable based on this single prompt. For a more reputable conclusion, further testing with multiple prompts is essential.

I invite further discussion, critique, and additional testing to refine these evaluations.

---

*This research is my homemade effort. All analyses, criticisms, and conclusions are based on a single prompt and should be considered preliminary.*
