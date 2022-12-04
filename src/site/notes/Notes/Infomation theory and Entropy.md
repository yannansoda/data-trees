---
{"dg-publish":true,"permalink":"/notes/infomation-theory-and-entropy/"}
---

Neural Code - Lecture 14

## Information & Entropy - Part 1
### Math background knowledge
Before getting into neural data, we can understand he information and entropy with an example of creating a message.

Take an alphabet $n_1, n_2, ... , n_q$ to create a message of length $N$, we can create $M$ different messages: 
$$M =number\ of \ states = \frac {N!} {n_1! n_2! ... n_q!}$$
consider probabilities $p_1, p_2, ..., p_q$ for $n_1, n_2, ... , n_q$, i.e.:
$n_1= Np_1$, $n_2= Np_2$, ... , $n_q= Np_q$
then
$$M =\frac {N!} {(Np_1)! (Np_2)! ... (Np_q)!}$$
use **Stirling's approximation** $ln \ q! = q\ lnq - q$ and $\sum p_i = 1$, then $$ln(M) = -N \sum p_i \ lnp_i$$
rescale to bits (i.e., logarithm to the base of 2), the average information is
$$<I> = log_2(M) = N(\sum -p_i \ log_2 \ p_i)$$
the average information per alphabet is
$$\frac {<I>}{N} = \sum -p_i \ log_2 \ p_i$$
To maximize the entropy 
$$I = -\sum _{I=1} ^q p_i log_2(p_i) + \lambda ( \sum _{I=1} ^q p_i-1)$$
$$\frac{dI}{dp_j} = -ln (p_j) /ln(2) -1/ln(2) + \lambda$$
$I$ is maximal when 
$$ p_i = \frac{1}{q}$$

>**Stiring's formula**
> $$n! = \sqrt{2 \pi} n^{n+1/2} exp(-n)$$
> $$ln\ n! = n \ln n - n + \frac{1}{2} ln(2\pi n)$$
> for very large n: 
> $$ln(n!) = n\ ln \ n - n$$
> 
>proof:
>$$n! = \int_0^\infty x^nexp(-x)\, dx$$
>set $I(a)$ 
>$$I(a) = \int_0^\infty exp(-ax)dx = a^{-1}$$
>then 
>$$({-\frac{d}{da}})^n I(a) = \int_0^\infty x^n exp(-ax)dx = n!\ a^{-n-1} $$
>when a=1
>$$\int_0^\infty x^nexp(-x)\, dx = n!$$


### Information of spike trains
Consider spike trains as binary strings (0 or 1) of length $N$ with $probability\ of \ 1 (firing) = p$,  $probability \ of \ 0 (not \ firing) = 1-p = q$, then the number of states will be:
$$\frac{N!}{(N_p)!(N_q)!}$$
the entropy $S$ will be:
$$S\sim ln{\frac{N!}{(N_p)!(N_q)!}}$$
use $p+q=1$ and the Stiring's formula as following
$$ln(M!) = M\ lnM - M$$  
one can derive:
$$S \approx -Nplnp - Nqlnq$$
after rescaling to bits (i.e., logarithm to the base of 2):
$$\frac{S}{N} = -p \ log_2p - q \ log_2q$$
which is a special case of
$$\frac{S}{N} = - \sum p_i \ log_2 (p_i)$$


Spike trains can contain errors. For instance, synaptic failure can change 1 to 0; spontaneous spikes can change 0 to 1.
One can control the level of error and indicate the length of spike trains from that. 

In a binary system,
$$2^{M_c}\geqslant 2^M{M_c\choose k}  = 2^M\frac{M_c!}{k!(M_c-k)!}$$
in which M is the length of message bits, $M_c$ is the length of coding bits, k is the length of error bits.

Assume an error rate $\epsilon < 1/2$
$$k \approx \epsilon M_c$$
after taking a logarithm to the base of 2:
$$ln \ {2^{M_c}}\geqslant ln \{2^M\frac{M_c!}{{\epsilon M_c}!(M_c-\epsilon M_c)!}\}$$
after some derivations:
$$\frac{M} {M_c} = 1 + [ \,\epsilon log_2(\epsilon) + (1-\epsilon)log_2(1-\epsilon)]\,$$
which increases with the error probability $\epsilon$.

With $M_c$ as the entropy of encoded string:
- total energy cost to set a message:
$$M_c k T ln2$$
- average energy cost for error correction:
$$M_c k T ln2 \{ \epsilon \ log_2 (1/ \epsilon)\ + (1-\epsilon) \ log_2 (1/(1-\epsilon))\}$$
- energy not wasted:
$$M_c k T ln2 \{ 1+\epsilon \ log_2 (1/ \epsilon)\ + (1-\epsilon) \ log_2 (1-\epsilon)\}$$
- maximum information:
$$M_c \{ 1 + \epsilon \ log_2 (\epsilon)\ + (1-\epsilon) \ log_2 (\epsilon)\}$$
- error entropy:
$$- M_c [\, \epsilon \ log_2(\epsilon) + (1-\epsilon) \ log_2(1-\epsilon)]\ $$


## Information and Entropy - Part 2
### Information and Entropy
Because information should be addictive for independent events:
$$p(r_1, r_2) = p(r_1)p(r_2)$$
i.e. the corresponding information should be:
$$I(r_1, r_2) = I(r_1) + I(r_2)$$
so the information can have log base:
$$I(r) = -log\ p(r)$$
using log base2, it can be turned into digits with unit bits:
$$I_r = -log_2 \ p(r)$$ 

The surprise or unpredictability (in units of "bits") associated with a  particular response is:
$$h(P[r]) = -log_2P[r]$$
Then, entropy is just the information averaged over all possible responses
$$H = <I>_r = -\sum p(r_i)\ log_2 p(r_i)$$
which measures availabvle information or variability of a distribution.

Several features of information and entropy:
- additivity: $h(P[r_1]P(r_2)) = h(P[r_1]) + h(P[r_2])$ for independent responses $r_1$ and $r_2$.
- for a single response, $h(P[r])$ decreases with $P(r)$, because low probability responses are more surprising than high probability responses.
- If you observe the relationship between the propability $p$ and the informartion $H$, you will find that response with a fair frequency (not too low/high because the inform) contribute most to the entropy.
### Entropy for Continuous Variables
For a continuous response, probability of response between $r$ and $r+\Delta r$ is expressed in terms of probability density $p(r) \Delta r$, the information is:
$$H = \lim_{\Delta r -> 0} (-\sum p(r) \Delta r \ log_2(p(r) \Delta r)) = \lim_{\Delta r -> 0} (-\sum p(r) \Delta r \ log_2 p(r) - log_2 \Delta r) $$
Problem: $log_2 \Delta r$ diverges for $\Delta r -> 0$
$$\lim_{\Delta r -> 0} (H + log_2 \Delta r) = \lim_{\Delta r -> 0} (-\sum p(r) \Delta r \ log_2 p(r))$$
then the estimated infomation H is
$$\hat H = \lim_{\Delta r -> 0} (H + log_2 \Delta r) = - \int dr \ p(r) log_2p(r)$$
in which the $\Delta r$ is the resolution limit with which $r$ can be measured.
Entropy differences are independent of $\Delta r$.

### Entropy rate 
With the duration T, i.e. the spike train length considering no more than one spike per bin of a spike train.
#### Entropy rate [bit/s] 
$$h = \frac{H}{T} $$
#### Entropy per spike [bit/spike]
$$h = \frac{H}{<r>T}$$

## Mutual Information
Entropy is a measure of the theoretical capacity of a code to convey information. Mutual information measures how much of that capacity is actually used when the code is employed to describe a particular set of data. Entropy is a measure of response variability, but it does not tell us anything about the source of that variability - which can be done by mutual information. 

Mutual information is the information about the stimulus in the reponse. It is the difference between the total response entropy and the average response entropy on trials that involve repetitive presentation of the same stimulus:

$$I_m(R; S) = H(R) - H(R|S) = \int \int p(r,s) log_2 \frac{p(r,s)}{p(r)p(s)} ds dr$$
which means the information of $R$ about $S$ equals the information of $S$ about $R$ (symmetric).

- If $r$ and $s$ are independent, i.e. $p(r,s) = p(r)p(s)$, then  $$I_m(R; S) = 0$$
- If $r$ is uniquely determined for each $s$: $I_m(R;S) = -\int p(s)log_2 p(s) ds = H(S)$

> Derivation of mutual information:
> 
> The entropy of the responses to a given stimulus is:
> $$H_s = -\sum _r P[r|s]\ log_2 P[r|s]$$
> If we average this quantity over all the stimuli, we obtain a quantity called the noise entropy:
> $$H_{noise} = \sum _s \ P[s]H_s =  -\sum _{s,r} P[s]P[r|s]\ log_2 P[r|s]$$
> This is the entropy associated with that part of the response variability that is not due to changes in the stimulus, but arises from other sources. 
> 
>  Thus, the mutual information is obtained by subtracting the noise entropy from the full response entropy:
>  $$I_m = H - H_{noise} = - \sum P[r]log_2P[r] + \sum _{s,r} P[s]P[r|s]\ log_2 P[r|s] =  \sum p[r,s] log_2 \frac{p[r,s]}{p[r]p[s]} $$


### Kullback-Leibler Divergence
The mutual information is related to a measure used in statistics called the  Kullback-Leibler (KL) divergence. 
$$D_{KL} (P(x); Q(x)) = \int p(x) log_2 \frac{p(x)}{q(x)} dx$$
The $D_{KL} (P; Q) \geq 0$ with equality if and only if $P=Q$. 

Divergence: The additional uncertainty induced by using probabilities from one distribution to describe another distribution.

Mutual information is the KL divergence between the joint distribution of $S$ and $R$ and their product distribution (i.e. the case of independent $S$ and $R$) (to check if the distributions are dependent)

The fact that $D_{KL} (P; Q) \geq 0$  proves that the mutual information cannot be negative. In addition, it can never be larger than either the full response entropy or the entropy of the stimulus set.

### Bonus: mutual information vs. Fisher information
- The Fisher information is a local measure because it depends on the expected curvature of the likelihood $P[r|s]$ (typically for the responses of many cells) evaluated at the true stimulus value. 
- The mutual information is a global measure in the sense that it depends on the average overall uncertainty in the decoding distribution $p[s|r]$, including values of $s$ both close to and far from the true stimulus.

If the decoding distribution $p[s|r]$ has a single peak about the true stimulus, the Fisher information and the mutual information are closely related.
### Kullback-Leibler Divergence
^aa57f9
$$D_{KL} (P(x); Q(x)) = \int p(x) log_2 \frac{p(x)}{q(x)} dx$$
Mutual information is the KL divergence between the joint distribution of $S$ and $R$ and their product distribution (i.e. the case of independent $S$ and $R$) (to check if the distributions are dependent)

### Maximizing the mutual information (for populations of neurons): Redundancy reduction
Since $$I_m(R;S) = H(R) - H(R|S)$$
If $R=f(S)+N$ with $f$ invertible, $N$ additive noise:
$$H(R|S) = H(N)$$
in this case, maximizing $I_m$ is equivalent to maximizing the response entropy $H(R) =  -\sum P[r]log_2P[r]$.

An efficient way of maximizing information transmission is redundancy reduction, i.e. minimizing mutual information between the outputs, i.e. decorrelation.

**What would be efficient codes?**
Given stimuli $s$, find linear transformation $W$
$$u=Ws$$
such that the covariance matrix of the outputs, $<u u^T>$, is diagonal, i.e. no correlations between the $u_i$. 
> covariance matrix is diagonal = no correlations

Assuming $<u u^T> = \bold I$,
$$W^T W = <ss^T>^{-1}$$
For a given set of stimuli, $W$ is not uniquely determined, seevral solutions are possible:
#### Decorrelation 1: Whitening (ZCA)
solution 1: $W$ symmetrical ($W^T = W$)
$$W_z = <s s^T>^{-1/2}$$
- typically localized filters
- for natural images: DoG-like filters.
#### Decorrelation 2: PCA
solution 2: $W$ orthogonal ($W^T = W$)
$$W_P = D^{-1/2} E^T$$
with $E$ the matrix of eigenvectors of the covariance matrix and $D$ the diagonal matrix of eigenvalues.
- corresponds to rotation
- typically global filters
#### Decorrelation 3: ICA (Independent component analysis)
Decorrelation with the additional constraint that the probability distributions of the outputs factorize
remove higher-order
needs a learning rule
ICA find more independent component (comparison of decorrelation methods: joint and product distribution looks more similar than other pairs)
 


constant stimulus -> more irregular spikes

e.g.
only a small fraction of information is in stimulus-reponse correlation


## Information and Entropy - Example of the blowfly large monopolar cell (LMC)

### Entropy maximization for a single neuron
Recall the entropy is 
$$H = - \int dr \ p(r) log_2p(r) - log_2 \Delta r$$
in which $log_2 \Delta r$ is a held fixed. To maximize the entropy, we must find a $p[r]$ that maximizes
$$- \int _0 ^{r_{max}} dr \ p(r) log_2 \ p(r) $$ 
with $r_{max}$ as the maximum firing rate of the studied neuron. Also, remember that $p[r]$ subject to the constraint
$$\int _0 ^{r_{max}} dr\ p[r]=1$$
With some derivations, one can get the probability that maximizes entropy (independent of $r$)
$$p[r] = \frac {1}{r_{max}}$$
which corresponds to **histogram equalization**.
Then the entropy is 
$$H = log_2 \ r_{max} - log_2 \Delta r = log_2 \ (\frac{r_{max}}{\Delta r})$$

### Histogram equalization
It is a signal-processing technique. Applied to neural responses, this is a procedure for tailoring the neuronal selectivity so that $p[r]=1/r_{max}$in response to a set of stimuli over which the entropy is to be maximized.

Suppose a neuron responds to a stimulus characterized by the parameters by firing at a rate $r=f(s)$. 

For small $s$, the probability that the continuous stimulus variable falls in the range between $s$ and $s+\Delta s$ is given in terms of the stimulus probability density by $p[s] \Delta s$. This produces a response that falls in the range between $f(s+\Delta s)$ and $f(s)$.  

If the response probability density takes its optimal value, $p[r]=1/r_{max}$, the probability that the response falls within this range is $|f(s+\Delta s)−f(s)|/r_{max}$. 

Setting these two probabilities equal to each other, we find that$p[s] \Delta s = |f(s+\Delta s)−f(s)|/r_{max}$.

In the limit $\Delta s \rarr 0$, the equalization condition becomes
$$\frac {df}{ds} = r_{max}p[s]$$
which has the solution
$$f(s) = r_{max} \int _{S_{min}} ^S ds' p[s']$$
where $s_{min}$ is the minimum value of $s$, which is assumed to generate no response. 

Thus, entropy maximization requires that **the average firing rate of the responding neuron be proportional to the integral of the probability density of the stimulus**.

### Example: fly's LMC
Laughlin (1981) has provided evidence that responses of the large monopolar cell  (LMC)  in  the  visual  system  of  the fly  satisfy  the  entropy-maximizing condition. 
The LMC responds to contrast, and Laughlin measured the probability distribution of contrasts of natural scenes in habitats where the flies he studied live.  
**The response as a function of contrast is very close to the integrated probability density**, suggesting that the LMC is using a maximum entropy encoding.amll fraction of information is in stimulus-reponse correlation


