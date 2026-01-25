Main principle / heuristic used

Since this is week 1 and I don't have enough information, I prioritised exploration over exploitation. I tried to select the points that are spread out across the input space ( for example the values across low/mid/high ranges in different dimensions), aiming for a space-filling / diverse sampling effect. The goal is to learn the basic landscape of each black-box function quickly (whether it’s smooth vs. rugged, unimodal vs. multimodal) rather than betting early on any single region.

Most challenging functions and why
In my opinion the hardest to query are the higher-dimensional functions (especially 6-D and 8-D) because one extra point covers a tiny fraction of the search space (“curse of dimensionality”). Without knowing whether the function is smooth, noisy, or has strong interactions between variables, it’s difficult to justify exploitation. Additional information that would help: the variable bounds (confirming [0,1]), whether the function is noisy, and whether there are constraints or known structure (e.g., separable vs. highly interacting).

How I’ll adjust strategy in future rounds
Once new results arrive, I’ll move toward a balanced explore & exploit approach:

Fit a simple surrogate model per function (for example Gaussian Process for low dims; Random Forest / TPE-style surrogate for higher dims).
Use an acquisition rule (e.g., Expected Improvement / UCB) to pick points that either look promising (exploitation) or have high uncertainty (exploration).
In higher dimensions, I’ll keep some global exploration (random/low-discrepancy) while also testing local improvements around the current best point (small perturbations).
If outputs suggest noise, I’ll prefer strategies robust to noise (e.g., averaging, larger exploration, less aggressive exploitation).