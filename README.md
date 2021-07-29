# How-to-Calculate-Partial-Correlation-coefficient-in-R

partial correlation coefficient r, When we want to find the linear relationship between two variables, we often choose the Pearson correlation coefficient.

But some cases we want to know the relationship between two variables while controlling a third variable.

Suppose we want to measure the association between the number of hours students studied and the final score he/she awarded while controlling the current grade in the class.

This is one of the common example you can relate the same into other scenarios.

These kinds of situations partial correlation are more appropriate because we want to find the relation between two variables while controlling the third variable.

This tutorial describes how to execute partial correlation in R.
How to Calculate Partial Correlation in R
partial correlation coefficient r

We can take same example for the execution. Suppose our data frame contains three variables Grade, hours and score.

Let’s store the data frame into data.

data <- data.frame(Grade = c(80, 50, 80, 90, 92, 85, 76, 81, 90, 95),
                 hours = c(5, 4, 6, 6, 3, 5, 9, 9, 5, 6),
                 Score = c(90, 80, 70, 80, 95, 91, 99, 88, 92, 91))

The objective is to measure the association between score and hours while controlling Grade.

Significance of Spearman’s Rank Correlation »

data
     Grade hours Score
 1     80     5    90
 2     50     4    80
 3     80     6    70
 4     90     6    80
 5     92     3    95
 6     85     5    91
 7     76     9    99
 8     81     9    88
 9     90     5    92
 10    95     6    91

We are using ppcor library for the partial correlation analysis.

Correlation Analysis Different Types of Plots in R »

library(ppcor)
pcor(data)
$estimate
            Grade       hours     Score
Grade  1.00000000 -0.02240543 0.3124521
hours -0.02240543  1.00000000 0.1232100
Score  0.31245213  0.12320996 1.0000000
$p.value
          Grade     hours     Score
Grade 0.0000000 0.9543751 0.4130139
hours 0.9543751 0.0000000 0.7521524
Score 0.4130139 0.7521524 0.0000000
$statistic
            Grade       hours     Score
Grade  0.00000000 -0.05929409 0.8702405
hours -0.05929409  0.00000000 0.3284858
Score  0.87024054  0.32848576 0.0000000
$n
[1] 10
$gp
[1] 1
$method
[1] "pearson"

Inference

The partial correlation between hours studied and final exam score is 0.1232100, which is a small positive correlation. As hours studied increases parallelly exam score tends to increase while the current grade is controlled.

The p-value for this partial correlation is 0.7521524, which is not statistically significant at α = 0.05.

Same away we can infer,

Kendall’s Rank Correlation in R-Correlation Test »

The partial correlation between grade and final exam score is 0.3124521, which is a medium positive correlation. As current grade increases, exam score tends to increases, assuming hours studied is held constant.

The p-value for this partial correlation is 0.4130139, which is not statistically significant at α = 0.05.

The partial correlation between grade and hours studied is –0.02240543, which is a small negative correlation. As the grade increases, the final exam score tends to decreases, assuming the final exam score is held constant.

The p-value for this partial correlation is 0.9543751, which is not statistically significant at α = 0.05.
Conclusion

This tutorial described the method used to calculate the partial correlation as “Pearson.” In pcor() function can execute other methods also like “Kendall” or “Spearman” as alternative methods to calculate the correlations.
