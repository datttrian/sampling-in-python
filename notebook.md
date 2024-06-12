# Sampling in Python

## Introduction to Sampling

### Simple sampling with pandas

Throughout this chapter, you'll be exploring song data from Spotify.
Each row of this population dataset represents a song, and there are
over 40,000 rows. Columns include the song name, the artists who
performed it, the release year, and attributes of the song like its
duration, tempo, and danceability. You'll start by looking at the
durations.

Your first task is to sample the Spotify dataset and compare the mean
duration of the population with the sample.

`spotify_population` is available and `pandas` is loaded as `pd`.

**Instructions**

- Sample 1000 rows from `spotify_population`, assigning to
  `spotify_sample`.

**Answer**

```{python}

```

### Simple sampling and calculating with NumPy

You can also use `numpy` to calculate parameters or statistics from a
list or `pandas` Series.

You'll be turning it up to eleven and looking at the `loudness` property
of each song.

`spotify_population` is available and `numpy` is loaded as `np`.

**Instructions**

- Create a `pandas` Series, `loudness_pop`, by subsetting the `loudness`
  column from `spotify_population`.
- Sample `loudness_pop` to get 100 random values, assigning to
  `loudness_samp`.

**Answer**

```{python}

```

### Are findings from the sample generalizable?

You just saw how convenience sampling—collecting data using the easiest
method—can result in samples that aren't representative of the
population. Equivalently, this means findings from the sample are not
generalizable to the population. Visualizing the distributions of the
population and the sample can help determine whether or not the sample
is representative of the population.

The Spotify dataset contains an `acousticness` column, which is a
confidence measure from zero to one of whether the track was made with
instruments that aren't plugged in. You'll compare the `acousticness`
distribution of the total population of songs with a sample of those
songs.

`spotify_population` and `spotify_mysterious_sample` are available;
`pandas` as `pd`, `matplotlib.pyplot` as `plt`, and `numpy` as `np` are
loaded.

**Instructions**

- Plot a histogram of the `acousticness` from `spotify_population` with
  bins of width `0.01` from `0` to `1` using pandas `.hist()`.

**Answer**

```{python}

```

### Are these findings generalizable?

Let's look at another sample to see if it is representative of the
population. This time, you'll look at the `duration_minutes` column of
the Spotify dataset, which contains the length of the song in minutes.

`spotify_population` and `spotify_mysterious_sample2` are available;
`pandas`, `matplotlib.pyplot`, and `numpy` are loaded using their
standard aliases.

**Instructions**

- Plot a histogram of `duration_minutes` from `spotify_population` with
  bins of width `0.5` from `0` to `15` using pandas `.hist()`.

**Answer**

```{python}

```

### Generating random numbers

You've used `.sample()` to generate pseudo-random numbers from a set of
values in a DataFrame. A related task is to generate random numbers that
follow a statistical distribution, like the uniform distribution or the
normal distribution.

Each random number generation function has distribution-specific
arguments and an argument for specifying the number of random numbers to
generate.

`matplotlib.pyplot` is loaded as `plt`, and `numpy` is loaded as `np`.

**Instructions**

- Generate 5000 numbers from a uniform distribution, setting the
  parameters `low` to `-3` and `high` to `3`.

**Answer**

```{python}

```

## Sampling Methods

### Simple random sampling

The simplest method of sampling a population is the one you've seen
already. It is known as *simple random sampling* (sometimes abbreviated
to "SRS"), and involves picking rows at random, one at a time, where
each row has the same chance of being picked as any other.

In this chapter, you'll apply sampling methods to a synthetic
(fictional) employee attrition dataset from IBM, where "attrition" in
this context means leaving the company.

`attrition_pop` is available; `pandas` as `pd` is loaded.

**Instructions**

- Sample 70 rows from `attrition_pop` using simple random sampling,
  setting the random seed to `18900217`.
- Print the sample dataset, `attrition_samp`. *What do you notice about
  the indices?*

**Answer**

```{python}

```

### Systematic sampling

One sampling method that avoids randomness is called *systematic
sampling*. Here, you pick rows from the population at regular intervals.

For example, if the population dataset had one thousand rows, and you
wanted a sample size of five, you could pick rows `0`, `200`, `400`,
`600`, and `800`.

`attrition_pop` is available; `pandas` has been pre-loaded as `pd`.

**Instructions**

- Set the sample size to `70`.
- Calculate the population size from `attrition_pop`.
- Calculate the interval between the rows to be sampled.

**Answer**

```{python}

```

### Is systematic sampling OK?

Systematic sampling has a problem: if the data has been sorted, or there
is some sort of pattern or meaning behind the row order, then the
resulting sample may not be representative of the whole population. The
problem can be solved by shuffling the rows, but then systematic
sampling is equivalent to simple random sampling.

Here you'll look at how to determine whether or not there is a problem.

`attrition_pop` is available; `pandas` is loaded as `pd`, and
`matplotlib.pyplot` as `plt`.

**Instructions**

- Add an index column to `attrition_pop`, assigning the result to
  `attrition_pop_id`.
- Create a scatter plot of `YearsAtCompany` versus `index` for
  `attrition_pop_id` using pandas `.plot()`.

**Answer**

```{python}

```

### Proportional stratified sampling

If you are interested in subgroups within the population, then you may
need to carefully control the counts of each subgroup within the
population. *Proportional stratified sampling* results in subgroup sizes
within the sample that are representative of the subgroup sizes within
the population. It is equivalent to performing a simple random sample on
each subgroup.

`attrition_pop` is available; `pandas` is loaded with its usual alias.

**Instructions**

- Get the proportion of employees by `Education` level from
  `attrition_pop`.

**Answer**

```{python}

```

### Equal counts stratified sampling

If one subgroup is larger than another subgroup in the population, but
you don't want to reflect that difference in your analysis, then you can
use *equal counts stratified sampling* to generate samples where each
subgroup has the same amount of data. For example, if you are analyzing
blood types, O is the most common blood type worldwide, but you may wish
to have equal amounts of O, A, B, and AB in your sample.

`attrition_pop` is available; `pandas` is loaded with its usual alias.

**Instructions**

- Use equal counts stratified sampling on `attrition_pop` to get 30
  employees from each `Education` group, setting the seed to `2022`.

**Answer**

```{python}

```

### Weighted sampling

Stratified sampling provides rules about the probability of picking rows
from your dataset at the subgroup level. A generalization of this is
*weighted sampling*, which lets you specify rules about the probability
of picking rows at the row level. The probability of picking any given
row is proportional to the weight value for that row.

`attrition_pop` is available; `pandas`, `matplotlib.pyplot`, and `numpy`
are loaded with their usual aliases.

**Instructions**

- Plot `YearsAtCompany` from `attrition_pop` as a histogram with bins of
  width `1` from `0` to `40`.

**Answer**

```{python}

```

### Performing cluster sampling

Now that you know when to use cluster sampling, it's time to put it into
action. In this exercise, you'll explore the `JobRole` column of the
attrition dataset. You can think of each job role as a subgroup of the
whole population of employees.

`attrition_pop` is available; `pandas` is loaded with its usual alias,
and the `random` package is available. A seed of `19790801` has also
been set with `random.seed()`.

**Instructions**

- Create a list of unique `JobRole` values from `attrition_pop`, and
  assign to `job_roles_pop`.
- Randomly sample four `JobRole` values from `job_roles_pop`.

**Answer**

```{python}

```

### 3 kinds of sampling

You're going to compare the performance of point estimates using simple,
stratified, and cluster sampling. Before doing that, you'll have to set
up the samples.

You'll use the `RelationshipSatisfaction` column of the `attrition_pop`
dataset, which categorizes the employee's relationship with the company.
It has four levels: `Low`, `Medium`, `High`, and `Very_High`. `pandas`
has been loaded with its usual alias, and the `random` package has been
loaded.

**Instructions**

- Perform simple random sampling on `attrition_pop` to get one-quarter
  of the population, setting the seed to `2022`.

<!-- -->

- Perform stratified sampling on `attrition_pop` to sample one-quarter
  of each `RelationshipSatisfaction` group, setting the seed to `2022`.

<!-- -->

- Create a list of unique values from `attrition_pop`'s
  `RelationshipSatisfaction` column.
- Randomly sample `satisfaction_unique` to get two values.
- Subset the population for rows where `RelationshipSatisfaction` is in
  `satisfaction_samp` and clear any unused categories from
  `RelationshipSatisfaction`; assign to `attrition_clust_prep`.
- Perform cluster sampling on the selected satisfaction groups, sampling
  one quarter of the *population* and setting the seed to `2022`.

**Answer**

```{python}

```

### Comparing point estimates

Now that you have three types of sample (simple, stratified, and
cluster), you can compare point estimates from each sample to the
population parameter. That is, you can calculate the same summary
statistic on each sample and see how it compares to the summary
statistic for the population.

Here, we'll look at how satisfaction with the company affects whether or
not the employee leaves the company. That is, you'll calculate the
proportion of employees who left the company (they have an `Attrition`
value of `1`) for each value of `RelationshipSatisfaction`.

`attrition_pop`, `attrition_srs`, `attrition_strat`, and
`attrition_clust` are available; `pandas` is loaded with its usual
alias.

**Instructions**

Group `attrition_pop` by `RelationshipSatisfaction` levels and calculate
the mean of `Attrition` for each level.

Calculate the proportion of employee attrition for each relationship
satisfaction group, this time on the simple random sample,
`attrition_srs`.

Calculate the proportion of employee attrition for each relationship
satisfaction group, this time on the stratified sample,
`attrition_strat`.

Calculate the proportion of employee attrition for each relationship
satisfaction group, this time on the cluster sample, `attrition_clust`.

**Answer**

```{python}

```

## Sampling Distributions

### Calculating relative errors

The size of the sample you take affects how accurately the point
estimates reflect the corresponding population parameter. For example,
when you calculate a sample mean, you want it to be close to the
population mean. However, if your sample is too small, this might not be
the case.

The most common metric for assessing accuracy is *relative error*. This
is the absolute difference between the population parameter and the
point estimate, all divided by the population parameter. It is sometimes
expressed as a percentage.

`attrition_pop` and `mean_attrition_pop` (the mean of the `Attrition`
column of `attrition_pop`) are available; `pandas` is loaded as `pd`.

**Instructions**

- Generate a simple random sample from `attrition_pop` of fifty rows,
  setting the seed to `2022`.
- Calculate the mean employee `Attrition` in the sample.
- Calculate the relative error between `mean_attrition_srs50` and
  `mean_attrition_pop` as a *percentage*.

<!-- -->

- Calculate the *relative error percentage* again. This time, use a
  simple random sample of one hundred rows of `attrition_pop`.

**Answer**

```{python}

```

### Replicating samples

When you calculate a point estimate such as a sample mean, the value you
calculate depends on the rows that were included in the sample. That
means that there is some randomness in the answer. In order to quantify
the variation caused by this randomness, you can create many samples and
calculate the sample mean (or another statistic) for each sample.

`attrition_pop` is available; `pandas` and `matplotlib.pyplot` are
loaded with their usual aliases.

**Instructions**

- Replicate the provided code so that it runs `500` times. Assign the
  resulting list of sample means to `mean_attritions`.

**Answer**

```{python}

```

### Exact sampling distribution

To quantify how the point estimate (sample statistic) you are interested
in varies, you need to know all the possible values it can take and how
often. That is, you need to know its distribution.

The distribution of a sample statistic is called the *sampling
distribution*. When we can calculate this exactly, rather than using an
approximation, it is known as the *exact sampling distribution*.

Let's take another look at the sampling distribution of dice rolls. This
time, we'll look at five eight-sided dice. (These have the numbers one
to eight.)

![8 sided
die](https://assets.datacamp.com/production/repositories/5975/datasets/001ee1102f4838b0806d9b3592ce76ce454c3892/shutterstock_231673213_8_sided_die.jpeg)

`pandas`, `numpy`, and `matplotlib.pyplot` are loaded with their usual
aliases. The `expand_grid()` function is also available, which expects a
dictionary of key-value pairs as its argument. The definition of the
`expand_grid()` function is provided in the [pandas
documentation](https://pandas.pydata.org/pandas-docs/version/0.17.1/cookbook.html#creating-example-data).

**Instructions**

- Expand a grid representing 5 8-sided dice. That is, create a DataFrame
  with five columns from a dictionary, named `die1` to `die5`. The rows
  should contain all possibilities for throwing five dice, each numbered
  `1` to `8`.

**Answer**

```{python}

```

### Generating an approximate sampling distribution

Calculating the exact sampling distribution is only possible in very
simple situations. With just five eight-sided dice, the number of
possible rolls is `8**5`, which is over thirty thousand. When the
dataset is more complicated, for example, where a variable has hundreds
or thousands of categories, the number of possible outcomes becomes too
difficult to compute exactly.

In this situation, you can calculate an *approximate sampling
distribution* by simulating the exact sampling distribution. That is,
you can repeat a procedure over and over again to simulate both the
sampling process and the sample statistic calculation process.

`pandas`, `numpy`, and `matplotlib.pyplot` are loaded with their usual
aliases.

**Instructions**

- Sample one to eight, five times, with replacement. Assign to
  `five_rolls`.
- Calculate the mean of `five_rolls`.

**Answer**

```{python}

```

### Population & sampling distribution means

One of the useful features of sampling distributions is that you can
quantify them. Specifically, you can calculate summary statistics on
them. Here, you'll look at the relationship between the mean of the
sampling distribution and the population parameter's mean.

Three sampling distributions are provided. For each, the employee
attrition dataset was sampled using simple random sampling, then the
mean attrition was calculated. This was done 1000 times to get a
sampling distribution of mean attritions. One sampling distribution used
a sample size of 5 for each replicate, one used 50, and one used 500.

`attrition_pop`, `sampling_distribution_5`, `sampling_distribution_50`,
and `sampling_distribution_500` are available; `numpy` as `np` is
loaded.

**Instructions**

- Calculate the mean of `sampling_distribution_5`,
  `sampling_distribution_50`, and `sampling_distribution_500` (a mean of
  sample means).

**Answer**

```{python}

```

### Population & sampling distribution variation

You just calculated the mean of the sampling distribution and saw how it
is an estimate of the corresponding population parameter. Similarly, as
a result of the central limit theorem, the standard deviation of the
sampling distribution has an interesting relationship with the
population parameter's standard deviation and the sample size.

`attrition_pop`, `sampling_distribution_5`, `sampling_distribution_50`,
and `sampling_distribution_500` are available; `numpy` is loaded with
its usual alias.

**Instructions**

- Calculate the standard deviation of `sampling_distribution_5`,
  `sampling_distribution_50`, and `sampling_distribution_500` (a
  standard deviation of sample means).

**Answer**

```{python}

```

## Bootstrap Distributions

### Generating a bootstrap distribution

The process for generating a bootstrap distribution is similar to the
process for generating a sampling distribution; only the first step is
different.

To make a sampling distribution, you start with the population and
sample without replacement. To make a bootstrap distribution, you start
with a sample and sample that with replacement. After that, the steps
are the same: calculate the summary statistic that you are interested in
on that sample/resample, then replicate the process many times. In each
case, you can visualize the distribution with a histogram.

Here, `spotify_sample` is a subset of the `spotify_population` dataset.
To make it easier to see how resampling works, a row index column called
`'index'` has been added, and only the artist name, song name, and
`danceability` columns have been included.

`spotify_sample` is available; `pandas`, `numpy`, and
`matplotlib.pyplot` are loaded with their usual aliases.

**Instructions**

- Generate a single bootstrap resample from `spotify_sample`.

**Answer**

```{python}

```

### Sampling distribution vs. bootstrap distribution

The sampling distribution and bootstrap distribution are closely linked.
In situations where you can repeatedly sample from a population (these
occasions are rare), it's helpful to generate both the sampling
distribution and the bootstrap distribution, one after the other, to see
how they are related.

Here, the statistic you are interested in is the mean `popularity` score
of the songs.

`spotify_population` (the whole dataset) and `spotify_sample` (`500`
randomly sampled rows from `spotify_population`) are available; `pandas`
and `numpy` are loaded with their usual aliases.

**Instructions**

- Generate a sampling distribution of 2000 replicates.
- Sample 500 rows of the population without replacement and calculate
  the mean `popularity`.

<!-- -->

- Generate a bootstrap distribution of 2000 replicates.
- Sample 500 rows of the sample with replacement and calculate the mean
  `popularity`.

**Answer**

```{python}

```

### Compare sampling and bootstrap means

To make calculation easier, distributions similar to those calculated
from the previous exercise have been included, this time using a sample
size of `5000`.

`spotify_population`, `spotify_sample`, `sampling_distribution`, and
`bootstrap_distribution` are available; `pandas` and `numpy` are loaded
with their usual aliases.

**Instructions**

Calculate the mean `popularity` in 4 ways:

- Population: from `spotify_population`, take the mean of `popularity`.
- Sample: from `spotify_sample`, take the mean of `popularity`.
- Sampling distribution: from `sampling_distribution`, take its mean.
- Bootstrap distribution: from `bootstrap_distribution`, take its mean.

**Answer**

```{python}

```

### Compare sampling and bootstrap standard deviations

In the same way that you looked at how the sampling distribution and
bootstrap distribution could be used to estimate the population mean,
you'll now take a look at how they can be used to estimate variation, or
more specifically, the standard deviation, in the population.

Recall that the sample size is `5000`.

`spotify_population`, `spotify_sample`, `sampling_distribution`, and
`bootstrap_distribution` are available; `pandas` and `numpy` are loaded
with their usual aliases.

**Instructions**

Calculate the standard deviation of `popularity` in 4 ways.

- Population: from `spotify_population`, take the standard deviation of
  `popularity`.
- Original sample: from `spotify_sample`, take the standard deviation of
  `popularity`.
- Sampling distribution: from `sampling_distribution`, take its standard
  deviation and multiply by the square root of the sample size (`5000`).
- Bootstrap distribution: from `bootstrap_distribution`, take its
  standard deviation and multiply by the square root of the sample size.

**Answer**

```{python}

```

### Calculating confidence intervals

You have learned about two methods for calculating confidence intervals:
the *quantile method* and the *standard error method*. The standard
error method involves using the inverse cumulative distribution function
(inverse CDF) of the normal distribution to calculate confidence
intervals. In this exercise, you'll perform these two methods on the
Spotify data.

`spotify_population`, `spotify_sample`, and `bootstrap_distribution` are
available; `pandas` and `numpy` are loaded with their usual aliases, and
`norm` has been loaded from `scipy.stats`.

**Instructions**

- Generate a 95% confidence interval using the quantile method on the
  bootstrap distribution, setting the `0.025` quantile as `lower_quant`
  and the `0.975` quantile as `upper_quant`.

Generate a 95% confidence interval using the standard error method from
the bootstrap distribution.

- Calculate `point_estimate` as the mean of `bootstrap_distribution`,
  and `standard_error` as the standard deviation of
  `bootstrap_distribution`.
- Calculate `lower_se` as the `0.025` quantile of an inv. CDF from a
  normal distribution with mean `point_estimate` and standard deviation
  `standard_error`.
- Calculate `upper_se` as the `0.975` quantile of that same inv. CDF.

**Answer**

```{python}

```
