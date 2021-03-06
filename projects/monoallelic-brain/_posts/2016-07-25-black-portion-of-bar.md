---
layout: default
tags: [ andy, manuscript ]
title: Interpretation of the Black Bars
---

What is the precise meaning of the sentence below, taken from [Ifat's manuscript][ifat]?

>The black portion of each bar represents the fraction of individuals with evidence for biallelic expression (where the observed $$S_g$$ is close to 0.5 and the 95% confidence interval given the observed read counts does not include 0.7)

## My reading

The intention must have been to test if gene $$g$$ is biallelically expressed in individual $$i$$.  But the sentence in question may be understood in two ways (Interpretation A and B).  Before discussing those cases I start with an assumption that was made (personal communication with Andy).

### Binomial assumption

For individual $$i$$ and gene $$g$$, the statistic $$S_{ig}$$ is assumed to be distributed as $$\mathrm{Binom}(n_{ig}, \theta_{ig})$$.  The two parameters in this binomial distribution are the observed total read count $$n_{ig}$$ and $$\theta_{ig}$$, which is the expected proportion of higher read counts in $$n_{ig}$$.  Note that  $$\theta_{ig}$$ is a **parameter**, an unobservable ( theoretical) quantity, while its counterpart $$S_{ig} / n_{ig}$$ is a **statistic**, an observable quantity, and that parameters have confidence intervals while statistics prediction intervals.

### Interpretation A: Classical hypothesis testing

In this case we have the null hypothesis $$H_0$$ that $$\theta_{ig} = 1/2$$.  $$H_0$$ models an ideally behaved (perfectly balanced) biallelically expressing gene.  Then, what was really meant instead of confidence interval for some parameter was indeed the **prediction** interval for presumably the $$S_{ig}/n_{ig}$$ statistic.  The 95 % prediction interval provides us a rule for testing $$H_0$$: if the observed $$s_{ig}/n_{ig}$$ falls in that interval we accept $$H_0$$ otherwise we reject it at significance level $$0.05$$.

The 95 % prediction interval can be calculated as follows. Let $$F_{ig}$$ be the cumulative distribution function (CDF) of the $$\mathrm{Binom}(n_{ig}, 1/2)$$ distribution and let  $$F_{ig}^{-1}$$ be the quantile function (inverse CDF).  Then the 95 % prediction interval may be given as $$[F_{ig}^{-1}(0.025), F_{ig}^{-1}(0.975)]$$.  However, independently of $$H_0$$ we are certain that $$S_{ig}/n_{ig}\ge 1/2$$ due to the definition of $$S_{ig}$$.  Thus the prediction interval that expresses this certainty is $$[1/2, F_{ig}^{-1}(0.95)]$$.

### Interpretation B: Hypothesis testing based on confidence interval

If indeed confidence interval was meant in the sentence that would obviously be an interval for $$\theta_{ig}$$, which is treated as unknown unlike in case A where we hypothesized that $$\theta_{ig} = 1/2$$.  The value 0.7 can be considered as the threshold that divides the null hypothesis $$0.5 \le \theta_{ig} \le 0.7$$ (biallelic expression) from the alternative hypothesis $$0.7 < \theta_{ig} \le 1$$ (monoallelic expression).  Then a sensible rule may be to

1. accept the null hypothesis when the confidence interval is contained in $$[0.5, 0.7)$$ and mark individual $$i$$ *black*
2. accept the alternative hypothesis when it is $$\subset (0.7, 1]$$ and mark $$i$$ with *a second color*
3. otherwise, accept neither hypotheses i.e remain "ignorant" and mark $$i$$ with a *third color*, say gray

Note that only in the 3rd case is 0.7 contained in the confidence interval so that under both the null and alternative hypothesis "the confidence interval does not include 0.7", as the sentence prescribes, which however makes little sense.  Perhaps what was meant in the original sentence is that the confidence interval $$\subset [0.5, 0.7)$$, I wonder.

Calculation of confidence intervals may be done various ways in general.  For the $$\theta_{ig}$$ the best way is to use the fact that the log likelihood is asymptotically chi-square distributed.

## Conclusion

Interpretation A and B both conform the sentence in question.  They have quite different interpretations, though, and involve very different calculations.  What semantics the sentence really has should turn out from the Excel formula that was used to calculate the "black bars".

[ifat]: https://docs.google.com/document/d/1cWd4UH98SJR5lihDihC0ZO-C_A1-8MQ5COcixxCLzHE/edit
<!-- MathJax scripts -->
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
