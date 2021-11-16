---
content_type: page
parent_title: 1.3 Order of Accuracy
parent_uid: a3fbfbbd-e140-393b-aed5-af945a9316f9
title: 1.3 Order of Accuracy
uid: 58553753-c9cc-c012-f030-d87844ae8db5
---

*   [<Local Order of Accuracy]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-order-of-accuracy)
*   [1.3.1Errors]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy)
*   [1.3.2Local Truncation Error]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-truncation-error)
*   [1.3.3Local Order of Accuracy]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-order-of-accuracy)
*   [1.3.4Definition of Multi-Step Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-definition-of-multi-step-methods)
*   [1.3.5Example of Most Accurate Multi-Step Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-example-of-most-accurate-multi-step-method)
*   [\>Example of Most Accurate Multi-Step Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-example-of-most-accurate-multi-step-method)

1.3.4 Definition of Multi-Step Methods
--------------------------------------

[Measurable Outcome 1.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorM15), [Measurable Outcome 1.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorM18), [Measurable Outcome 1.13]({{< baseurl >}}/pages/measurable-outcome-index/#anchorM113), [Measurable Outcome 1.15]({{< baseurl >}}/pages/measurable-outcome-index/#anchorM115)

The class of finite difference methods known as multi-step methods is one of the most widely-used approaches for solving ordinary differential equations, and forms the basis for solving partial differential equations as well.

Definition of Multi-Step Methods
--------------------------------

The generic form of an \\(s\\)-step multi-step method is,

| \\\[v^{n+1} + \\sum \_{i=1}^ s \\alpha \_ i v^{n+1-i} = {\\Delta t}\\sum \_{i=0}^ s \\beta \_ i f^{n+1-i}.\\\] | (1.51) 

A multi-step method with \\(\\beta \_0 = 0\\) is known as an **explicit** method since in this case the new value \\(v^{n+1}\\) can be determined as an explicit function of known values (i.e. from \\(v^ i\\) and \\(f\_ i\\) with \\(i \\leq n\\)). A multi-step method with \\(\\beta \_0 \\neq 0\\) is known as an **implicit** method since in this case the new value \\(v^{n+1}\\) is an implicit function of itself through the forcing function, \\(f^{n+1} = f(v^{n+1},t^{n+1})\\). We defer implicit methods to Section [1.7.1]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods) and focus on explicit methods here.

**Exercise 1** What are the non-zero \\(\\alpha \_ i\\) and \\(\\beta \_ i\\) for the forward Euler method?

Exercise 1

 \\(\\alpha \_1=-1, \\beta \_1=1\\)

 \\(\\alpha \_1=1, \\beta \_1=2\\)

 \\(\\alpha \_2=-1, \\beta \_1=2\\)

 \\(\\alpha \_1=-1, \\beta \_1=2\\)

Answer:

Using the notation given above, the forward Euler method is:

| \\\[\\alpha \_1 = -1 \\quad \\mbox{all other} \\quad \\alpha \_ i = 0\\\] | (1.52) | \\\[\\beta \_1 = 1 \\quad \\mbox{all other} \\quad \\beta \_ i = 0\\\] | (1.53) 

**Exercise 2** What are the non-zero \\(\\alpha \_ i\\) and \\(\\beta \_ i\\) for the Midpoint method?

Exercise 2

 \\(\\alpha \_1=-1, \\beta \_1=1\\)

 \\(\\alpha \_1=1, \\beta \_1=2\\)

 \\(\\alpha \_2=-1, \\beta \_1=2\\)

 \\(\\alpha \_1=-1, \\beta \_1=2\\)

CheckShow Answer

Answer:

Using the notation given above, the midpoint method is:

| \\\[\\alpha \_2 = -1 \\quad \\mbox{all other} \\quad \\alpha \_ i = 0\\\] | (1.54) | \\\[\\beta \_1 = 2 \\quad \\mbox{all other} \\quad \\beta \_ i = 0\\\] | (1.55) 

BackLocal Order of Accuracy ContinueExample of Most Accurate Multi-Step Method