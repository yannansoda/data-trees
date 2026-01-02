---
{"topic":"Math, Statistics","dg-publish":true,"permalink":"/StudyNotes/Fisher Information/","dgPassFrontmatter":true,"noteIcon":""}
---



## Fisher information

Assume there are two closely spaced stimuli s and s + $\Delta$s, then we can signal s if:

$$\frac{p(r|s+\Delta s)}{p(r|s)} < 1$$

when the likelihood ratio (i.e. the left side) is equal to 1, it will be hard to decide if the stimulus is s or s + $\Delta$s.

If one want to be sure that he is signaling s, the likelihood ratio should be as different from 1 as possible (on average), which means the following value should be as large as possible:

$$<\ (\frac{p(r|s+\Delta s)}{p(r|s)} - 1)^2 >\ $$

after some derivations, we define the Fisher information based on it:

$$ J(s) = <\ (\frac{d}{ds} ln \ p (r|s))^2 >\ _{p(r|s)}$$