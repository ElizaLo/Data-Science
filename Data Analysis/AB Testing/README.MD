# A/B Testing

## Terminology

- **Overall Evaluation Criterion (OEC).** A quantitative measure of the experiment’s objective. In statistics this is often called the Response or Dependent Variable; other synonyms include Outcome, Evaluation metric, Performance metric, or Fitness Function. Experiments may have multiple objectives and a scorecard approach might be taken, although selecting a single metric, possibly as a weighted combination of such objectives is highly desired and recommended. A single metric forces tradeoffs to be made once for multiple experiments and aligns the organization behind a clear objective. A good OEC should not be short-term focused (e.g., clicks); to the contrary, it should include factors that predict long-term goals, such as predicted lifetime value and repeat visits. Ulwick describes some ways to measure what customers want (although not specifically for the web).
- **Factor.** A controllable experimental variable that is thought to influence the OEC. Factors are assigned **Values**, sometimes called **Levels** or **Versions**. Factors are sometimes called **Variables**. In simple A/B tests, there is a single factor with two values: A and B.
- **Variant.** A user experience being tested by assigning levels to the factors; it is either the Control or one of the Treatments. Sometimes referred to as **Treatment**, although we prefer to specifically differentiate between the Control, which is a special variant that designates the existing version being compared against and the new Treatments being tried. In case of a bug, for example, the experiment is aborted and all users should see the Control variant.
- **Experimentation Unit.** The entity on which observations are made. Sometimes called an item. The units are assumed to be independent. On the web, the user is the most common experimentation unit, although some experiments may be done on sessions or page views. For the rest of the paper, we will assume that the experimentation unit is a user. It is important that the user receive a consistent experience throughout the experiment, and this is commonly achieved through cookies.
- **Null Hypothesis.** The hypothesis, often referred to as H<sub>0</sub>, that the OECs for the variants are not different and that any observed differences during the experiment are due to random fluctuations.
- **Confidence level.** The probability of failing to reject (i.e., retaining) the null hypothesis when it is true.
- **Power.** The probability of correctly rejecting the null hypothesis, H<sub>0</sub>, when it is false. Power measures our ability to detect a difference when it indeed exists.
  > Вероятность правильного отклонения нулевой гипотезы H<sub>0</sub>, когда она ложна. Сила измеряет нашу способность обнаруживать разницу, когда она действительно существует.
- **A/A Test.** Sometimes called a Null Test. Instead of an A/B test, you exercise the experimentation system, assigning users to one of two groups, but expose them to exactly the same experience. An A/A test can be used to (i) collect data and assess its variability for power calculations, and (ii) test the experimentation system (the Null hypothesis should be rejected about 5% of the time when a 95% confidence level is used).
- **Standard Deviation (Std-Dev).** A measure of variability, typically denoted by 𝜎.
- **Standard Error (Std-Err).** For a statistic, it is the standard deviation of the sampling distribution of the sample statistic. For a mean of 𝑛 independent observations, it is 𝜎/ 𝑛 where 𝜎 is the estimated standard deviation.

1. **Confidence level.** Commonly set to 95%, this level implies that 5% of the time we will incorrectly conclude that there is a difference when there is none (Type I error). All else being equal, increasing this level reduces our power (below).
  > Обычно установленный на 95%, этот уровень означает, что в 5% случаев мы ошибочно придем к выводу, что есть разница, когда ее нет (ошибка типа I). При прочих равных, повышение этого уровня снижает нашу силу.
2. **Power.** Commonly desired to be around 80-95%, although not directly controlled. If the Null Hypothesis is false, i.e., there is a difference in the OECs, the power is the probability of determining that the difference is statistically significant. (A Type II error is one where we retain the Null Hypothesis when it is false.)
  > **Сила.** Обычно желательно около 80-95%, хотя напрямую не контролируется. Если нулевая гипотеза неверна, т. Е. Существует различие в OEC, мощность - это вероятность определения того, что разница статистически значима. (Ошибка типа II - это ошибка, при которой мы сохраняем нулевую гипотезу, когда она ложна.)

## Courses

- [ ] [A/B Testing & Optimization Course](https://www.dynamicyield.com/course/testing-and-optimization/) by XP<sup>2</sup> Dynamic Yield
- [ ] [A/B Testing by Google](https://www.udacity.com/course/ab-testing--ud257)

## Calculators

- ### Statistical A/B-test Calculator
  - [A/B Test Calculator](https://measuringu.com/ab-cal/) by MeasuringU
  - [A/B Test Calculator](https://abtestguide.com/calc/) by ABTestguide


- ### Bayesian A/B-test Calculator
  - [Bayesian A/B-test Calculator](https://abtestguide.com/bayesian/)
  - [Bayesian A/B Testing Calculator](https://marketing.dynamicyield.com/bayesian-calculator/) by Dynamic Yield
  
- ## A/B Split & Multivariate Test Duration Calculator
  - [A/B Split & Multivariate Test Duration Calculator](https://vwo.com/tools/ab-test-duration-calculator/)
  
  ## Read
  
  - [ ] [A/B Testing Explained + a Collection of A/B Testing Learning Resources](https://soshace.com/ab-testing-resources/)
  - [ ] [How to Analyze A/B Test Results and Statistical Significance in A/B Testing](https://www.invespcro.com/blog/how-to-analyze-a-b-test-results/)
  - [ ] [How to do A/B Testing and Improve Your Conversions Quickly](https://www.crazyegg.com/blog/ab-testing/)
  - [ ] [10 Tips for Your Next A/B Test Report](https://online-metrics.com/ab-test-report/)
  - [ ] [Статистические гипотезы](http://mathprofi.ru/statisticheskie_gipotezy.html)
  - [ ] [Проверка статистических гипотез](http://www.ipiran.ru/frenkel/hypothesis_testing.pdf)
  - [ ] [Статистическая значимость](https://www.calltouch.ru/glossary/statisticheskaya-znachimost/)
  - [ ] [The complete guide to A/B testing](https://www.abtasty.com/ab-testing/)
  - [ ] [Data science you need to know! A/B testing](https://towardsdatascience.com/data-science-you-need-to-know-a-b-testing-f2f12aff619a)
  - [ ] [Statistical Significance](https://www.investopedia.com/terms/s/statistically_significant.asp)
  - [ ] [WHAT STATISTICAL TEST DO I USE?](https://measuringu.com/what-test/) by MeasuringU
  - [ ] [What every product manager should know about AB Testing](https://medium.com/swlh/what-every-product-manager-should-know-about-ab-testing-7e7619fe4533)
  - [ ] [A/B Testing Guide](https://vwo.com/ab-testing/#how-to-make-an-a-b-testing-calendar)
