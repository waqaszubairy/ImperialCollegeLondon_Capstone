
Project Overview
-----------------
This repository captures my work on the Black-Box Optimisation (BBO) capstone project, a multi-week exercise centred on improving the performance of unknown functions through iterative querying. The internal mechanics of each function are concealed, and learning is driven solely by observing input–output pairs returned after each submission.

The purpose of the BBO capstone project is to develop the ability to make efficient, evidence-based decisions under uncertainty, which is a frequent challenge in real-world machine learning systems. Practical examples include hyperparameter optimisation, system tuning, and simulation-driven decision-making where gradients or full model knowledge are unavailable.

This capstone reflects how machine learning problems are approached in production environments, where feedback is limited and evaluation budgets are constrained. It supports the development of transferable skills in experimental design, iterative optimisation and technical communication that are directly relevant to applied machine learning and data science work


Inputs and Outputs
------------------
Inputs
        The project consists of eight independent black-box functions, each with a fixed dimensionality:
        Function 1–2: 2D
        Function 3: 3D
        Function 4–5: 4D
        Function 6: 5D
        Function 7: 6D
        Function 8: 8D
        Each week, I submit one query point per function in the following format:
        x1-x2-x3-...-xn
        where:
        each value lies in the interval [0, 1]
        each value is specified to six decimal places
        each value begins with 0 (e.g. 0.123456)
        Example (2D function):
        0.157321-0.823654
Outputs
        For each submitted query, the system returns a single scalar response value, representing the function’s performance at that point. The function structure, gradients and noise characteristics are unknown. Sample of output value I received from my week 1 document is mentioned below.


        Function 1:	5.0677603251625e-162
        Function 2:	0.3765928430932734
        Function 3:	-0.05200479043115147
        Function 4:	-21.436843228872494
        Function 5:	187.3509656043825
        Function 6:	-1.7626803789825753
        Function 7:	0.028989276474455275
        Function 8:	7.3410156721259


Challenge Objectives
---------------------
1. The primary objective of the BBO capstone project is to maximise the output of each black-box function while operating under several constraints:
2. Only one new query per function per week is allowed
3. The total number of queries is limited, encouraging efficient learning
4. The internal function structure is completely unknown
5. Feedback is received after submission, not interactively

Given these constraints, the challenge is not only to find high-performing inputs, but to do so strategically, minimising wasted queries and maximising information gained from each evaluation.


Technical Approach
-------------------
My approach evolves iteratively and is intentionally documented as a living process.

Week 1 – Exploration
    With no prior performance information, I prioritised exploration. Query points were selected to be diverse and space-filling, ensuring broad coverage of the input domain. The aim was to gain an initial understanding of the response scale and variability across functions.

Week 2 – Evidence-Based Heuristics
    Using Week 1 outputs, I adopted a hybrid exploration–exploitation strategy:
    Functions with strong positive responses were explored locally using small perturbations (exploitation).
    Functions with poor or negative responses were probed in distant regions of the space (exploration).
    This stage relied on simple heuristics rather than formal models, reflecting the still-limited data available.

Week 3 – Model-Informed Thinking (SVM Perspective)
    In Week 3, I began framing the problem through a classification lens inspired by Support Vector Machines (SVMs). Outputs were conceptually treated as “high-performing” vs “low-performing”, guiding queries toward:
        1. regions likely to belong to a “high” class (exploitation), and
        2. uncertain regions that would help refine a decision boundary (exploration).
        3. While full SVM training is premature with limited data, this perspective improves interpretability and helps structure decisions, especially in    higher-dimensional settings.


Ongoing Strategy
----------------
As more data becomes available, I plan to:
        introduce simple surrogate models (e.g. linear models, kernel methods)
        compare model-guided decisions with heuristic baselines
        continuously document assumptions, limitations and observed patterns
        Balancing exploration and exploitation remains central, with decisions justified by observed evidence rather than blind optimisation.