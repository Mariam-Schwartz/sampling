# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 1000 (from the original 50000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: MARIAM SCHWARTZ (formerly IBRAHIM)

```
Please write your explanation here...

```
Stages of Sampling in the Model
1. Infection Sampling:
Individuals are initially chosen to be infected using np.random.choice, with a sample size based on the ATTACK_RATE (set to 0.10, so 10% of the total 1000 individuals are infected).
Sampling Frame: All attendees at weddings and brunches.
Distribution: Uniform random sampling without replacement.
2. Primary Contact Tracing Sampling:
Among the infected individuals, a fraction (determined by TRACE_SUCCESS, set to 0.20) is traced, using a Bernoulli trial (np.random.rand(...) < TRACE_SUCCESS).
Sampling Frame: All infected individuals.
Distribution: Bernoulli distribution with a success probability of 0.20.
3. Secondary Contact Tracing Sampling:
Events that meet the SECONDARY_TRACE_THRESHOLD (at least 2 traces) are marked as fully traced, so all infected individuals at these events are considered traced.
Sampling Frame: Events with primary traces meeting the threshold.
Distribution: Conditional based on the count of traced individuals at each event.

Changes Made to the code 
Set a Random Seed: Adding np.random.seed(42) will ensure that the random choices for infections and tracing are the same each time the script is executed

Reduce Simulation Runs: Changing 50000 to 1000 for the results loop will reduce the computation load while still providing insight into the simulation’s distribution, the graph has the same distribution plot


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `HH:MM AM/PM - DD/MM/YYYY`
* The branch name for your repo should be: `sampling-and-reproducibility`
* What to submit for this assignment:
    * This markdown file (sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `sampling-and-reproducibility`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
