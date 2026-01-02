---
{"topic":"Statistics","dg-publish":true,"permalink":"/StudyNotes/Circular Statistics/","dgPassFrontmatter":true,"noteIcon":""}
---


# Circular Distribution
## Von Mises Distribution = normal distribution for 
$$
f(x) = \frac{e^{\kappa cos(x - \mu)}}{2 \pi I_0 (\kappa)}
$$
where $\frac{1}{\kappa} \propto \sigma^2$

## How spread is the distribution?
### Resultant Vector Length (R)
- It describes how spread is the distrbution around the mean.
- range [0, 1]

### Circular Variance
- Circular Variance = 1 - R
> [!INFO]
> Note that it does not describe the "expected deviation from the mean" as in normal linear statistics 

## Whether the  distribution is uniform?
- If the distribution is von Mises 
=> Parametric test for uniformity = __Rayleigh test__
	- The tested distribution must be von Mises 
	- Null hypothesis: the data are from a unifrom distribution
-  If  the distribution is not von Mises (e.g. bimodal) 
=> Non-Parametric test (for linear data see [[StudyNotes/Non-parametric methods\|Non-parametric methods]]):
	- __Omnibus test__
	- __Rao's test__

# Test for significance of the mean/median
| Circular | Similar tests for linear data | Prerequisites|
| -- | -- | --|
| circular version of t-test |  student t-test | from a von Mises distribution |
| parametric paired-tests" Watson-Williams Test | paired-t test | from a von Mises distribution |
| non-parametric paired-test (on median!!!) | Kruskal-Wallis test[[StudyNotes/Non-parametric methods#Non-parametric methods\|Non-parametric methods#Non-parametric methods]] | no prerequisites for the distribution |

	In non-parametric tests, median is always more important and better estimated, because it is more resilient to the outlier is more robust (e.g. considering when you have a outlier group far away from the 'main' distibution)