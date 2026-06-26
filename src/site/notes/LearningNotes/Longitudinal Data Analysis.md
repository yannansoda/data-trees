---
{"topic":"DataScience, AIxHealth","dg-publish":true,"permalink":"/LearningNotes/Longitudinal Data Analysis/","dgPassFrontmatter":true,"noteIcon":"","dg-note-properties":{"topic":"DataScience, AIxHealth"}}
---

# Overview
## Definitions

Longitudinal data = data collected from the same individuals or units repeatedly over time. 
## Data Structure
### Long Format
- One row per subject-time combination.
- usually preferred for mixed-effects models, GEE, time-varying Cox models, and most longitudinal analyses
### Wide Format
- One row per subject, with repeated measurements stored in separate columns.
- can be useful for descriptive summaries, paired comparisons, MANOVA, or some machine learning workflows
- but: less flexible for irregular follow-up times
## Characteristics
- Repeated observations are usually correlated
- Individuals may differ in their baseline level and in their rate of change over time
- Measurement times may be regular or irregular
- Missing data are common
- Dropout may be informative, especially in health studies
- The number of observations per subject may vary
- Time can be modeled as continuous, categorical, nonlinear, or event-based

## Common Research Questions
- **Change Over Time**: Does a biomarker change with age or follow-up time?
- **Group Differences in Trajectories**: Do different groups change differently over time? This is often tested using a `time x group` interaction.
- **Baseline Predictor of Future Change**: Does a baseline variable predict later trajectory?
- **Time-Varying Exposure or Biomarker**: Does the updated value of a biomarker predict future risk?
- **Trajectory Subgroups**: Are there distinct groups of people with different longitudinal patterns?
- **Longitudinal Biomarker and Event Outcome**: Is a biomarker trajectory associated with time-to-event outcomes?
# Modeling Strategies

## Modeling Methods

| Method                                                                                              | When to use                                                                              | Pros                                                                             | Cons                                                                                              | Health-data example                                                   |
| --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **Change-score analysis**                                                                           | Compare baseline-to-follow-up change                                                     | Intuitive; easy to report                                                        | Noisy; sensitive to measurement error; limited to few time points                                 | Compare 6-month weight loss between interventions                     |
| **ANCOVA** ([[LearningNotes/ANOVA & Post-hoc Tests#ANCOVA\|ANOVA & Post-hoc Tests#ANCOVA]])                                                      | Compare one follow-up outcome between groups, adjusting for baseline                     | Simple; interpretable; often more efficient than change scores                   | Usually limited to one follow-up; does not model trajectories                                     | Compare 12-month blood pressure by treatment, adjusting for baseline  |
| **Repeated-measures ANOVA** ([[LearningNotes/ANOVA & Post-hoc Tests\|ANOVA & Post-hoc Tests]])                                            | Compare fixed, common time points in a balanced design                                   | Simple; familiar                                                                 | Needs near-complete, regularly timed data; assumes sphericity; inflexible with missingness        | Compare mean HbA1c at baseline, 3, 6, and 12 months                   |
| **MANOVA** ([[LearningNotes/ANOVA & Post-hoc Tests#MANOVA\|ANOVA & Post-hoc Tests#MANOVA]])                                                      | Treat repeated time points as correlated outcomes                                        | Avoids sphericity; models cross-time correlation                                 | Often needs complete data; poor fit for many or irregular time points                             | Compare treatment groups on blood pressure at three visits            |
| **Mixed-effects models** ([[LearningNotes/Linear Mixed Models\|Linear mixed models]])                                                  | Model repeated or nested outcomes, including irregular visits and incomplete data        | Models individual trajectories; handles unbalanced data; supports random effects | Requires covariance/random-effect choices; inference depends on model and missingness assumptions | Estimate patient-specific eGFR decline over time                      |
| **Generalized estimating equations (GEE)** ([[LearningNotes/Generalized Linear Models#Relationship to GEE\|Generalized Linear Models#Relationship to GEE]])      | Estimate population-average effects for correlated continuous, binary, or count outcomes | Robust population-average inference; flexible outcome distributions              | Does not model individual trajectories; dropout can bias results                                  | Estimate the average treatment effect on repeated hypertension status |
| **Structural equation models (SEM)** ([[LearningNotes/Structural Equation Models\|Structural Equation Models]])                      | Model complex relations among observed and latent variables                              | Handles latent constructs; tests direct and indirect paths                       | Specification-sensitive; complex; often needs large samples                                       | Model links among latent frailty, inflammation, and disability        |
| **Latent growth curve models** ([[LearningNotes/Structural Equation Models#Latent Growth Curve Models\|Structural Equation Models#Latent Growth Curve Models]]) | Model average and individual change within an SEM framework                              | Estimates growth factors; supports latent variables                              | Needs adequate waves and sample size; specification-sensitive                                     | Model cognitive decline using repeated test scores                    |
| **Transition models**                                                                               | Model the current outcome conditional on prior outcomes                                  | Captures short-term dependence and state changes                                 | Interpretation is history-dependent; less suited to long-term trajectories                        | Model transitions among healthy, prediabetes, and diabetes states     |
| **Time-varying Cox models** ([[LearningNotes/Survival Analysis#Cox (Proportional Hazards) Model\|Survival Analysis#Cox (Proportional Hazards) Model]])                | Relate updated exposures or biomarkers to time-to-event outcomes                         | Uses changing covariates; handles censoring                                      | Assumes proportional hazards unless extended; time-dependent confounding may bias estimates       | Relate updated blood pressure to stroke risk                          |
| **Joint models** (a model for trajectory + a model for survival)                                    | Analyze a longitudinal marker and related event time together                            | Links marker trajectory to event risk; accounts for informative dropout          | Complex; computationally intensive; specification-sensitive                                       | Link PSA trajectory to prostate-cancer recurrence                     |
| **Latent class trajectory models**                                                                  | Identify subgroups with distinct longitudinal patterns                                   | Finds clinically meaningful trajectory groups; allows heterogeneous trends       | Class number can be unstable; assignments are probabilistic                                       | Identify distinct BMI trajectories from childhood to adulthood        |

## Missing Data Handling

- if Missing at Random ([[LearningNotes/Handling Missing Data#^656f1e\|Handling Missing Data#^656f1e]]): mixed-effects models are valid under missing at random assumptions if the model is correctly specified
- if Missing Not at Random ([[LearningNotes/Handling Missing Data#^b7a197\|Handling Missing Data#^b7a197]]):common and problematic in health studies, can try
	- mixed-effects models
	- multiple imputation
	- inverse probability weighting
	- sensitivity analysis
	- joint modeling of longitudinal and dropout/event processes

## Time Data Handling
### Design of time definition 
Time is a key design choice in longitudinal analysis. Possible definitions:
- time since baseline
- age
- calendar time
- time since diagnosis
- time before event
- treatment phase
- visit number
### Model of time
Time can be modeled as:
- continuous
- categorical
- piecewise linear
- spline-based
- nonlinear
- random slope

# Key Model Interpretation

### Fixed Effect of Time
Average change in the outcome per unit time.
### Group Effect
Difference between groups at the reference time point, often baseline.

### Time x Group Interaction
Difference in rate of change between groups.
This is often the most important term when comparing trajectories.

### Random Intercept
Allows each subject to have their own baseline level.

### Random Slope
Allows each subject to have their own rate of change.
### Within-Person Effect & Between-Person Effect

>[!Tip] Within-person and between-person effects can differ and should not always be interpreted as the same thing.

#### Within-Person Effect: 
Association between changes within the same person over time.\Example:
> When a person's blood pressure increases above their own average, does their risk increase?
#### Between-Person Effect
Association between differences across people.
Example:
> Do people with higher average blood pressure have higher risk than others?

# Practical Workflow

1. Understand the study design.
2. Define the time scale.
3. Visualize individual trajectories with spaghetti plot.
4. Plot group-level mean/smoothed trajectories.
5. Check missingness patterns.
6. Decide whether the goal is population-average inference, subject-specific inference, prediction, or trajectory discovery.
7. Choose the model accordingly.
8. Fit a simple model first.
9. Add nonlinear time, interactions, or random slopes if needed.
10. Check assumptions and model fit.
11. Interpret time effects and time x group interactions carefully.
12. Conduct sensitivity analyses for missing data and dropout.


# Health Data Examples

### Repeated Blood Biomarkers

Question:

> Does inflammatory biomarker level increase faster among people who later develop cardiovascular disease?

Possible methods:

- mixed-effects model
- time-varying Cox model
- joint model

### Cognitive Decline

Question:

> Do APOE-e4 carriers show faster cognitive decline?

Possible methods:

- mixed-effects model
- latent growth curve model
- joint model with dementia onset

### Disease Progression

Question:

> What are the common trajectories of kidney function decline?

Possible methods:

- mixed-effects model
- latent class trajectory model
- joint model with kidney failure outcome

### Treatment Follow-Up

Question:

> Does a treatment reduce blood pressure over repeated follow-up visits?

Possible methods:

- ANCOVA for simple baseline-follow-up design
- mixed-effects model for multiple visits
- GEE for population-average treatment effec
