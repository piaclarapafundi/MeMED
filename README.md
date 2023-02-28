# MeMED
Sample size calculation

#### MeMED Sample size calculation for sensitivity of MeMED with respect to procalcitonin in pediatric respiratory infections

# HYPOTHESIS
Sensitivity improvement of +/-7%

# Power calculations for a diagnostic test
install.packages("MKpower")
library(MKpower)

#power.diagnostic.test(...) 
#Compute sample size, power, delta, or significance level of a diagnostic test for an expected sensititivy or specificity.

# power.diagnostic.test(sens = NULL, spec = NULL,
#                      n = NULL, delta = NULL, sig.level = 0.05,
#                      power = NULL, prev = NULL, 
#                      method = c("exact", "asymptotic"),NMAX = 1e4)

#sens or spec: Expected sensitivity/specificity (either sens or spec has to be specified). 
#delta: sens-delta resp. spec-delta is used as lower confidence limit
#sig.level: Significance level (Type I error probability)
#power: Power of test (1 minus Type II error probability)
#prev: Expected prevalence (if NULL, it means prev = 0.5 is assumed)
#method: exact or asymptotic formula; default "exact".
#NMAX: Maximum sample size considered in case method = "exact".

power.diagnostic.test(sens = 0.90, #expected sensitivity, i.e. at least that of procalcitonin
                      n = NULL, 
                      delta = 0.15, ##sens-delta will be used as lower confidence limit
                      sig.level = 0.05, #type I error
                      power = 0.80, #1 minus Type II error probability
                      prev = 0.20, #estimated mean prevalence of disease between 1 month and 10 years of age
                      method = "exact") #default method, it returns integer n

# OUTPUT
Diagnostic test exact power calculation 

           sens = 0.9
              n = 50
             n1 = 200
          delta = 0.15
      sig.level = 0.05
          power = 0.8
           prev = 0.2

# NOTE: n is number of cases, n1 is number of controls

# Citation
citation(package = "MKpower")
Kohl M (2020). _MKpower: Power Analysis and Sample Size Calculation_. R package version 0.5, <http://www.stamats.de>.

# R software citation
citation()
R Core Team (2022). R: A language and environment for statistical computing. R Foundation for Statistical Computing, Vienna, Austria. URL https://www.R-project.org/.
