---
content_type: page
parent_title: 3.3 Monte Carlo Methods
parent_uid: 2733fa33-374f-cb88-814c-413cb75b3483
title: 3.3 Monte Carlo Methods
uid: e4ed709d-1333-d460-e932-cde246cff19f
---

*   [<Monte Carlo Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods)
*   [3.3.1Introduction]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods)
*   [3.3.2Monte Carlo Analysis]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-analysis)
*   [3.3.3Monte Carlo Example]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-example)
*   [3.3.4Inversion Method for Sampling]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-inversion-method-for-sampling)
*   [\>Monte Carlo Example]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-example)

3.3.2 Monte Carlo Analysis
--------------------------

[Measurable Outcome 3.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO33), [Measurable Outcome 3.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO35)

In this lecture, we begin our exploration of probabilistic methods, i.e., numerical methods that are used to quantify the impact of uncertainty. In particular, we will focus on the Monte Carlo method, since it is the most common probabilistic analysis method and is the foundation for many others.

Why are probabilistic methods important for engineering analysis and design? More and more there is a realization of the importance of analyzing and managing uncertainty in engineering systems. There are many sources of uncertainty, including uncertain technology performance (especially for advanced technologies whose performance may not be proven in the field), variability due to manufacturing processes, uncertain operating conditions (e.g., weather conditions, wind gusts), and uncertainty due to limitations in the models we use. To be able to design robust, reliable, high-performance systems, we need to be able to analyze how all these different sources of uncertainty affect our system.

To make our discussion concrete, we will consider a simplified model for the heat transfer through a cooled turbine blade as shown in Figure [3.2]({{< baseurl >}}/resources/turb_blade2).

![The schematic shows a cross-section of a turbine blade, where the wider part of the blade is labeled Tcool, and the inner, thinner part of the blade is labeled as thermal barrier.](BASEURL_PLACEHOLDER/resources/turb_blade2)

**Figure 3.2**: Turbine blade heat transfer example.

A one-dimensional model of the heat transfer along the dashed line is,

| \\\[\\dot{q} = h\_{gas} (T\_{gas} - T\_{TBC}) \\\\ \\dot{q} = \\frac{k\_{TBC}}{L\_{TBC}} (T\_{TBC} - T\_{mh}) \\\\ \\dot{q} = \\frac{k\_ m}{L\_ m} (T\_{mh} - T\_{mc}) \\\\ \\dot{q} = h\_{cool} (T\_{mc} - T\_{cool})\\\] | (3.23) 

where \\(h\_{gas}\\) and \\(h\_{cool}\\) denote the convective heat transfer coefficients of the flow surrounding the blade and the cooling flow inside the blade, respectively. \\(k\_ m\\) is the thermal conductivity of the metal and \\(L\_ m\\) is the blade metal thickness. \\(k\_{TBC}\\) is the thermal conductivity of the thermal barrier coating on the blade and \\(L\_{TBC}\\) is the thickness of the thermal barrier coating. \\(T\\) denotes temperature, where the subscripts are \\(\_{gas}\\) for the flow surrounding the blade, \\(\_{TBC}\\) for the thermal barrier coating, \\(\_{mh}\\) for the metal hot side, \\(\_{mc}\\) for the metal cold side, and \\(\_{cool}\\) for the cooling fluid.

Then, given the values of \\(h\_{gas}\\), \\(T\_{gas}\\), \\(k\_{TBC}\\), \\(L\_{TBC}\\), \\(k\_ m\\), \\(L\_ m\\), \\(h\_{cool}\\), and \\(T\_{cool}\\), we can solve these four equations to determine, \\(T\_{TBC}\\), \\(T\_{mh}\\), \\(T\_{mc}\\), and \\(\\dot{q}\\). In the design of cooled turbine blades, a key measure of system performance is the hot-side metal temperature, \\(T\_{mh}\\), because as this temperature increases, the durability (usable life) of a blade decreases. Thus, the goal of the heat transfer design is to maintain the metal temperatures at an acceptably low value while minimizing cost.

Nominal Analysis of Turbine Blade Heat Transfer
-----------------------------------------------

A typical, deterministic analysis of the turbine blade heat transfer problem would assume that all of the input parameters are at their nominal (i.e., design-intent) values. Suppose the design-intent values were,

| \\(\\displaystyle\\hspace{9.9mm}{h\_{gas} = 3000W/(m^2K) \\hspace{.5mm} \\text{,} \\hspace{4mm} h\_{cool} = 1000W/(m^2K)\\hspace{.5mm} \\text{,}\\\\ \\hspace{9.9mm}T\_{gas} = 1500K \\hspace{.5mm} \\text{,} \\hspace{4mm} T\_{cool} = 600K\\hspace{.5mm} \\text{,}\\\\ \\hspace{9.9mm}k\_{TBC} = 1W/(mK) \\hspace{.5mm} \\text{,} \\hspace{4mm} k\_{m} = 20W/(mK)\\hspace{.5mm} \\text{,}\\\\ \\hspace{9.9mm}L\_{TBC} = 0.0005m \\hspace{.5mm} \\text{,} \\hspace{4mm} L\_{m} = 0.003m }\\) | (3.24) 

The results of this design-intent analysis give,

| \\\[T\_{TBC} = 1348.7 K, \\quad T\_{mh} = 1121.8 K, \\quad T\_{mc} = 1053.8 K,\\quad \\dot{q} = 453780 W/m^2\\\] | (3.25) 

Analysis of Turbine Blade Heat Transfer Under Uncertainty
---------------------------------------------------------

Due to manufacturing variability, the parameters of the actual manufactured blades are not exactly the design-intent values but rather are distributed over a range of values. For example, due to the difficulty of applying the thermal barrier coating on the outside of the blades, the thickness of the thermal barrier coating is variable.

The role of probabilistic methods is to quantify the impact of this type of variability on properties of interest (e.g., the hot-side metal temperature). The results of the probabilistic analysis can take many forms depending on the specific application. In the example of the turbine blade where the hot-side metal temperature is critical, the following information might be desired from a probabilistic analysis:

1.  The distribution of \\(T\_{mh}\\) that would be observed in the population of manufactured blades.
    
2.  The probability that \\(T\_{mh}\\) is above some critical value (indicating the blade's life will be unacceptably low).
    
3.  Instead of determining the entire distribution of \\(T\_{mh}\\), sometimes knowing the mean value, \\(\\mu \_{T\_{mh}}\\), is sufficient.
    
4.  To have some indication of the variability of \\(T\_{mh}\\) without requiring accurate estimation of the entire distribution, the standard deviation, \\(\\sigma \_{T\_{mh}}\\), can be used.
    

The Monte Carlo method is based on the idea of taking a small, randomly-drawn sample from a population and estimating the desired outputs from this sample. For the outputs described above, this would involve:

1.  Replacing the distribution of \\(T\_{mh}\\) that would be observed over the entire population of manufactured blades with the distribution (i.e., histogram) of \\(T\_{mh}\\) observed in the random sample.
    
2.  Replacing the probability that \\(T\_{mh}\\) is above a critical value for the entire population of manufactured blades with the fraction of blades in the random sample that have Tmh greater than the critical value.
    
3.  Replacing the mean value of \\(T\_{mh}\\) for the entire population with the mean value of the random sample.
    
4.  Replacing the standard deviation of \\(T\_{mh}\\) for the entire population with the standard deviation of the random sample.
    

In Summary
----------

In the next unit, we will see how to carry out this analysis using Monte Carlo simulation. In summary, our probabilistic analysis involves three steps:

1.  Generate a random sample of the input parameters according to the (assumed) distributions of the inputs.
    
2.  Analyze (deterministically) each set of inputs in the sample.
    
3.  Estimate the desired probabilistic outputs (e.g., mean, standard deviation), and the uncertainty in these outputs, using the random sample.
    

BackMonte Carlo Methods ContinueMonte Carlo Example