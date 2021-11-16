---
content_type: page
parent_title: 3.3 Monte Carlo Methods
parent_uid: 2733fa33-374f-cb88-814c-413cb75b3483
title: 3.3 Monte Carlo Methods
uid: 2ff49897-a168-59d4-5d17-feb89ff6fae6
---

*   [<Monte Carlo Analysis]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-analysis)
*   [3.3.1Introduction]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods)
*   [3.3.2Monte Carlo Analysis]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-analysis)
*   [3.3.3Monte Carlo Example]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-example)
*   [3.3.4Inversion Method for Sampling]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-inversion-method-for-sampling)
*   [\>Inversion Method for Sampling]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-inversion-method-for-sampling)

3.3.3 Monte Carlo Example
-------------------------

[Measurable Outcome 3.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO33), [Measurable Outcome 3.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO35)

To demonstrate the Monte Carlo simulation method in more detail, let's consider the specific case where the thermal barrier coating in the previous turbine blade example is known to be uniformly distributed from \\(0.00025m < L\_{TBC} < 0.00075m\\) as shown from the probability density function (PDF) of LTBC in Figure [3.3]({{< baseurl >}}/resources/ltbc_uniform).

![The graph shows a line begins at 0 PDF(LTBC), which goes to 2000 PDF(LTBC), and returns to 0 PDF(LTBC).](BASEURL_PLACEHOLDER/resources/ltbc_uniform)

**Figure 3.3**: Probability density function (PDF) of \\(L\_{TBC}\\) uniformly-distributed from 0.00025m < \\(L\_{TBC}\\) <0.00075m

The first step is to generate a random sample of \\(L\_{TBC}\\). The basic approach relies on the ability to generate random numbers that are uniformly distributed from 0 to 1. This type of functionality exists within many different scientific programming environments or languages. In MATLAB®, the command rand returns a random number that is uniformly distributed from 0 to 1. Then, using the uniform distribution from 0 to 1, a uniform distribution of \\(L\_{TBC}\\) over the desired range can be created,

| \\\[L\_{TBC} = 0.00025 + 0.0005 U\\\] | (3.26) 

where \\(U\\) is a random variable uniformly distributed from 0 to 1.

This approach is used to create the samples shown as histograms in Figure 21.3 for samples of size \\(N\\) = 100, 1000, and 10000. For the smaller sample size (specifically \\(N\\) = 100), the fact that the sample was drawn from a uniform distribution is not readily apparent. However, as the number of samples increases, the uniform distribution becomes more evident. Clearly, the sample size will have a direct impact on the accuracy of the probabilistic estimates in the Monte Carlo method.

![The figure is a histogram of a random sample from a uniformly-distributed LTBC for a sample size of N=100.](BASEURL_PLACEHOLDER/resources/ltbc_n100) ![The figure is a histogram of a random sample from a uniformly-distributed LTBC for a sample size of N=1000.](BASEURL_PLACEHOLDER/resources/ltbc_n1000) ![The figure is a histogram of a random sample from a uniformly-distributed LTBC for a sample size of N=10000.](BASEURL_PLACEHOLDER/resources/ltbc_n10000)

**Figure 3.4**: Histogram of a random sample from a uniformly-distributed \\(L\_{TBC}\\) for a sample size of N=100,1000,and 10000.

The following is a MATLAB script that implements the Monte Carlo method for this uniform distribution of \\(L\_{TBC}\\). The distributions of \\(T\_{mh}\\) shown in Figure 3.5 correspond to the \\(L\_{TBC}\\) distributions shown in Figure 3.4 and were generated with this script.

clear all; 
hgas = 3000; 
Tgas = 1500; 
ktbc = 1; 
km = 20; 
Lm = 0.003; 
hcool = 1000; 
Tcool = 600; 
N = 100; 
Ltbc = zeros(N,1); 
Tmh = zeros(N,1); 
for n = 1:N, Ltbc(n) = 0.00025 + 0.0005\*rand; 
\[Ttbc, Tmh(n), Tmc, q\] = blade1D(hgas, Tgas, ktbc, Ltbc(n), km, Lm, hcool, Tcool); 
end figure(1); 
hist(Ltbc,20); 
xlabel('\\(L\_{tbc}\\) (m)'); 
figure(2); 
hist(Tmh,20); 
xlabel('\\(T\_{mh}\\) (K)'); 

![The figure is a histogram of Tmh, given a uniformly distributed LTBC for a sample size of N=100.](BASEURL_PLACEHOLDER/resources/tmh_n100) ![The figure is a histogram of Tmh, given a uniformly distributed LTBC for a sample size of N=1000.](BASEURL_PLACEHOLDER/resources/tmh_n1000) ![The figure is a histogram of Tmh, given a uniformly distributed LTBC for a sample size of N=10000.](BASEURL_PLACEHOLDER/resources/tmh_n10000)

**Figure 3.5**: Histogram of \\(T\_{mh}\\), given a uniformly-distributed \\(L\_{TBC}\\), for a sample size of N=100,1000,and 10000

Consider the third plot in Figure [3.5](javascript: void(0)). If we choose a sample corresponding to \\(L\_{TBC}\\)=3, in which region of the output histogram do you expect the corresponding \\(T\_{mh}\\) to lie ?

Exercise 1

&nbsp; \\(\[1060, 1100\]\\) &nbsp;

&nbsp; \\(\[1100, 1150\]\\) &nbsp;

&nbsp; \\(\[1150, 1200\]\\) &nbsp;

CheckShow Answer

Answer:

For any given value of \\(L\_{TBC}\\), \\(T\_{mh}\\) is inversely proportional to \\(L\_{TBC}\\), the thicker the barrier coating, the lower \\(T\_{mh}\\) will be.

BackMonte Carlo Analysis ContinueInversion Method for Sampling