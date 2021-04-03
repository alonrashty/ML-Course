Problem Set 1
================
Alon Rashty
04/04/2021

-   [About the Course](#about-the-course)
    -   [Question 1](#question-1)
    -   [Question 2](#question-2)
    -   [Question 3](#question-3)
-   [RStudio](#rstudio)
    -   [Question 1](#question-1-1)
    -   [Question 2](#question-2-1)
    -   [Question 3](#question-3-1)

### About the Course

#### Question 1

Because we need to identify the causal factor in order to apply the
research results on policymaking, otherwise we could “tackle” the wrong
one and not get the results we aimed for. Causal inference is not ML
main goal, and instead it is interested in the best predictions.

#### Question 2

We need to have (or to assume) the error is not correlated with the
covariates (omitted variables), so we don’t have biased estimates. Also,
when we analyze experiments we need to have a good enough randomization
between the treatment and control groups.

#### Question 3

-   The linearity assumption means that we are looking for the average
    treatment effect although it might be heterogeneous.

### RStudio

#### Question 1

``` r
library(tidyverse)
library(kableExtra)
```

#### Question 2

``` r
iris %>%
  select(contains("Sepal") | Species) %>%
  group_by(Species) %>%
  summarise("Average Sepal Length" = mean(Sepal.Length)) %>%
  kbl(caption = "Table 1", align = 'lc') %>%
  kable_classic(full_width = F, html_font = "Cambria")
```

<table class=" lightable-classic" style="font-family: Cambria; width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
Table 1
</caption>
<thead>
<tr>
<th style="text-align:left;">
Species
</th>
<th style="text-align:center;">
Average Sepal Length
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
setosa
</td>
<td style="text-align:center;">
5.006
</td>
</tr>
<tr>
<td style="text-align:left;">
versicolor
</td>
<td style="text-align:center;">
5.936
</td>
</tr>
<tr>
<td style="text-align:left;">
virginica
</td>
<td style="text-align:center;">
6.588
</td>
</tr>
</tbody>
</table>

#### Question 3

``` r
mtcars %>%
  mutate(cyl = as.factor(cyl)) %>%
  ggplot(aes(x = hp, y = mpg, color = cyl)) +
    geom_point() +
    geom_smooth(method = lm)+
    theme(text=element_text(size=16,  family="serif"))
```

![](PS1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->
