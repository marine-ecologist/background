# background

`callr::r_bg()` is a function from the callr package that launches a new background R process to evaluate a function asynchronously. 

The `background()` function uses `callr::r_bg()` to run any R expression asynchronously in a separate R session, captures all created objects, and returns them to the calling environment. The function automatically loads the packages currently in use, evaluates the expression in isolation, and saves the resulting environment as an .rds file. Upon successful completion, it assigns all objects back into the specified environment, with optional conflict handling controlled via the overwrite argument. This allows safe, silent, and reproducible execution of long-running or blocking tasks without interrupting the main R session.

When not to use `background()`:
	•	For non-interactive scripts (e.g., Rscript pipelines), parallel tools (future, foreach, targets) are more robust
	•	When reproducibility in environments (e.g., CI/CD, HPC) is required, using renv or targets pipelines is safer
	•	When deterministic side effects (e.g., file writing) must be guaranteed
