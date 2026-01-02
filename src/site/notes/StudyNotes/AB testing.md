---
{"topic":"DataScience","dg-publish":true,"permalink":"/StudyNotes/AB testing/","dgPassFrontmatter":true,"noteIcon":""}
---


A/B testing is a user experience research methodology.
- A/B/N testing = randomized controlled experiments = controlled experiments = bucket testing = split-run testing
- A/B tests consist of a randomized experiment with two variants, A and B. It includes the application of statistical hypothesis testing or "two-sample hypothesis testing" as used in the field of statistics
- It is a way to compare two versions of a single variable, typically by testing a subject's response to variant A against variant B, and determining which of the two variants is more effective
- A/B testing is not good for testing long-term effect

>[!link] resource: https://www.emmading.com/ab-testing-cheat-sheet
# Experiment Design
- Prerequisites
	- Define key metrics: **Overall Evaluation Criterion (OEC)**
	- Changes are easy to be made
	- have enough randomization units 
- Experiment design
	- what population to select
	- size of an experiment
- Experiment running
	- collect data: instrument loggings, or utilize companies platform
- Result to decision
	- sanity checks: results are unreliable if assumptions are violated
	- consider
		- tradeoffs between metric
		- cost of launching
- Post-launch monitoring
# Techniques
### Metric selection
- **Driver Metrics** (surrogate metric, indirect/predictive metric)
	- major metric in AB testing
	- short-term, sensitive and timely
	- measurable
	- attributable 
- **Success Metrics**: [[StudyNotes/DS for Business#^a0ff11\|DS for Business#^a0ff11]]
	- a single or a very small set of metrics that capture the ultimate success you are striving towards
	- ensure success metrics are simple and stable
- combine qualitative and quantitive methods
	- qualitative: user experience research, focus groups, and surveys
	- quantitive: data analysis 
- strategies for metric selection
	- consider business goals: growth, engagement, revenue
	- consider user experience
### Sample size estimation: using [[StudyNotes/Power Analysis\|Power Analysis]]
### Randomization units
= unit of diversion = who/what we randomly assign to each variant of an A/B test
- general considerations
	- consistent user experience
	- variability
	- ethical considerations
- commonly used Randomization units
	- Account-Based (User-Based): user ID
	- Cookies
	- Session-Based (or Page View-Based): event 
	- device ID (only for mobile)
- what should be considered when choosing randomization units
	- user visible: user-level randomization required
	- non-user visible: user-level randomization NOT required
- the coarseness of randomization