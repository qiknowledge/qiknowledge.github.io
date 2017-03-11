## Common used function and commands in R

* ## Survival Analysis
  - let $f(t)$ be the probability density function (p.d.f) of event time _T_. Then $F(t)$ represents $S(t) = Pr(T>t) = 1-Pr(T \leq t) = 1 -\int_o^tf(u)du$![](assets\2017-03-09-18-07-20.png)
  ![](assets\2017-03-09-18-06-13.png)
  ![](assets\2017-03-09-18-08-13.png)
  ![](assets\2017-03-09-18-09-27.png)
  ![](assets\2017-03-09-18-11-07.png)
  ![](assets\2017-03-09-18-14-36.png)
  - The `hazard rate` is referred to as the force of mortality, the intensity rate, or the instantaneous risk. By Equation (1.6) , the hazard rate is mathematically defined as the derivative of the log survival probability at time t multiplied by − 1. As a survival function is monotonically decreasing, the hazard function is nonnegative but not necessarily smaller than or equal to one. Therefore, as the standardized p.d.f., the hazard rate is a conditional probability rate. It is essential for the reader to comprehend the concept and the underlying properties of the hazard function because most survival models described in later chapters are created on the hazard rate.
  ![](assets\2017-03-09-18-21-36.png)
  ![](assets\2017-03-09-18-22-04.png)


  - There are three main types of censoring: `right, left, and interval`. Censoring could occur, for example, when administering a survey to mothers every other month asking if they are still breast feeding. Right censoring occurs when mothers are still breast feeding after the last survey, since we do not know exactly how long they will continue. Left censoring occurs when mothers enter the study after they have stopped breast feeding. We do not know exactly when they stopped breast feeding, although we know that it happened before their entry to the study. Interval censoring occurs if the breast feeding ended between two successive surveys since one can only say that breast feeding ended somewhere within the past two months. 
  - Simple approaches researchers might choose to deal with censored data are to set the censored observations to missing or replace the unobserved value of the variable by zero, the minimum, maximum, mean value, or a randomly assigned value from the range of possible values. When the censoring is minimal, using one of these approaches can be reasonable. When it is not, these simple solutions can, however, cause serious bias in estimates and standard errors obtained in subsequent statistical analysis, can discard potent
  - <div style="background-color:red">The logistic regression, for example, can be applied to estimate the probability of experiencing a particular lifetime event within a limited time period; nevertheless, it does not consider the time when the event occurs and therefore disregards the length of the survival process. Suppose that two population groups have the same rate of experiencing a particular event by the end of an observation period but members in one group are expected to experience the event significantly later than do those in the other. The former population group has an advantaged survival pattern because its average life is extended. Obviously,the logistic regression ignores this timing factor, therefore not providing precise information.</div>
  - ### Kaplan-Meier survival estimates
    ![](assets\2017-03-09-16-55-11.png)
