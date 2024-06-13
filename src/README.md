# Sampling in Python

[![View On GitHub](github.svg)](https://github.com/datttrian/sampling-in-python)

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
- Calculate the mean duration in minutes from `spotify_population` using `pandas`.
- Calculate the mean duration in minutes from `spotify_sample` using `pandas`.

**Answer**

```python
pip install pandas pyarrow
```

```python
# added/edited
import pandas as pd
spotify_population = pd.read_feather("spotify_2000_2020.feather")
```

```python
# Sample 1000 rows from spotify_population
spotify_sample = spotify_population.sample(n=1000)

# Print the sample
print(spotify_sample)

# Calculate the mean duration in mins from spotify_population
mean_dur_pop = spotify_population["duration_minutes"].mean()

# Calculate the mean duration in mins from spotify_sample
mean_dur_samp = spotify_sample["duration_minutes"].mean()

# Print the means
print(mean_dur_pop)
print(mean_dur_samp)
```

           acousticness                                            artists  \
    14634        0.2480                 ['Lenny Tavárez', 'Justin Quiles']   
    24221        0.0744                           ['Florida Georgia Line']   
    312          0.2190                                      ['Nicky Jam']   
    40883        0.8380                                     ['King Krule']   
    21085        0.4160                        ['Aventura', 'Judy Santos']   
    ...             ...                                                ...   
    5745         0.1560                                   ['Jason Isbell']   
    13711        0.9650  ['Marcus Gilmore', 'Danny Grissett', 'Vicente ...   
    11769        0.0305                               ['Pitbull', 'Kesha']   
    38232        0.4790                                ['Aretha Franklin']   
    25450        0.0515                                  ['Darryl Worley']   
    
           danceability  duration_ms  duration_minutes  energy  explicit  \
    14634         0.777     154286.0          2.571433  0.6560       1.0   
    24221         0.494     199320.0          3.322000  0.9360       0.0   
    312           0.825     179093.0          2.984883  0.9360       0.0   
    40883         0.563     169693.0          2.828217  0.4080       0.0   
    21085         0.804     254720.0          4.245333  0.5600       0.0   
    ...             ...          ...               ...     ...       ...   
    5745          0.568     193613.0          3.226883  0.5270       0.0   
    13711         0.445     396520.0          6.608667  0.0978       0.0   
    11769         0.589     204200.0          3.403333  0.9660       0.0   
    38232         0.821     147227.0          2.453783  0.4960       0.0   
    25450         0.478     242293.0          4.038217  0.6250       0.0   
    
                               id  instrumentalness   key  liveness  loudness  \
    14634  2w8SKQCnT2YQK1qCqKl2uW          0.000002   2.0    0.1390    -5.823   
    24221  3grPZ1iQg2tEdh0ZCh3HTt          0.000000   1.0    0.1480    -2.989   
    312    634SIK3O65qhslx5DLX44X          0.000000   6.0    0.0572    -4.148   
    40883  35rf8iduzQ7vd8hFbDlv0o          0.000010   4.0    0.1080    -8.972   
    21085  65H6t1WQBim6q93yM8fEwn          0.000000   1.0    0.0608    -6.912   
    ...                       ...               ...   ...       ...       ...   
    5745   3TWffuE2fuzzl1qC2W2V6j          0.000000   4.0    0.1360   -10.206   
    13711  75A0vJQiBzAxkC7pMjoSeX          0.915000   3.0    0.1210   -26.924   
    11769  3tgZ9vmhuAY9wEoNUJskzV          0.000000  11.0    0.1470    -4.106   
    38232  1LI7vkkJ5EKLl6MpZBWZF2          0.000023   0.0    0.3280    -8.400   
    25450  5JWuz7zukN8z9JLNm29U5K          0.000000   7.0    0.1160    -5.975   
    
           mode                  name  popularity release_date  speechiness  \
    14634   0.0          La Pared 360        78.0   2020-02-06       0.1580   
    24221   1.0                  Stay        61.0   2012-01-01       0.0418   
    312     1.0     Me Voy Pa'l Party        52.0   2003-08-05       0.0435   
    40883   1.0             Easy Easy        51.0   2013-08-24       0.0365   
    21085   0.0              Obsesion        74.0   2002-06-01       0.0397   
    ...     ...                   ...         ...          ...          ...   
    5745    0.0             24 Frames        53.0   2015-07-17       0.0249   
    13711   1.0     Two Sleepy People        50.0   2011-06-06       0.0397   
    11769   1.0  Timber (feat. Ke$ha)        61.0         2012       0.0980   
    38232   1.0               Respect        45.0   2007-04-09       0.0462   
    25450   1.0   Have You Forgotten?        52.0   2003-01-01       0.0341   
    
             tempo  valence    year  
    14634  168.103    0.833  2020.0  
    24221  141.939    0.582  2012.0  
    312     95.033    0.780  2003.0  
    40883  146.908    0.234  2013.0  
    21085  133.682    0.768  2002.0  
    ...        ...      ...     ...  
    5745   104.930    0.761  2015.0  
    13711  117.283    0.173  2011.0  
    11769  129.984    0.803  2012.0  
    38232  114.605    0.955  2007.0  
    25450  160.196    0.343  2003.0  
    
    [1000 rows x 20 columns]
    3.8521519140900073
    3.96381525

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
- Calculate the mean of `loudness_pop` using `numpy`.
- Calculate the mean of `loudness_samp` using `numpy`.

**Answer**

```python
# added/edited
import numpy as np
```

```python
# Create a pandas Series from the loudness column of spotify_population
loudness_pop = spotify_population['loudness']

# Sample 100 values of loudness_pop
loudness_samp = loudness_pop.sample(n=100)

print(loudness_samp)


# Calculate the mean of loudness_pop
mean_loudness_pop = np.mean(loudness_pop)

# Calculate the mean of loudness_samp
mean_loudness_samp = np.mean(loudness_samp)

print(mean_loudness_pop)
print(mean_loudness_samp)
```

    5860     -4.118
    2821     -4.757
    24252    -7.327
    32814    -5.148
    11347    -6.487
              ...  
    29380    -5.066
    2883    -24.789
    26014    -2.403
    9116    -13.325
    35617    -6.839
    Name: loudness, Length: 100, dtype: float64
    -7.366856851353947
    -7.433510000000002

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
- Update the histogram code to use the `spotify_mysterious_sample` dataset.

**Answer**

```python
pip install matplotlib
```

```python
# added/edited
import matplotlib.pyplot as plt
spotify_mysterious_sample = spotify_population[spotify_population['acousticness'] > 0.95]
```

```python
# Visualize the distribution of acousticness with a histogram
spotify_population['acousticness'].hist(bins=np.arange(0, 1.01, 0.01))
plt.show()
```

![png](notebook_files/notebook_12_0.png)

```python
# Update the histogram to use spotify_mysterious_sample
spotify_mysterious_sample['acousticness'].hist(bins=np.arange(0, 1.01, 0.01))
plt.show()
```

![png](notebook_files/notebook_13_0.png)

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
- Update the histogram code to use the `spotify_mysterious_sample2` dataset.

**Answer**

```python
# added/edited
spotify_mysterious_sample2 = spotify_population.sample(n=50)
```

```python
# Visualize the distribution of duration_minutes as a histogram
spotify_population['duration_minutes'].hist(bins=np.arange(0, 15.5, 0.5))
plt.show()
```

![png](notebook_files/notebook_16_0.png)

```python
# Update the histogram to use spotify_mysterious_sample2
spotify_mysterious_sample2['duration_minutes'].hist(bins=np.arange(0, 15.5, 0.5))
plt.show()
```

![png](notebook_files/notebook_17_0.png)

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
- Generate 5000 numbers from a normal distribution, setting the parameters `loc` to `5` and `scale` to `2`.
- Plot a histogram of `uniforms` with bins of width of `0.25` from `-3` to `3` using `plt.hist()`.
- Plot a histogram of normals with bins of width of 0.5 from -2 to 13 using plt.hist().

**Answer**

```python
# Generate random numbers from a Uniform(-3, 3)
uniforms = np.random.uniform(low=-3, high=3, size=5000)

# Print uniforms
print(uniforms)


# Generate random numbers from a Normal(5, 2)
normals = np.random.normal(loc=5, scale=2, size=5000)

# Print normals
print(normals)
```

    [-1.8421194   0.64404365 -1.92788746 ... -2.57639818  1.59173031
     -0.11919233]
    [6.24654043 4.44286574 2.85788322 ... 4.99755308 4.32760378 2.80415531]

```python
# Generate random numbers from a Uniform(-3, 3)
uniforms = np.random.uniform(low=-3, high=3, size=5000)

# Plot a histogram of uniform values, binwidth 0.25
plt.hist(uniforms, bins=np.arange(-3, 3.25, 0.25))
plt.show()
```

![png](notebook_files/notebook_20_0.png)

```python
# Generate random numbers from a Normal(5, 2)
normals = np.random.normal(loc=5, scale=2, size=5000)

# Plot a histogram of normal values, binwidth 0.5
plt.hist(normals, bins=np.arange(-2, 13.5, 0.5))
plt.show()
```

![png](notebook_files/notebook_21_0.png)

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

```python
# added/edited
attrition_pop = pd.read_feather("attrition.feather")
```

```python
# Sample 70 rows using simple random sampling and set the seed
attrition_samp = attrition_pop.sample(n=70, random_state=18900217)

# Print the sample
print(attrition_samp)
```

          Age  Attrition     BusinessTravel  DailyRate            Department  \
    1134   35        0.0      Travel_Rarely        583  Research_Development   
    1150   52        0.0         Non-Travel        585                 Sales   
    531    33        0.0      Travel_Rarely        931  Research_Development   
    395    31        0.0      Travel_Rarely       1332  Research_Development   
    392    29        0.0      Travel_Rarely        942  Research_Development   
    ...   ...        ...                ...        ...                   ...   
    361    27        0.0  Travel_Frequently       1410                 Sales   
    1180   36        0.0      Travel_Rarely        530                 Sales   
    230    26        0.0      Travel_Rarely       1443                 Sales   
    211    29        0.0  Travel_Frequently        410  Research_Development   
    890    30        0.0  Travel_Frequently       1312  Research_Development   
    
          DistanceFromHome      Education    EducationField  \
    1134                25         Master           Medical   
    1150                29         Master     Life_Sciences   
    531                 14       Bachelor           Medical   
    395                 11        College           Medical   
    392                 15  Below_College     Life_Sciences   
    ...                ...            ...               ...   
    361                  3  Below_College           Medical   
    1180                 2         Master     Life_Sciences   
    230                 23       Bachelor         Marketing   
    211                  2  Below_College     Life_Sciences   
    890                  2         Master  Technical_Degree   
    
         EnvironmentSatisfaction  Gender  ...  PerformanceRating  \
    1134                    High  Female  ...          Excellent   
    1150                     Low    Male  ...          Excellent   
    531                Very_High  Female  ...          Excellent   
    395                     High    Male  ...          Excellent   
    392                   Medium  Female  ...          Excellent   
    ...                      ...     ...  ...                ...   
    361                Very_High  Female  ...        Outstanding   
    1180                    High  Female  ...          Excellent   
    230                     High  Female  ...          Excellent   
    211                Very_High  Female  ...          Excellent   
    890                Very_High  Female  ...          Excellent   
    
         RelationshipSatisfaction  StockOptionLevel TotalWorkingYears  \
    1134                     High                 1                16   
    1150                   Medium                 2                16   
    531                 Very_High                 1                 8   
    395                 Very_High                 0                 6   
    392                       Low                 1                 6   
    ...                       ...               ...               ...   
    361                    Medium                 2                 6   
    1180                     High                 0                17   
    230                      High                 1                 5   
    211                      High                 3                 4   
    890                 Very_High                 0                10   
    
         TrainingTimesLastYear WorkLifeBalance  YearsAtCompany  \
    1134                     3            Good              16   
    1150                     3            Good               9   
    531                      5          Better               8   
    395                      2            Good               6   
    392                      2            Good               5   
    ...                    ...             ...             ...   
    361                      3          Better               6   
    1180                     2            Good              13   
    230                      2            Good               2   
    211                      3          Better               3   
    890                      2          Better               9   
    
          YearsInCurrentRole  YearsSinceLastPromotion YearsWithCurrManager  
    1134                  10                       10                    1  
    1150                   8                        0                    0  
    531                    7                        1                    6  
    395                    5                        0                    1  
    392                    4                        1                    3  
    ...                  ...                      ...                  ...  
    361                    5                        0                    4  
    1180                   7                        6                    7  
    230                    2                        0                    0  
    211                    2                        0                    2  
    890                    7                        0                    7  
    
    [70 rows x 31 columns]

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
- Systematically sample `attrition_pop` to get the rows of the population at each `interval`, starting at 0; assign the rows to `attrition_sys_samp`.

**Answer**

```python
# Set the sample size to 70
sample_size = 70

# Calculate the population size from attrition_pop
pop_size = len(attrition_pop)

# Calculate the interval
interval = pop_size // sample_size

# Systematically sample 70 rows
attrition_sys_samp = attrition_pop.iloc[::interval]

# Print the sample
print(attrition_sys_samp)
```

          Age  Attrition BusinessTravel  DailyRate            Department  \
    0      21        0.0  Travel_Rarely        391  Research_Development   
    21     19        0.0  Travel_Rarely       1181  Research_Development   
    42     45        0.0  Travel_Rarely        252  Research_Development   
    63     23        0.0  Travel_Rarely        373  Research_Development   
    84     30        1.0  Travel_Rarely        945                 Sales   
    ...   ...        ...            ...        ...                   ...   
    1365   48        0.0  Travel_Rarely        715  Research_Development   
    1386   48        0.0  Travel_Rarely       1355  Research_Development   
    1407   50        0.0  Travel_Rarely        989  Research_Development   
    1428   50        0.0     Non-Travel        881  Research_Development   
    1449   52        0.0  Travel_Rarely        699  Research_Development   
    
          DistanceFromHome      Education EducationField EnvironmentSatisfaction  \
    0                   15        College  Life_Sciences                    High   
    21                   3  Below_College        Medical                  Medium   
    42                   2       Bachelor  Life_Sciences                  Medium   
    63                   1        College  Life_Sciences               Very_High   
    84                   9       Bachelor        Medical                  Medium   
    ...                ...            ...            ...                     ...   
    1365                 1       Bachelor  Life_Sciences               Very_High   
    1386                 4         Master  Life_Sciences                    High   
    1407                 7        College        Medical                  Medium   
    1428                 2         Master  Life_Sciences                     Low   
    1449                 1         Master  Life_Sciences                    High   
    
          Gender  ...  PerformanceRating RelationshipSatisfaction  \
    0       Male  ...          Excellent                Very_High   
    21    Female  ...          Excellent                Very_High   
    42    Female  ...          Excellent                Very_High   
    63      Male  ...        Outstanding                Very_High   
    84      Male  ...          Excellent                     High   
    ...      ...  ...                ...                      ...   
    1365    Male  ...          Excellent                     High   
    1386    Male  ...          Excellent                   Medium   
    1407  Female  ...          Excellent                Very_High   
    1428    Male  ...          Excellent                Very_High   
    1449    Male  ...          Excellent                      Low   
    
          StockOptionLevel TotalWorkingYears TrainingTimesLastYear  \
    0                    0                 0                     6   
    21                   0                 1                     3   
    42                   0                 1                     3   
    63                   1                 1                     2   
    84                   0                 1                     3   
    ...                ...               ...                   ...   
    1365                 0                25                     3   
    1386                 0                27                     3   
    1407                 1                29                     2   
    1428                 1                31                     3   
    1449                 1                34                     5   
    
         WorkLifeBalance  YearsAtCompany  YearsInCurrentRole  \
    0             Better               0                   0   
    21            Better               1                   0   
    42            Better               1                   0   
    63            Better               1                   0   
    84              Good               1                   0   
    ...              ...             ...                 ...   
    1365            Best               1                   0   
    1386          Better              15                  11   
    1407            Good              27                   3   
    1428          Better              31                   6   
    1449          Better              33                  18   
    
          YearsSinceLastPromotion YearsWithCurrManager  
    0                           0                    0  
    21                          0                    0  
    42                          0                    0  
    63                          0                    1  
    84                          0                    0  
    ...                       ...                  ...  
    1365                        0                    0  
    1386                        4                    8  
    1407                       13                    8  
    1428                       14                    7  
    1449                       11                    9  
    
    [70 rows x 31 columns]

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
- Randomly shuffle the rows of `attrition_pop`.
- Reset the row indexes, and add an index column to `attrition_pop`.
- Repeat the scatter plot of `YearsAtCompany` versus `index`, this time using `attrition_shuffled`.

**Answer**

```python
# Add an index column to attrition_pop
attrition_pop_id = attrition_pop.reset_index()

# Plot YearsAtCompany vs. index for attrition_pop_id
attrition_pop_id.plot(x="index", y="YearsAtCompany", kind="scatter")
plt.show()
```

![png](notebook_files/notebook_29_0.png)

```python
# Shuffle the rows of attrition_pop
attrition_shuffled = attrition_pop.sample(frac=1)

# Reset the row indexes and create an index column
attrition_shuffled = attrition_shuffled.reset_index(drop=True).reset_index()

# Plot YearsAtCompany vs. index for attrition_shuffled
attrition_shuffled.plot(x="index", y="YearsAtCompany", kind="scatter")
plt.show()
```

![png](notebook_files/notebook_30_0.png)

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
- Use proportional stratified sampling on `attrition_pop` to sample 40% of each `Education` group, setting the seed to `2022`.
- Get the proportion of employees by `Education` level from `attrition_strat`.

**Answer**

```python
# Proportion of employees by Education level
education_counts_pop = attrition_pop['Education'].value_counts(normalize=True)

# Print education_counts_pop
print(education_counts_pop)
```

    Education
    Bachelor         0.389116
    Master           0.270748
    College          0.191837
    Below_College    0.115646
    Doctor           0.032653
    Name: proportion, dtype: float64

```python
# Proportional stratified sampling for 40% of each Education group
attrition_strat = attrition_pop.groupby('Education')\
 .sample(frac=0.4, random_state=2022)

# Print the sample
print(attrition_strat)
```

          Age  Attrition     BusinessTravel  DailyRate            Department  \
    1191   53        0.0      Travel_Rarely        238                 Sales   
    407    29        0.0  Travel_Frequently        995  Research_Development   
    1233   59        0.0  Travel_Frequently       1225                 Sales   
    366    37        0.0      Travel_Rarely        571  Research_Development   
    702    31        0.0  Travel_Frequently        163  Research_Development   
    ...   ...        ...                ...        ...                   ...   
    733    38        0.0  Travel_Frequently        653  Research_Development   
    1061   44        0.0  Travel_Frequently        602       Human_Resources   
    1307   41        0.0      Travel_Rarely       1276                 Sales   
    1060   33        0.0      Travel_Rarely        516  Research_Development   
    177    29        0.0      Travel_Rarely        738  Research_Development   
    
          DistanceFromHome      Education    EducationField  \
    1191                 1  Below_College           Medical   
    407                  2  Below_College     Life_Sciences   
    1233                 1  Below_College     Life_Sciences   
    366                 10  Below_College     Life_Sciences   
    702                 24  Below_College  Technical_Degree   
    ...                ...            ...               ...   
    733                 29         Doctor     Life_Sciences   
    1061                 1         Doctor   Human_Resources   
    1307                 2         Doctor     Life_Sciences   
    1060                 8         Doctor     Life_Sciences   
    177                  9         Doctor             Other   
    
         EnvironmentSatisfaction  Gender  ...  PerformanceRating  \
    1191               Very_High  Female  ...        Outstanding   
    407                      Low    Male  ...          Excellent   
    1233                     Low  Female  ...          Excellent   
    366                Very_High  Female  ...          Excellent   
    702                Very_High  Female  ...        Outstanding   
    ...                      ...     ...  ...                ...   
    733                Very_High  Female  ...          Excellent   
    1061                     Low    Male  ...          Excellent   
    1307                  Medium  Female  ...          Excellent   
    1060               Very_High    Male  ...          Excellent   
    177                   Medium    Male  ...          Excellent   
    
         RelationshipSatisfaction  StockOptionLevel TotalWorkingYears  \
    1191                Very_High                 0                18   
    407                 Very_High                 1                 6   
    1233                Very_High                 0                20   
    366                    Medium                 2                 6   
    702                 Very_High                 0                 9   
    ...                       ...               ...               ...   
    733                 Very_High                 0                10   
    1061                     High                 0                14   
    1307                   Medium                 1                22   
    1060                      Low                 0                14   
    177                      High                 0                 4   
    
         TrainingTimesLastYear WorkLifeBalance  YearsAtCompany  \
    1191                     2            Best              14   
    407                      0            Best               6   
    1233                     2            Good               4   
    366                      3            Good               5   
    702                      3            Good               5   
    ...                    ...             ...             ...   
    733                      2          Better              10   
    1061                     3          Better              10   
    1307                     2          Better              18   
    1060                     6          Better               0   
    177                      2          Better               3   
    
          YearsInCurrentRole  YearsSinceLastPromotion YearsWithCurrManager  
    1191                   7                        8                   10  
    407                    4                        1                    3  
    1233                   3                        1                    3  
    366                    3                        4                    3  
    702                    4                        1                    4  
    ...                  ...                      ...                  ...  
    733                    3                        9                    9  
    1061                   7                        0                    2  
    1307                  16                       11                    8  
    1060                   0                        0                    0  
    177                    2                        2                    2  
    
    [588 rows x 31 columns]


    /tmp/ipykernel_4815/385919107.py:2: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      attrition_strat = attrition_pop.groupby('Education')\

```python
# Calculate the Education level proportions from attrition_strat
education_counts_strat = attrition_strat['Education'].value_counts(normalize=True)

# Print education_counts_strat
print(education_counts_strat)
```

    Education
    Bachelor         0.389456
    Master           0.270408
    College          0.192177
    Below_College    0.115646
    Doctor           0.032313
    Name: proportion, dtype: float64

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
- Get the proportion of employees by `Education` level from `attrition_eq`.

**Answer**

```python
# Get 30 employees from each Education group
attrition_eq = attrition_pop.groupby('Education')\
 .sample(n=30, random_state=2022)

# Print the sample
print(attrition_eq)
```

          Age  Attrition     BusinessTravel  DailyRate            Department  \
    1191   53        0.0      Travel_Rarely        238                 Sales   
    407    29        0.0  Travel_Frequently        995  Research_Development   
    1233   59        0.0  Travel_Frequently       1225                 Sales   
    366    37        0.0      Travel_Rarely        571  Research_Development   
    702    31        0.0  Travel_Frequently        163  Research_Development   
    ...   ...        ...                ...        ...                   ...   
    774    33        0.0      Travel_Rarely        922  Research_Development   
    869    45        0.0      Travel_Rarely       1015  Research_Development   
    530    32        0.0      Travel_Rarely        120  Research_Development   
    1049   48        0.0      Travel_Rarely        163                 Sales   
    350    29        1.0      Travel_Rarely        408  Research_Development   
    
          DistanceFromHome      Education    EducationField  \
    1191                 1  Below_College           Medical   
    407                  2  Below_College     Life_Sciences   
    1233                 1  Below_College     Life_Sciences   
    366                 10  Below_College     Life_Sciences   
    702                 24  Below_College  Technical_Degree   
    ...                ...            ...               ...   
    774                  1         Doctor           Medical   
    869                  5         Doctor           Medical   
    530                  6         Doctor     Life_Sciences   
    1049                 2         Doctor         Marketing   
    350                 25         Doctor  Technical_Degree   
    
         EnvironmentSatisfaction  Gender  ...  PerformanceRating  \
    1191               Very_High  Female  ...        Outstanding   
    407                      Low    Male  ...          Excellent   
    1233                     Low  Female  ...          Excellent   
    366                Very_High  Female  ...          Excellent   
    702                Very_High  Female  ...        Outstanding   
    ...                      ...     ...  ...                ...   
    774                      Low  Female  ...          Excellent   
    869                     High  Female  ...          Excellent   
    530                     High    Male  ...        Outstanding   
    1049                  Medium  Female  ...          Excellent   
    350                     High  Female  ...          Excellent   
    
         RelationshipSatisfaction  StockOptionLevel TotalWorkingYears  \
    1191                Very_High                 0                18   
    407                 Very_High                 1                 6   
    1233                Very_High                 0                20   
    366                    Medium                 2                 6   
    702                 Very_High                 0                 9   
    ...                       ...               ...               ...   
    774                      High                 1                10   
    869                       Low                 0                10   
    530                       Low                 0                 8   
    1049                      Low                 1                14   
    350                    Medium                 0                 6   
    
         TrainingTimesLastYear WorkLifeBalance  YearsAtCompany  \
    1191                     2            Best              14   
    407                      0            Best               6   
    1233                     2            Good               4   
    366                      3            Good               5   
    702                      3            Good               5   
    ...                    ...             ...             ...   
    774                      2          Better               6   
    869                      3          Better              10   
    530                      2          Better               5   
    1049                     2          Better               9   
    350                      2            Best               2   
    
          YearsInCurrentRole  YearsSinceLastPromotion YearsWithCurrManager  
    1191                   7                        8                   10  
    407                    4                        1                    3  
    1233                   3                        1                    3  
    366                    3                        4                    3  
    702                    4                        1                    4  
    ...                  ...                      ...                  ...  
    774                    1                        0                    5  
    869                    7                        1                    4  
    530                    4                        1                    4  
    1049                   7                        6                    7  
    350                    2                        1                    1  
    
    [150 rows x 31 columns]


    /tmp/ipykernel_4815/38261059.py:2: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      attrition_eq = attrition_pop.groupby('Education')\

```python
# Get the proportions from attrition_eq
education_counts_eq = attrition_eq['Education'].value_counts(normalize=True)

# Print the results
print(education_counts_eq)
```

    Education
    Below_College    0.2
    College          0.2
    Bachelor         0.2
    Master           0.2
    Doctor           0.2
    Name: proportion, dtype: float64

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
- Sample 400 employees from `attrition_pop` weighted by `YearsAtCompany`.
- Plot `YearsAtCompany` from `attrition_weight` as a histogram with bins of width `1` from `0` to `40`.

**Answer**

```python
# Plot YearsAtCompany from attrition_pop as a histogram
attrition_pop['YearsAtCompany'].hist(bins=np.arange(0, 41, 1))
plt.show()
```

![png](notebook_files/notebook_39_0.png)

```python
# Sample 400 employees weighted by YearsAtCompany
attrition_weight = attrition_pop.sample(n=400, weights="YearsAtCompany")

# Print the sample
print(attrition_weight)
```

          Age  Attrition     BusinessTravel  DailyRate            Department  \
    1269   45        0.0      Travel_Rarely       1385  Research_Development   
    1422   53        0.0  Travel_Frequently        124                 Sales   
    1283   39        1.0  Travel_Frequently        203  Research_Development   
    1449   52        0.0      Travel_Rarely        699  Research_Development   
    1225   41        0.0         Non-Travel        256                 Sales   
    ...   ...        ...                ...        ...                   ...   
    617    32        1.0  Travel_Frequently        238  Research_Development   
    137    22        0.0      Travel_Rarely        604  Research_Development   
    475    33        0.0      Travel_Rarely       1075       Human_Resources   
    1228   48        1.0  Travel_Frequently        708                 Sales   
    285    28        0.0      Travel_Rarely        640  Research_Development   
    
          DistanceFromHome      Education    EducationField  \
    1269                20        College           Medical   
    1422                 2       Bachelor         Marketing   
    1283                 2       Bachelor     Life_Sciences   
    1449                 1         Master     Life_Sciences   
    1225                10        College           Medical   
    ...                ...            ...               ...   
    617                  5        College     Life_Sciences   
    137                  6  Below_College           Medical   
    475                  3        College   Human_Resources   
    1228                 7        College           Medical   
    285                  1       Bachelor  Technical_Degree   
    
         EnvironmentSatisfaction  Gender  ...  PerformanceRating  \
    1269                    High    Male  ...          Excellent   
    1422                    High  Female  ...          Excellent   
    1283                     Low    Male  ...          Excellent   
    1449                    High    Male  ...          Excellent   
    1225                    High    Male  ...          Excellent   
    ...                      ...     ...  ...                ...   
    617                      Low  Female  ...          Excellent   
    137                      Low    Male  ...        Outstanding   
    475                Very_High    Male  ...          Excellent   
    1228               Very_High  Female  ...          Excellent   
    285                Very_High    Male  ...          Excellent   
    
         RelationshipSatisfaction  StockOptionLevel TotalWorkingYears  \
    1269                   Medium                 0                21   
    1422                      Low                 1                30   
    1283                Very_High                 3                21   
    1449                      Low                 1                34   
    1225                      Low                 0                19   
    ...                       ...               ...               ...   
    617                       Low                 0                 8   
    137                 Very_High                 0                 3   
    475                      High                 1                 7   
    1228                     High                 2                19   
    285                    Medium                 0                 5   
    
         TrainingTimesLastYear WorkLifeBalance  YearsAtCompany  \
    1269                     2          Better              20   
    1422                     2          Better              15   
    1283                     4          Better              18   
    1449                     5          Better              33   
    1225                     4          Better              19   
    ...                    ...             ...             ...   
    617                      2          Better               4   
    137                      3          Better               2   
    475                      4            Best               4   
    1228                     3          Better               9   
    285                      2            Good               3   
    
          YearsInCurrentRole  YearsSinceLastPromotion YearsWithCurrManager  
    1269                   7                        4                   10  
    1422                   7                        6                   12  
    1283                   7                       11                    5  
    1449                  18                       11                    9  
    1225                   2                       11                    9  
    ...                  ...                      ...                  ...  
    617                    1                        0                    3  
    137                    2                        2                    2  
    475                    3                        0                    3  
    1228                   7                        7                    7  
    285                    2                        1                    2  
    
    [400 rows x 31 columns]

```python
# Plot YearsAtCompany from attrition_weight as a histogram
attrition_weight['YearsAtCompany'].hist(bins=np.arange(0, 41, 1))
plt.show()
```

![png](notebook_files/notebook_41_0.png)

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
- Subset `attrition_pop` for the sampled job roles by filtering for rows where `JobRole` is in `job_roles_samp`.
- Remove any unused categories from `JobRole`.
- For each job role in the filtered dataset, take a random sample of ten rows, setting the seed to `2022`.

**Answer**

```python
# added/edited
import random
```

```python
# Create a list of unique JobRole values
job_roles_pop = list(attrition_pop['JobRole'].unique())

# Randomly sample four JobRole values
job_roles_samp = random.sample(job_roles_pop, k=4)

# Print the result
print(job_roles_samp)
```

    ['Sales_Executive', 'Sales_Representative', 'Healthcare_Representative', 'Manager']

```python
# Filter for rows where JobRole is in job_roles_samp
jobrole_condition = attrition_pop['JobRole'].isin(job_roles_samp)
attrition_filtered = attrition_pop[jobrole_condition]

# Print the result
print(attrition_filtered)
```

          Age  Attrition     BusinessTravel  DailyRate            Department  \
    1      19        1.0      Travel_Rarely        528                 Sales   
    3      18        0.0      Travel_Rarely        812                 Sales   
    4      18        1.0  Travel_Frequently       1306                 Sales   
    9      18        1.0  Travel_Frequently        544                 Sales   
    23     19        1.0  Travel_Frequently        602                 Sales   
    ...   ...        ...                ...        ...                   ...   
    1464   55        0.0      Travel_Rarely        452  Research_Development   
    1465   55        0.0      Travel_Rarely       1117                 Sales   
    1466   58        0.0         Non-Travel        350                 Sales   
    1467   58        0.0      Travel_Rarely        682                 Sales   
    1468   58        1.0      Travel_Rarely        147  Research_Development   
    
          DistanceFromHome      Education    EducationField  \
    1                   22  Below_College         Marketing   
    3                   10       Bachelor           Medical   
    4                    5       Bachelor         Marketing   
    9                    3        College           Medical   
    23                   1  Below_College  Technical_Degree   
    ...                ...            ...               ...   
    1464                 1       Bachelor           Medical   
    1465                18         Doctor     Life_Sciences   
    1466                 2       Bachelor           Medical   
    1467                10         Master           Medical   
    1468                23         Master           Medical   
    
         EnvironmentSatisfaction  Gender  ...  PerformanceRating  \
    1                  Very_High    Male  ...          Excellent   
    3                  Very_High  Female  ...          Excellent   
    4                     Medium    Male  ...          Excellent   
    9                     Medium  Female  ...          Excellent   
    23                      High  Female  ...        Outstanding   
    ...                      ...     ...  ...                ...   
    1464               Very_High    Male  ...          Excellent   
    1465                     Low  Female  ...        Outstanding   
    1466                  Medium    Male  ...        Outstanding   
    1467               Very_High    Male  ...          Excellent   
    1468               Very_High  Female  ...          Excellent   
    
         RelationshipSatisfaction  StockOptionLevel TotalWorkingYears  \
    1                   Very_High                 0                 0   
    3                         Low                 0                 0   
    4                   Very_High                 0                 0   
    9                        High                 0                 0   
    23                        Low                 0                 1   
    ...                       ...               ...               ...   
    1464                     High                 0                37   
    1465                Very_High                 0                37   
    1466                Very_High                 1                37   
    1467                     High                 0                38   
    1468                Very_High                 1                40   
    
         TrainingTimesLastYear WorkLifeBalance  YearsAtCompany  \
    1                        2            Good               0   
    3                        2          Better               0   
    4                        3          Better               0   
    9                        2            Best               0   
    23                       5            Best               0   
    ...                    ...             ...             ...   
    1464                     2          Better              36   
    1465                     2          Better              10   
    1466                     0            Good              16   
    1467                     1            Good              37   
    1468                     3            Good              40   
    
          YearsInCurrentRole  YearsSinceLastPromotion YearsWithCurrManager  
    1                      0                        0                    0  
    3                      0                        0                    0  
    4                      0                        0                    0  
    9                      0                        0                    0  
    23                     0                        0                    0  
    ...                  ...                      ...                  ...  
    1464                  10                        4                   13  
    1465                   9                        7                    7  
    1466                   9                       14                   14  
    1467                  10                        1                    8  
    1468                  10                       15                    6  
    
    [642 rows x 31 columns]

```python
# Remove categories with no rows
attrition_filtered['JobRole'] = attrition_filtered['JobRole'].cat.remove_unused_categories()

# Randomly sample 10 employees from each sampled job role
attrition_clust = attrition_filtered.groupby("JobRole")\
    .sample(n=10, random_state=2022)

# Print the sample
print(attrition_clust)         
```

          Age  Attrition     BusinessTravel  DailyRate            Department  \
    812    31        0.0      Travel_Rarely        616  Research_Development   
    1190   38        0.0      Travel_Rarely       1495  Research_Development   
    378    33        0.0      Travel_Rarely       1069  Research_Development   
    920    35        0.0  Travel_Frequently       1199  Research_Development   
    917    33        0.0      Travel_Rarely        501  Research_Development   
    1058   34        0.0      Travel_Rarely        404  Research_Development   
    1264   46        0.0  Travel_Frequently        638  Research_Development   
    1340   44        0.0      Travel_Rarely        477  Research_Development   
    655    34        0.0      Travel_Rarely       1442  Research_Development   
    896    42        0.0      Travel_Rarely       1128  Research_Development   
    1106   51        0.0      Travel_Rarely        942  Research_Development   
    1307   41        0.0      Travel_Rarely       1276                 Sales   
    1359   43        0.0  Travel_Frequently        394                 Sales   
    1266   50        0.0      Travel_Rarely       1452  Research_Development   
    1310   53        0.0      Travel_Rarely       1376                 Sales   
    1417   59        0.0         Non-Travel       1420       Human_Resources   
    1044   34        0.0      Travel_Rarely       1354  Research_Development   
    1336   48        0.0  Travel_Frequently        365  Research_Development   
    1280   42        0.0      Travel_Rarely        265                 Sales   
    1285   39        0.0      Travel_Rarely        412  Research_Development   
    1096   34        0.0      Travel_Rarely       1326                 Sales   
    1454   53        0.0      Travel_Rarely        661                 Sales   
    432    35        0.0      Travel_Rarely        682                 Sales   
    187    24        1.0      Travel_Rarely        693                 Sales   
    653    31        1.0      Travel_Rarely       1365                 Sales   
    207    32        0.0      Travel_Rarely        499                 Sales   
    713    34        0.0      Travel_Rarely       1239                 Sales   
    512    39        0.0  Travel_Frequently        766                 Sales   
    961    32        0.0      Travel_Rarely       1093                 Sales   
    845    41        0.0  Travel_Frequently       1018                 Sales   
    92     35        0.0      Travel_Rarely        890                 Sales   
    101    29        0.0      Travel_Rarely       1090                 Sales   
    153    31        1.0  Travel_Frequently       1060                 Sales   
    1008   53        0.0      Travel_Rarely       1436                 Sales   
    140    38        0.0      Travel_Rarely        395                 Sales   
    23     19        1.0  Travel_Frequently        602                 Sales   
    1150   52        0.0         Non-Travel        585                 Sales   
    104    20        1.0  Travel_Frequently        769                 Sales   
    148    33        0.0         Non-Travel       1038                 Sales   
    188    50        0.0      Travel_Rarely        316                 Sales   
    
          DistanceFromHome      Education    EducationField  \
    812                 12       Bachelor           Medical   
    1190                10       Bachelor           Medical   
    378                  1       Bachelor     Life_Sciences   
    920                 18         Master     Life_Sciences   
    917                 15        College           Medical   
    1058                 2         Master  Technical_Degree   
    1264                 1       Bachelor           Medical   
    1340                 7         Master           Medical   
    655                  9       Bachelor           Medical   
    896                 13       Bachelor           Medical   
    1106                 3       Bachelor  Technical_Degree   
    1307                 2         Doctor     Life_Sciences   
    1359                26        College     Life_Sciences   
    1266                11       Bachelor     Life_Sciences   
    1310                 2        College           Medical   
    1417                 2         Master   Human_Resources   
    1044                 5       Bachelor           Medical   
    1336                 4         Doctor           Medical   
    1280                 5        College         Marketing   
    1285                13         Master           Medical   
    1096                 3       Bachelor             Other   
    1454                 7        College         Marketing   
    432                 18         Master           Medical   
    187                  3        College     Life_Sciences   
    653                 13         Master           Medical   
    207                  2  Below_College         Marketing   
    713                 13         Master           Medical   
    512                 20       Bachelor     Life_Sciences   
    961                  6         Master           Medical   
    845                  1       Bachelor         Marketing   
    92                   2       Bachelor         Marketing   
    101                 10       Bachelor         Marketing   
    153                  1       Bachelor     Life_Sciences   
    1008                 6        College         Marketing   
    140                  9       Bachelor         Marketing   
    23                   1  Below_College  Technical_Degree   
    1150                29         Master     Life_Sciences   
    104                  9       Bachelor         Marketing   
    148                  8  Below_College     Life_Sciences   
    188                  8         Master         Marketing   
    
         EnvironmentSatisfaction  Gender  ...  PerformanceRating  \
    812                Very_High  Female  ...          Excellent   
    1190                    High  Female  ...          Excellent   
    378                   Medium  Female  ...          Excellent   
    920                     High    Male  ...          Excellent   
    917                   Medium  Female  ...          Excellent   
    1058                    High  Female  ...          Excellent   
    1264                    High    Male  ...          Excellent   
    1340                     Low  Female  ...          Excellent   
    655                Very_High  Female  ...          Excellent   
    896                   Medium    Male  ...          Excellent   
    1106                     Low  Female  ...          Excellent   
    1307                  Medium  Female  ...          Excellent   
    1359                    High    Male  ...          Excellent   
    1266                    High  Female  ...          Excellent   
    1310                    High    Male  ...          Excellent   
    1417                    High  Female  ...        Outstanding   
    1044                    High  Female  ...          Excellent   
    1336                    High    Male  ...        Outstanding   
    1280               Very_High    Male  ...          Excellent   
    1285                    High  Female  ...          Excellent   
    1096               Very_High    Male  ...          Excellent   
    1454                     Low  Female  ...          Excellent   
    432                   Medium    Male  ...          Excellent   
    187                      Low  Female  ...          Excellent   
    653                   Medium    Male  ...          Excellent   
    207                     High    Male  ...          Excellent   
    713                Very_High    Male  ...          Excellent   
    512                     High    Male  ...          Excellent   
    961                   Medium    Male  ...          Excellent   
    845                     High  Female  ...          Excellent   
    92                 Very_High  Female  ...          Excellent   
    101                Very_High    Male  ...          Excellent   
    153                Very_High  Female  ...          Excellent   
    1008                  Medium    Male  ...        Outstanding   
    140                   Medium    Male  ...          Excellent   
    23                      High  Female  ...        Outstanding   
    1150                     Low    Male  ...          Excellent   
    104                Very_High  Female  ...          Excellent   
    148                   Medium  Female  ...          Excellent   
    188                Very_High    Male  ...          Excellent   
    
         RelationshipSatisfaction  StockOptionLevel TotalWorkingYears  \
    812                      High                 2                10   
    1190                     High                 1                18   
    378                       Low                 0                 6   
    920                 Very_High                 2                10   
    917                       Low                 1                10   
    1058                Very_High                 0                14   
    1264                     High                 1                21   
    1340                Very_High                 1                24   
    655                    Medium                 0                 9   
    896                      High                 2                10   
    1106                Very_High                 0                15   
    1307                   Medium                 1                22   
    1359                Very_High                 2                25   
    1266                   Medium                 0                21   
    1310                     High                 1                22   
    1417                Very_High                 1                30   
    1044                Very_High                 0                14   
    1336                   Medium                 1                23   
    1280                   Medium                 0                21   
    1285                Very_High                 2                21   
    1096                Very_High                 0                15   
    1454                Very_High                 1                35   
    432                 Very_High                 1                 6   
    187                       Low                 0                 4   
    653                      High                 0                 9   
    207                       Low                 3                 4   
    713                      High                 1                 9   
    512                 Very_High                 1                 7   
    961                       Low                 0                12   
    845                 Very_High                 1                10   
    92                        Low                 0                 2   
    101                 Very_High                 2                 2   
    153                       Low                 0                 3   
    1008                Very_High                 1                13   
    140                 Very_High                 1                 3   
    23                        Low                 0                 1   
    1150                   Medium                 2                16   
    104                    Medium                 0                 2   
    148                 Very_High                 0                 3   
    188                 Very_High                 1                 4   
    
         TrainingTimesLastYear WorkLifeBalance  YearsAtCompany  \
    812                      2             Bad               9   
    1190                     4          Better               1   
    378                      3          Better               5   
    920                      2            Best              10   
    917                      6          Better               9   
    1058                     2            Best              14   
    1264                     5            Good              10   
    1340                     4          Better              22   
    655                      3            Best               8   
    896                      2            Good               0   
    1106                     2          Better               2   
    1307                     2          Better              18   
    1359                     3            Best              25   
    1266                     5          Better               5   
    1310                     3            Best              17   
    1417                     3          Better               3   
    1044                     6          Better              11   
    1336                     3          Better               2   
    1280                     3            Best               1   
    1285                     4          Better              19   
    1096                     2          Better              13   
    1454                     3          Better               5   
    432                      2             Bad               5   
    187                      3          Better               2   
    653                      2             Bad               3   
    207                      3            Good               3   
    713                      2            Good               8   
    512                      6          Better               2   
    961                      0          Better              11   
    845                      2          Better               9   
    92                       3          Better               2   
    101                      2          Better               2   
    153                      2            Best               3   
    1008                     3             Bad               7   
    140                      3          Better               2   
    23                       5            Best               0   
    1150                     3            Good               9   
    104                      3          Better               2   
    148                      2            Good               2   
    188                      2          Better               2   
    
          YearsInCurrentRole  YearsSinceLastPromotion YearsWithCurrManager  
    812                    7                        8                    5  
    1190                   0                        0                    0  
    378                    0                        1                    4  
    920                    2                        0                    2  
    917                    7                        8                    1  
    1058                  11                        4                   11  
    1264                   9                        9                    5  
    1340                   6                        5                   17  
    655                    7                        7                    7  
    896                    0                        0                    0  
    1106                   2                        2                    2  
    1307                  16                       11                    8  
    1359                  12                        4                   12  
    1266                   4                        4                    4  
    1310                  13                       15                    2  
    1417                   2                        2                    2  
    1044                  10                        5                    8  
    1336                   2                        2                    2  
    1280                   0                        0                    0  
    1285                   9                       15                    2  
    1096                   9                        3                   12  
    1454                   2                        0                    4  
    432                    3                        0                    4  
    187                    2                        2                    0  
    653                    1                        1                    2  
    207                    2                        1                    2  
    713                    7                        1                    1  
    512                    1                        2                    2  
    961                    8                        5                    7  
    845                    3                        1                    7  
    92                     2                        2                    2  
    101                    2                        2                    2  
    153                    2                        2                    2  
    1008                   7                        4                    5  
    140                    2                        1                    2  
    23                     0                        0                    0  
    1150                   8                        0                    0  
    104                    2                        0                    2  
    148                    2                        2                    2  
    188                    2                        2                    2  
    
    [40 rows x 31 columns]


    /tmp/ipykernel_4815/1642936327.py:2: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      attrition_filtered['JobRole'] = attrition_filtered['JobRole'].cat.remove_unused_categories()
    /tmp/ipykernel_4815/1642936327.py:5: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      attrition_clust = attrition_filtered.groupby("JobRole")\

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

```python
# Perform simple random sampling to get 0.25 of the population
attrition_srs = attrition_pop.sample(frac=0.25, random_state=2022)
```

```python
# Perform stratified sampling to get 0.25 of each relationship group
attrition_strat = attrition_pop.groupby("RelationshipSatisfaction")\
    .sample(frac=0.25, random_state=2022)
```

    /tmp/ipykernel_4815/1183472179.py:2: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      attrition_strat = attrition_pop.groupby("RelationshipSatisfaction")\

```python
# Create a list of unique RelationshipSatisfaction values
satisfaction_unique = list(attrition_pop['RelationshipSatisfaction'].unique())

# Randomly sample 2 unique satisfaction values
satisfaction_samp = random.sample(satisfaction_unique, k=2)

# Filter for satisfaction_samp and clear unused categories from RelationshipSatisfaction
satis_condition = attrition_pop['RelationshipSatisfaction'].isin(satisfaction_samp)
attrition_clust_prep = attrition_pop[satis_condition]
attrition_clust_prep['RelationshipSatisfaction'] = attrition_clust_prep['RelationshipSatisfaction'].cat.remove_unused_categories()

# Perform cluster sampling on the selected group, getting 0.25 of attrition_pop
attrition_clust = attrition_clust_prep.groupby("RelationshipSatisfaction")\
    .sample(n=len(attrition_pop) // 4, random_state=2022)

```

    /tmp/ipykernel_4815/1225069142.py:10: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      attrition_clust_prep['RelationshipSatisfaction'] = attrition_clust_prep['RelationshipSatisfaction'].cat.remove_unused_categories()
    /tmp/ipykernel_4815/1225069142.py:13: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      attrition_clust = attrition_clust_prep.groupby("RelationshipSatisfaction")\

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

```python
# Mean Attrition by RelationshipSatisfaction group
mean_attrition_pop = attrition_pop.groupby('RelationshipSatisfaction')['Attrition'].mean()

# Print the result
print(mean_attrition_pop)


# Calculate the same thing for the simple random sample 
mean_attrition_srs = attrition_srs.groupby('RelationshipSatisfaction')['Attrition'].mean()

# Print the result
print(mean_attrition_srs)


# Calculate the same thing for the stratified sample 
mean_attrition_strat = attrition_strat.groupby('RelationshipSatisfaction')['Attrition'].mean()

# Print the result
print(mean_attrition_strat)


# Calculate the same thing for the cluster sample 
mean_attrition_clust = attrition_clust.groupby('RelationshipSatisfaction')['Attrition'].mean()

# Print the result
print(mean_attrition_clust)
```

    RelationshipSatisfaction
    Low          0.206522
    Medium       0.148515
    High         0.154684
    Very_High    0.148148
    Name: Attrition, dtype: float64
    RelationshipSatisfaction
    Low          0.134328
    Medium       0.164179
    High         0.160000
    Very_High    0.155963
    Name: Attrition, dtype: float64
    RelationshipSatisfaction
    Low          0.144928
    Medium       0.078947
    High         0.165217
    Very_High    0.129630
    Name: Attrition, dtype: float64
    RelationshipSatisfaction
    High         0.149864
    Very_High    0.160763
    Name: Attrition, dtype: float64


    /tmp/ipykernel_4815/3036671708.py:2: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      mean_attrition_pop = attrition_pop.groupby('RelationshipSatisfaction')['Attrition'].mean()
    /tmp/ipykernel_4815/3036671708.py:9: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      mean_attrition_srs = attrition_srs.groupby('RelationshipSatisfaction')['Attrition'].mean()
    /tmp/ipykernel_4815/3036671708.py:16: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      mean_attrition_strat = attrition_strat.groupby('RelationshipSatisfaction')['Attrition'].mean()
    /tmp/ipykernel_4815/3036671708.py:23: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      mean_attrition_clust = attrition_clust.groupby('RelationshipSatisfaction')['Attrition'].mean()

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

```python
# added/edited
mean_attrition_pop = attrition_pop['Attrition'].mean()
```

```python
# Generate a simple random sample of 50 rows, with seed 2022
attrition_srs50 = attrition_pop.sample(n=50, random_state=2022)

# Calculate the mean employee attrition in the sample
mean_attrition_srs50 = attrition_srs50['Attrition'].mean()

# Calculate the relative error percentage
rel_error_pct50 = 100 * abs(mean_attrition_pop - mean_attrition_srs50) / mean_attrition_pop

# Print rel_error_pct50
print(rel_error_pct50)


# Generate a simple random sample of 100 rows, with seed 2022
attrition_srs100 = attrition_pop.sample(n=100, random_state=2022)

# Calculate the mean employee attrition in the sample
mean_attrition_srs100 = attrition_srs100['Attrition'].mean()

# Calculate the relative error percentage
rel_error_pct100 = 100 * abs(mean_attrition_pop - mean_attrition_srs100) / mean_attrition_pop

# Print rel_error_pct100
print(rel_error_pct100)

```

    62.78481012658227
    6.962025316455695

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
- Draw a histogram of the `mean_attritions` list with 16 bins.

**Answer**

```python
# Create an empty list
mean_attritions = []
# Loop 500 times to create 500 sample means
for i in range(500):
 mean_attritions.append(
     attrition_pop.sample(n=60)['Attrition'].mean()
 )
  
# Print out the first few entries of the list
print(mean_attritions[0:5])
```

    [0.21666666666666667, 0.2, 0.21666666666666667, 0.23333333333333334, 0.1]

```python
# Create an empty list
mean_attritions = []
# Loop 500 times to create 500 sample means
for i in range(500):
 mean_attritions.append(
     attrition_pop.sample(n=60)['Attrition'].mean()
 )

# Create a histogram of the 500 sample means
plt.hist(mean_attritions, bins=16)
plt.show()

```

![png](notebook_files/notebook_59_0.png)

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
- Add a column, `mean_roll`, to `dice`, that contains the mean of the five rolls as a categorical.
- Create a bar plot of the `mean_roll` categorical column, so it displays the count of each `mean_roll` in increasing order from `1.0` to `8.0`.

**Answer**

```python
# added/edited
import itertools
def expand_grid(data_dict):
    rows = itertools.product(*data_dict.values())
    return pd.DataFrame.from_records(rows, columns=data_dict.keys())
```

```python
# Expand a grid representing 5 8-sided dice
dice = expand_grid(
  {'die1': [1, 2, 3, 4, 5, 6, 7, 8],
   'die2': [1, 2, 3, 4, 5, 6, 7, 8],
   'die3': [1, 2, 3, 4, 5, 6, 7, 8],
   'die4': [1, 2, 3, 4, 5, 6, 7, 8],
   'die5': [1, 2, 3, 4, 5, 6, 7, 8]
  })

# Print the result
print(dice)
```

           die1  die2  die3  die4  die5
    0         1     1     1     1     1
    1         1     1     1     1     2
    2         1     1     1     1     3
    3         1     1     1     1     4
    4         1     1     1     1     5
    ...     ...   ...   ...   ...   ...
    32763     8     8     8     8     4
    32764     8     8     8     8     5
    32765     8     8     8     8     6
    32766     8     8     8     8     7
    32767     8     8     8     8     8
    
    [32768 rows x 5 columns]

```python
# Add a column of mean rolls and convert to a categorical
dice['mean_roll'] = (dice['die1'] + dice['die2'] + 
                     dice['die3'] + dice['die4'] + 
                     dice['die5']) / 5
dice['mean_roll'] = dice['mean_roll'].astype('category')

# Print result
print(dice)
```

           die1  die2  die3  die4  die5 mean_roll
    0         1     1     1     1     1       1.0
    1         1     1     1     1     2       1.2
    2         1     1     1     1     3       1.4
    3         1     1     1     1     4       1.6
    4         1     1     1     1     5       1.8
    ...     ...   ...   ...   ...   ...       ...
    32763     8     8     8     8     4       7.2
    32764     8     8     8     8     5       7.4
    32765     8     8     8     8     6       7.6
    32766     8     8     8     8     7       7.8
    32767     8     8     8     8     8       8.0
    
    [32768 rows x 6 columns]

```python
# Draw a bar plot of mean_roll
dice['mean_roll'].value_counts(sort=False).plot(kind="bar")
plt.show()
```

![png](notebook_files/notebook_64_0.png)

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
- Replicate the sampling code 1000 times, assigning each result to the list `sample_means_1000`.
- Plot `sample_means_1000` as a histogram with `20` bins.

**Answer**

```python
# Sample one to eight, five times, with replacement
five_rolls = np.random.choice(list(range(1, 9)), size=5, replace=True)

# Print the mean of five_rolls
print(five_rolls.mean())


# Replicate the sampling code 1000 times
sample_means_1000 = []
for i in range(1000):
    sample_means_1000.append(
    np.random.choice(list(range(1, 9)), size=5, replace=True).mean()
    )

# Print the first 10 entries of the result
print(sample_means_1000[0:10])
```

    4.8
    [4.2, 5.8, 4.8, 5.2, 3.4, 3.0, 3.6, 5.6, 6.2, 5.6]

```python
# Draw a histogram of sample_means_1000 with 20 bins
plt.hist(sample_means_1000, bins=20)
plt.show()
```

![png](notebook_files/notebook_67_0.png)

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

```python
# added/edited
sampling_distribution_5 = [attrition_pop.sample(n=5)['Attrition'].mean() for _ in range(1000)]
sampling_distribution_50 = [attrition_pop.sample(n=50)['Attrition'].mean() for _ in range(1000)]
sampling_distribution_500 = [attrition_pop.sample(n=500)['Attrition'].mean() for _ in range(1000)]
```

```python
# Calculate the mean of the mean attritions for each sampling distribution
mean_of_means_5 = np.mean(sampling_distribution_5)
mean_of_means_50 = np.mean(sampling_distribution_50)
mean_of_means_500 = np.mean(sampling_distribution_500)

# Print the results
print(mean_of_means_5)
print(mean_of_means_50)
print(mean_of_means_500)
```

    0.1516
    0.15776
    0.161136

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

```python
# Calculate the std. dev. of the mean attritions for each sampling distribution
sd_of_means_5 = np.std(sampling_distribution_5, ddof=1)
sd_of_means_50 = np.std(sampling_distribution_50, ddof=1)
sd_of_means_500 = np.std(sampling_distribution_500, ddof=1)

# Print the results
print(sd_of_means_5)
print(sd_of_means_50)
print(sd_of_means_500)
```

    0.15975907787341212
    0.05167642453627043
    0.012850316518850212

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
- Calculate the mean of the `danceability` column of `spotify_1_resample` using numpy.
- Replicate the expression provided 1000 times.
- Create a bootstrap distribution by drawing a histogram of `mean_danceability_1000`.

**Answer**

```python
# added/edited
spotify_sample = spotify_population[['artists', 'name', 'danceability']]
```

```python
# Generate 1 bootstrap resample
spotify_1_resample = spotify_sample.sample(frac=1, replace=True)

# Print the resample
print(spotify_1_resample)
```

                             artists  \
    36544            ['Neon Indian']   
    11257            ['Chuck Wicks']   
    32854        ['Chris Stapleton']   
    16980  ['Brian Stokes Mitchell']   
    22023          ['Blake Shelton']   
    ...                          ...   
    32160                 ['Weezer']   
    21041                    ['D12']   
    5436    ['Thousand Foot Krutch']   
    8847                 ['Haystak']   
    15389             ['Los Cafres']   
    
                                                        name  danceability  
    36544                                    Deadbeat Summer         0.635  
    11257                                Stealing Cinderella         0.512  
    32854                            When The Stars Come Out         0.471  
    16980                   The Impossible Dream (The Quest)         0.386  
    22023                                          Honey Bee         0.481  
    ...                                                  ...           ...  
    32160  (If You're Wondering If I Want You To) I Want ...         0.695  
    21041                                       Purple Pills         0.780  
    5436                           The End Is Where We Begin         0.463  
    8847                                        My First Day         0.911  
    15389                                            Momento         0.720  
    
    [41656 rows x 3 columns]

```python
# Calculate of the danceability column of spotify_1_resample
mean_danceability_1 = np.mean(spotify_1_resample['danceability'])

# Print the result
print(mean_danceability_1)
```

    0.5910867774150184

```python
# Replicate this 1000 times
mean_danceability_1000 = []
for i in range(1000):
 mean_danceability_1000.append(
        np.mean(spotify_sample.sample(frac=1, replace=True)['danceability'])
 )
  
# Print the result
print(mean_danceability_1000)
```

    [0.5904832773189936, 0.5913621663145765, 0.5900986028423276, 0.5905381817745344, 0.5930551997311311, 0.5921350057614749, 0.5915282288265796, 0.5903228034376802, 0.5916797076051469, 0.5913512027078932, 0.5904753648934128, 0.5904020069137699, 0.5920672748223546, 0.5902138131361628, 0.5923683238909161, 0.5919732259458421, 0.5916186647781831, 0.5915103106395238, 0.5907257105819089, 0.5900108387747264, 0.5915321226233916, 0.5919121999231804, 0.5913817361244479, 0.591548492414058, 0.5906278351257922, 0.5916459429613982, 0.589737142308431, 0.592048677261379, 0.5910523165930479, 0.5904263635490685, 0.5913645933358939, 0.5914446754369119, 0.5900231299212599, 0.5903838006529671, 0.5907538601882081, 0.591140786441329, 0.5901308382946034, 0.5896519036873439, 0.5903136690992894, 0.5927458493374304, 0.589624599097369, 0.5911874663913962, 0.591475434511235, 0.5923185687536009, 0.591359131937776, 0.590478540906472, 0.592409364797388, 0.5902524870366813, 0.5912395165162282, 0.5907730939120415, 0.5907289178029577, 0.591156306414442, 0.5918330468599962, 0.5913952755905513, 0.5897655871903207, 0.5903791890724025, 0.5922401166698674, 0.5920755497407336, 0.5924950547340119, 0.5921004057038601, 0.5903730699058959, 0.5910546739965431, 0.5930155007681966, 0.5914223065104667, 0.5923608555790283, 0.5905184439216438, 0.5904566256961782, 0.5917979354714806, 0.5920102986364509, 0.5916771653543308, 0.5913872767428461, 0.5916369022469752, 0.5922124927981564, 0.5914890483963894, 0.5925698962934511, 0.5916137771269445, 0.5918084309583254, 0.5898779239485308, 0.5903952971960823, 0.5923821226233916, 0.5907190368734396, 0.5920030679854043, 0.5905140628000768, 0.5890988741117726, 0.5913012867294027, 0.5921654383522181, 0.5902063904359517, 0.5904932134626463, 0.591419680238141, 0.5896741717879778, 0.5914068537545613, 0.5899188760322642, 0.5927475249663913, 0.5923182422700211, 0.5921214662953715, 0.5928632417898982, 0.5918749135778758, 0.5908296715959286, 0.5920378192817362, 0.5905234347993086, 0.5920720640483964, 0.5899042658920685, 0.5897471840791242, 0.5915836590167084, 0.5906831188784328, 0.5907866645861342, 0.5921760058574996, 0.5916359948146726, 0.5897575499327828, 0.592358791050509, 0.5916631457653159, 0.5916293355098905, 0.592049013347417, 0.5919747479354714, 0.5918134338390628, 0.5902727026118687, 0.5910721240637603, 0.5917459933743039, 0.5911953764163626, 0.591135553101594, 0.5914182734780103, 0.5916119670635684, 0.5920934415210294, 0.5916908824659112, 0.5906950571346266, 0.5913002040522373, 0.5909335893988861, 0.5900854738813135, 0.590873237948915, 0.5919345400422508, 0.591064674956789, 0.5908707581140772, 0.5922247287305549, 0.5917525926637219, 0.5917047532168234, 0.5922896461494143, 0.5906823362780872, 0.5916190968888035, 0.5907955156520069, 0.5925713318609563, 0.5908108363741119, 0.5923985500288074, 0.5916065488765124, 0.5924048660457076, 0.5911416602650279, 0.5924547388131362, 0.5920987300748993, 0.5904042154791627, 0.5904591775494527, 0.5895627520645285, 0.5924556798540427, 0.5896188256193584, 0.5914466511426926, 0.5912973569233723, 0.5912358411753409, 0.5911484011907049, 0.5913605723065105, 0.5915528783368543, 0.5917585605915114, 0.5920867149990398, 0.5921764979834838, 0.5908438016132129, 0.5894642692529287, 0.5900457821202229, 0.5916212190320722, 0.5894987708853466, 0.5905484299980794, 0.5915508378144806, 0.5891443681582486, 0.5913908488573075, 0.5896524102170155, 0.5918501728442482, 0.5916593263875551, 0.5924154311503744, 0.592710358651815, 0.591338215383138, 0.5906444161705396, 0.5923693849625504, 0.5912614845400422, 0.5926662209525638, 0.5906650230458996, 0.5907738549068562, 0.5907106203188017, 0.5914775950643365, 0.591847277703092, 0.5902916914730171, 0.5920472657000192, 0.5926184463222586, 0.5911366885922796, 0.5896768844824275, 0.5905353658536585, 0.5907644661033223, 0.5909612708853467, 0.590370107547532, 0.5905025950643363, 0.5910026286729403, 0.5912540762435182, 0.593195167562896, 0.5921138275398502, 0.5916718599961589, 0.5905263683502977, 0.5916313568273478, 0.5921575211254081, 0.591737560015364, 0.5921280823890915, 0.591289972632994, 0.5904983723833301, 0.5916871735164203, 0.5895689792586901, 0.5906049572690609, 0.5910513947570578, 0.5918021485500289, 0.5895366789898214, 0.5929524918379105, 0.590689701363549, 0.5893784928941809, 0.5929567769348953, 0.5912896005377376, 0.5914077851930094, 0.5906727506241598, 0.5910920299596697, 0.5922718719992319, 0.5898690656808143, 0.5908801373151528, 0.5911205780679855, 0.5915573290762436, 0.591242987804878, 0.5909604810831572, 0.5911857043403111, 0.5918410697138468, 0.5914789970232379, 0.5889998607643556, 0.5914601113885154, 0.5914371543115038, 0.5909444665834455, 0.5919988789130017, 0.5913364893412716, 0.5896376728442481, 0.5920864557326676, 0.5909875144036874, 0.5902108051661226, 0.5916272085653927, 0.5911097945073939, 0.5929610812367966, 0.5924649246207029, 0.5897899366237758, 0.5916090623199539, 0.5899920539658152, 0.5914983627808718, 0.5911182782792395, 0.5926587238333014, 0.5917499615901671, 0.5909758282120223, 0.590581947378529, 0.5910964446898407, 0.5900391780295756, 0.5898580444593815, 0.5913701531592087, 0.5914907768388706, 0.5902549068561552, 0.5902258474169388, 0.5922378720952564, 0.5908522229690801, 0.5900444689840598, 0.5905641420203572, 0.5910331284808911, 0.5914867222008834, 0.5917375624159785, 0.5901196490301517, 0.5900733291722681, 0.5926754825235261, 0.5921738741117726, 0.5900491741885924, 0.5910017620510851, 0.589170710101786, 0.5903479834837718, 0.590470671691953, 0.591103166410601, 0.5907768988861148, 0.590709799308623, 0.589774479066641, 0.5910628024774343, 0.590603600921836, 0.5914778615325523, 0.5912203452083733, 0.5902909808911081, 0.5905774390243903, 0.5916571922412138, 0.5918162017476474, 0.5913298276358748, 0.5898638995582871, 0.5894717495678895, 0.5918100417706933, 0.5898451531592087, 0.5891922196082198, 0.5912663289802189, 0.5930372191280968, 0.5923428269637028, 0.5918683647013636, 0.5918531448050701, 0.5903828884194354, 0.5915098089110813, 0.5921305814288459, 0.5911986964662954, 0.5924450691376992, 0.5911646869598617, 0.5912362324755137, 0.5910852050124832, 0.5909655535817169, 0.5907678365661608, 0.5907256337622432, 0.5915086854234683, 0.5904451483579797, 0.5893630329364317, 0.5917255017284425, 0.5931404623583638, 0.5898314408488572, 0.5901673948530824, 0.5905790234299979, 0.5902494646629537, 0.5898498295563663, 0.59080330804686, 0.5913244502592664, 0.5919703091991549, 0.5921447210485883, 0.5904210389859804, 0.5912809775302478, 0.5909333493374305, 0.5913779839638947, 0.5913244286537355, 0.5902360140195889, 0.5919529335509891, 0.5923058767044364, 0.5893797172076052, 0.5918232043403111, 0.5928163865949684, 0.5902684919339353, 0.5914397301709239, 0.5917977770309198, 0.5918354834837718, 0.5908931774534281, 0.5917331188784329, 0.5909505881505667, 0.5920850201651623, 0.5909491597849049, 0.5925820746111005, 0.590247217687728, 0.5910764187632033, 0.5912397253696947, 0.5923187872095257, 0.591640726425965, 0.5907609948146725, 0.5922856707317072, 0.5907923780487805, 0.5920727842327637, 0.5910420419627425, 0.5899135346648743, 0.5912088798732476, 0.5908260754753217, 0.5923036177261377, 0.5914079028231227, 0.5915132129825235, 0.5922223785289035, 0.5906516012099098, 0.5901489965431151, 0.5907184439216439, 0.5920137387171116, 0.5893574058959095, 0.5912918787209526, 0.5913235116189743, 0.5913579652391012, 0.5900302261378914, 0.5905078860188208, 0.5911350417706934, 0.5905881361628578, 0.590902158152487, 0.5916355458997504, 0.5907732835605914, 0.5905153951411561, 0.5913280727866334, 0.5909203596120607, 0.5917131193585559, 0.5919441136931054, 0.5919797724217399, 0.5908836470136356, 0.589338628288842, 0.5910906424044556, 0.5921332797196082, 0.5919957893220664, 0.5921546019781063, 0.5919729642788554, 0.5910902799116574, 0.5921844584213558, 0.5916362300748992, 0.5915281015940081, 0.590163004129057, 0.5911690272709814, 0.5915273405991934, 0.5917579436335703, 0.5923474337430381, 0.590587711254081, 0.5913340119070482, 0.5901678389667754, 0.5916295899750336, 0.5903278279239487, 0.5912790450355291, 0.5918726281928174, 0.5913120702899942, 0.5906665042250816, 0.5909019348953333, 0.5909666890724026, 0.5898924740733628, 0.590969012867294, 0.5893375360092183, 0.5932667058767044, 0.5902896149414251, 0.5902999495870943, 0.5917911465335126, 0.5899393844824274, 0.5913077851930094, 0.5912149054157865, 0.592189773381986, 0.5915650470520453, 0.5906236508546188, 0.589812039082005, 0.5908749231803342, 0.5908491357787593, 0.5903736268484733, 0.5911747359323988, 0.5926867582101017, 0.590919680238141, 0.5921013035337046, 0.5936474649510275, 0.5892090287113501, 0.5913220544459382, 0.5916915930478203, 0.5913270837334358, 0.5906346072594584, 0.5914360596312654, 0.5906868518340695, 0.5917406400038411, 0.5924978538505857, 0.5909106851353947, 0.5903478802573459, 0.5910671547916266, 0.5921510274630306, 0.5918073746879201, 0.5917937536009218, 0.5924592279623584, 0.5919778351257922, 0.591948470808527, 0.5915865205492606, 0.590699251008258, 0.5897704028231229, 0.5911213006529671, 0.5892321562319955, 0.5918927309391203, 0.5906680070097946, 0.5916809823314768, 0.5927818681582485, 0.5931186695794123, 0.5893693081428846, 0.591035385058575, 0.5933872263299405, 0.5903254465143076, 0.5907201507585942, 0.5916856323218744, 0.5911584237564816, 0.5903412161513347, 0.5918124207797195, 0.5902987708853467, 0.5913649630305359, 0.5906304469944306, 0.5916613765123871, 0.5904834669675437, 0.592378264835798, 0.5914941809103131, 0.5907038193777608, 0.5917628624927982, 0.5912103538505856, 0.5911267500480122, 0.5917723161129249, 0.5909969320145958, 0.5910079124255809, 0.5922134722488958, 0.5911900302477434, 0.590699896773574, 0.5917571178221626, 0.5912849721528711, 0.5917390003840983, 0.5922338270597274, 0.5913095496447089, 0.5906240013443441, 0.5918767884578452, 0.5921601281928175, 0.5902856131169578, 0.5910236964662954, 0.5905632297868254, 0.5910176973305166, 0.5918283800652967, 0.5918621038985981, 0.591180358171692, 0.5895208709429614, 0.5912244694641828, 0.590458606203188, 0.5913488645093143, 0.5906131265603994, 0.5923008666218552, 0.5912350609756097, 0.5907235956404838, 0.5910798780487805, 0.5897406712118303, 0.5911452155751873, 0.5922011426925293, 0.5920964830996736, 0.5897988765123872, 0.5905571274246207, 0.5916419171307855, 0.5912285769156903, 0.5916107067409258, 0.590851925292875, 0.5924900062415979, 0.5903158200499328, 0.5901537785673133, 0.5927825259266372, 0.5894671980026887, 0.5911143268676781, 0.5908451219512195, 0.5905410433070868, 0.5917963054541963, 0.5921850369694642, 0.5907336518148646, 0.5913030631841751, 0.591281512867294, 0.5925963030535818, 0.5903796956020742, 0.5908932902823123, 0.5903139571730364, 0.5905643916842712, 0.5903807062608027, 0.5901917850969848, 0.5923831956980987, 0.5908897973881314, 0.590823785289034, 0.5909050989053197, 0.5904301853274438, 0.5917854522757826, 0.5913855434991357, 0.590897445746111, 0.5909560495486844, 0.5914863597080852, 0.5892219104090648, 0.5912561959861725, 0.5915486700595354, 0.5911534496831188, 0.5907647349721529, 0.5914116069713847, 0.5905520837334357, 0.5910324803149605, 0.5903221696754369, 0.5895300893028615, 0.5902359444017669, 0.5911393820818129, 0.590938460245823, 0.5912115085461879, 0.5922611244478586, 0.5924137939312464, 0.590714468503937, 0.5903414466103322, 0.5904160841175341, 0.5907436407720376, 0.5897416242558094, 0.5922141804301901, 0.5910058382946035, 0.5912000744190513, 0.592735389859804, 0.5920073290762435, 0.5914622215287114, 0.5917395501248319, 0.5898290522373728, 0.5907417802957557, 0.5919756937776071, 0.5910708205300558, 0.5901777511042826, 0.5896256433647014, 0.5914056486460534, 0.5924654575571345, 0.5902890748031496, 0.5925741981947378, 0.5930200403303245, 0.5917165690416746, 0.590944809871327, 0.5918345976570002, 0.590706767332437, 0.5905817049164587, 0.5905273309967352, 0.5919590791242557, 0.5918386282888419, 0.5913449082965239, 0.590506318417515, 0.5912237516804302, 0.5907482043403112, 0.5912116981947378, 0.5913172412137507, 0.5895859828115997, 0.59218031496063, 0.5910701123487613, 0.5915788697906663, 0.5916713414634146, 0.5908037185519494, 0.591814300460918, 0.5915465479162666, 0.5914474001344345, 0.5903872527367006, 0.5909844608219705, 0.5921679493950452, 0.5905505353370464, 0.5919126104282696, 0.5907511162857692, 0.5915687223929326, 0.5914637723257153, 0.5912749543883233, 0.5917729858843864, 0.5918900854618783, 0.5911661417322833, 0.5912246207028999, 0.5898272157672364, 0.5923154239485308, 0.59046119886691, 0.5915591367390052, 0.5911270573266757, 0.5917182038601881, 0.5908415258306126, 0.5915349601497983, 0.591108390147878, 0.5914992606107163, 0.5902647709813713, 0.5919689000384099, 0.5923743902439025, 0.590360553101594, 0.5907594272133666, 0.5916975465719224, 0.5927992270021125, 0.5927374735932398, 0.5909915426349146, 0.5922494118494334, 0.5909895813328212, 0.5911837670443634, 0.5899159064720568, 0.591471778375264, 0.5905607859612061, 0.591973199539082, 0.5927668235068178, 0.5897241429806029, 0.5913718599961592, 0.5918488260994815, 0.5917903567313231, 0.5906900110428269, 0.5905448026694834, 0.5918715647205685, 0.5911325331284808, 0.5905902991165739, 0.590627266180142, 0.5922920395621278, 0.5922624519877089, 0.5904545155559823, 0.591161328500096, 0.5911340023045899, 0.5912042202803919, 0.5907323218743998, 0.5925752808719033, 0.5920173396389475, 0.5907495990973689, 0.5901652294987516, 0.5908514955828692, 0.5901617990205493, 0.59080349769541, 0.5905721168619166, 0.5901626152294988, 0.58951306894565, 0.5914764355675053, 0.5922987660841176, 0.59098199539082, 0.5913083181294411, 0.5907915450355291, 0.5917382777991165, 0.5909415570386019, 0.5917278111196466, 0.591113400230459, 0.5915106347224891, 0.5903749015748032, 0.5895739413289803, 0.5891706260802765, 0.5897838462646438, 0.5902705804686, 0.5905983963894756, 0.5918592471672748, 0.5913440440752833, 0.5911477698290764, 0.5914910937199923, 0.5910516636258883, 0.5906569665834455, 0.5913493686383715, 0.5911547820241982, 0.5919586854234683, 0.5927859492029961, 0.5908259794507393, 0.5919121135010562, 0.5910562584021509, 0.5912748055502209, 0.5905279335509891, 0.5905314312463992, 0.5924389475705781, 0.5901952779911657, 0.5916709045515652, 0.5889162713654695, 0.5906843840023046, 0.5917031111964663, 0.5908601305934319, 0.5931750888227386, 0.5912835365853658, 0.5913185879585174, 0.5913952755905513, 0.5918359660072978, 0.5901517164394086, 0.5907223929325907, 0.5914282720376417, 0.5924513035337047, 0.5904577563856346, 0.5911147901862875, 0.5910225321682351, 0.5919315464758979, 0.5903774270213175, 0.591558980699059, 0.5915754153063184, 0.5926885130593431, 0.5905076747647398, 0.5915503864989438, 0.5920508282120222, 0.5913191857115421, 0.592431443249472, 0.5902169123295564, 0.5917637675244862, 0.590042992606107, 0.5911381697714615, 0.5906696946418283, 0.5889463678701747, 0.5907671859996159, 0.5902544171307855, 0.591535867582101, 0.5903141900326483, 0.5915265315920877, 0.5906589951027463, 0.5924393124639907, 0.5916067025158439, 0.5923754777222969, 0.5917039130017285, 0.591700460917995, 0.59095862300749, 0.5894952251776455, 0.5907227866333782, 0.5908456068753601, 0.5919217879777223, 0.5908045659688881, 0.5915206932974842, 0.5922471768772807, 0.5912743830420586, 0.5909122191280968, 0.5916728994622623, 0.590833231707317, 0.5926038169771461, 0.5911497983483773, 0.5905778471288651, 0.5914501296331861, 0.590883123679662, 0.5929111820626081, 0.5918488837142308, 0.5918705348569233, 0.5910901046667947, 0.5909919435375457, 0.5901634914538122, 0.5905371279047437, 0.5911426373151527, 0.5916323098713271, 0.5905331044747455, 0.5895569521797581, 0.5911861436527752, 0.5916450115229499, 0.5902508906280007, 0.5921167634914538, 0.59082410457077, 0.5922980170923757, 0.5926719728250432, 0.5914537833685424, 0.5898345952563856, 0.5905705900710582, 0.589666204148262, 0.5926694593816016, 0.5911882826003457, 0.5903213582677165, 0.5902422676205108, 0.5903099385442673, 0.5907500984251968, 0.590956908968696, 0.59163823218744, 0.5912416170539656, 0.5909986676589206, 0.5919641300172844, 0.5898807278663338, 0.5908259986556559, 0.5912593479930863, 0.591672949875168, 0.5929127112540811, 0.5892284136739004, 0.5904119550604955, 0.5923577563856347, 0.5921519396965623, 0.5901745870942963, 0.591922678605723, 0.5919776934895333, 0.5922229090647205, 0.5915901478778567, 0.5902100657768389, 0.5901466367390051, 0.5914918259074323, 0.5903973665258306, 0.5924844584213559, 0.5910196322258499, 0.5915491237756866, 0.5905317601305936, 0.5906377592663722, 0.5918401550797003, 0.592267673324371, 0.5907611604570772, 0.5907186719800269, 0.5901091079316305, 0.5922834141540235, 0.5908578284040714, 0.5909972464951027, 0.5928875264067601, 0.5922587550412906, 0.591867358843864, 0.5929746543115038, 0.5915178629729211, 0.5919309991357787, 0.5920348857307471, 0.5915403567313233, 0.590376068273478, 0.5912691016900327, 0.5910870030727867, 0.5901725441713078, 0.5908154575571347, 0.5898679902054927, 0.590630401382754, 0.5905790498367581, 0.5917595784520837, 0.5922606299212598, 0.591809820914154, 0.5912776718840023, 0.5917186695794123, 0.5923147013635491, 0.5897221648742078, 0.5898429277895141, 0.5915817097176878, 0.5916955804686, 0.5898644973113116, 0.590032765988093, 0.5915836518148647, 0.5903874063760322, 0.5910479834837717, 0.5910085077779912, 0.590113633090071, 0.5930848617246015, 0.5906305406183984, 0.5907654455540619, 0.5915424068561551, 0.5906768724793547, 0.5921079532360285, 0.5930382633954292, 0.5921289706164778, 0.5926954100249665, 0.5907358435759555, 0.5907942433262915, 0.591347148069906, 0.5914871399078164, 0.5921851377952757, 0.592485569905896, 0.5918931702515844, 0.5905834021509506, 0.5914241909928941, 0.5914567481275207, 0.5909028159208757, 0.5914612012675246, 0.5915330612636835, 0.5917372071250241, 0.5912737948914921, 0.5919954676397158, 0.591094490589591, 0.5917958373343577, 0.5906191088918763, 0.5905231827347802, 0.5916223041098522, 0.59075973449203, 0.5919043067025159, 0.5914110980410985, 0.5913626008258115, 0.5901190632801997, 0.5916955780679853, 0.5907580948722874, 0.5931632874015748, 0.5926394444977915, 0.5915298276358747, 0.5924043139043597, 0.5913470352410217, 0.5914081524870367, 0.5896477290186287, 0.5926900374495871, 0.5909242774150182, 0.5902421331860958, 0.5915037017476473, 0.591567961398118, 0.5907774918379105, 0.5914618206260802, 0.592013822738621, 0.5915318321490302, 0.5911244118494334, 0.5899057302669484, 0.5915226545995774, 0.5897361244478586, 0.5915301445169964, 0.5915520213174572, 0.5929825187247936, 0.5912830204532361, 0.5906530223737276, 0.589741182542731, 0.5916811071634338, 0.590975628961014, 0.5914945818129441, 0.5908822474553486, 0.5900442001152295, 0.5919150782600346, 0.5910303701747648, 0.5920796547916266, 0.5915977362204725, 0.5908253672940272, 0.5927746014979833, 0.5913638995582869, 0.5899234948146724, 0.590129441136931, 0.5913435039370079, 0.5914221648742078, 0.5909184439216439, 0.5913370606875359, 0.5910621783176494, 0.5927747383330132, 0.5908786633378145, 0.5917759458421356, 0.5904179806030343, 0.5920447978682543, 0.5916216967543692, 0.5913136450931438, 0.591582516324179, 0.5933729762819281, 0.5907876968503937, 0.5908844272133665, 0.5902402967159592, 0.5898390772037642, 0.5917083901478779, 0.5922032744382562, 0.5919466607451508, 0.5901147949875167, 0.5914866861916649, 0.590289658152487, 0.590450900230459, 0.5905990445554062, 0.5933620270789322, 0.5900572882657961, 0.5899880137315153, 0.5905335605915114, 0.5912624615901669, 0.5919886931054349, 0.5919942001152294, 0.5908987900902631, 0.590823622047244, 0.5934161825427309, 0.5908748583637412, 0.590442983003649, 0.5914128768964856, 0.5926596576723643, 0.5902695169963511, 0.5918666146533513, 0.5918392524486269, 0.5894006673708468, 0.5906669963510659, 0.5906520237180719, 0.5917478298444402, 0.5906291146533512, 0.5908409784904936, 0.5913112924908778, 0.5917522109660073]

```python
# Draw a histogram of the resample means
plt.hist(mean_danceability_1000)
plt.show()
```

![png](notebook_files/notebook_79_0.png)

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

```python
# added/edited
spotify_sample = spotify_population.sample(n=500)
```

```python
mean_popularity_2000_samp = []

# Generate a sampling distribution of 2000 replicates
for i in range(2000):
    mean_popularity_2000_samp.append(
     # Sample 500 rows and calculate the mean popularity     
     spotify_population.sample(n=500)['popularity'].mean()
    )

# Print the sampling distribution results
print(mean_popularity_2000_samp)


mean_popularity_2000_boot = []

# Generate a bootstrap distribution of 2000 replicates
for i in range(2000):
    mean_popularity_2000_boot.append(
     # Resample 500 rows and calculate the mean popularity
     spotify_sample.sample(n=500, replace=True)['popularity'].mean()
    )

# Print the bootstrap distribution results
print(mean_popularity_2000_boot)

```

    [55.046, 54.702, 54.438, 55.026, 54.644, 55.558, 55.514, 54.494, 55.908, 54.686, 55.028, 53.936, 55.326, 55.25, 55.378, 55.116, 53.982, 54.42, 55.18, 55.04, 55.012, 54.724, 54.278, 54.604, 54.682, 54.662, 54.292, 54.158, 55.424, 55.238, 53.84, 54.728, 54.082, 54.882, 54.986, 54.83, 55.302, 54.438, 54.082, 55.426, 55.048, 55.592, 54.828, 54.992, 54.286, 54.69, 54.368, 54.582, 55.284, 55.844, 56.126, 54.132, 55.458, 55.492, 54.436, 54.286, 54.764, 54.928, 54.504, 55.182, 54.682, 54.482, 55.6, 54.048, 54.52, 54.064, 54.844, 56.312, 54.424, 55.034, 55.134, 54.464, 55.62, 55.068, 55.212, 55.656, 54.432, 54.398, 54.38, 55.14, 55.022, 54.552, 55.526, 54.414, 54.54, 54.94, 55.11, 54.662, 55.276, 56.318, 55.124, 54.624, 54.55, 54.79, 55.266, 54.842, 55.292, 54.524, 54.224, 54.42, 55.522, 55.086, 55.474, 55.172, 54.778, 55.624, 53.984, 55.144, 54.682, 54.568, 55.542, 54.916, 54.642, 55.082, 54.722, 54.756, 55.114, 54.464, 53.98, 54.8, 54.392, 54.726, 55.188, 55.062, 54.816, 54.316, 53.87, 55.418, 54.024, 55.22, 54.704, 54.686, 55.606, 54.848, 54.372, 55.756, 54.946, 54.244, 54.394, 54.754, 55.088, 54.51, 54.476, 55.654, 55.192, 54.272, 55.13, 54.818, 55.356, 55.084, 54.656, 54.73, 55.454, 54.742, 54.88, 54.072, 54.578, 54.588, 54.478, 54.724, 55.1, 55.184, 54.262, 54.474, 54.268, 54.938, 55.096, 54.594, 54.212, 54.742, 54.592, 55.434, 55.324, 55.048, 54.632, 54.61, 54.974, 54.994, 55.45, 55.23, 55.348, 55.048, 54.824, 55.184, 54.738, 54.678, 54.462, 54.62, 54.906, 54.726, 55.882, 55.47, 55.9, 54.0, 53.398, 54.776, 54.682, 54.416, 54.9, 55.104, 54.166, 54.296, 54.742, 55.104, 55.072, 54.208, 54.66, 54.62, 54.704, 54.934, 54.706, 54.46, 55.212, 54.684, 54.62, 54.576, 55.112, 55.152, 55.034, 54.966, 54.63, 54.42, 54.178, 55.1, 55.584, 53.986, 55.468, 55.108, 55.092, 54.412, 54.436, 54.36, 54.52, 54.764, 53.89, 53.924, 54.456, 54.956, 54.79, 54.692, 54.958, 54.788, 54.554, 55.496, 54.826, 54.576, 54.358, 55.04, 55.026, 54.252, 54.352, 54.914, 53.882, 54.33, 55.084, 54.638, 55.154, 54.572, 54.638, 54.812, 55.43, 55.28, 54.656, 53.962, 55.204, 55.108, 54.85, 54.652, 55.424, 54.658, 55.272, 55.248, 54.78, 55.212, 54.466, 54.724, 55.47, 55.096, 55.036, 55.47, 55.06, 54.894, 54.912, 54.758, 55.064, 55.282, 54.484, 54.608, 55.462, 55.364, 54.812, 54.826, 54.584, 55.052, 54.9, 54.638, 55.63, 54.982, 54.062, 54.738, 54.226, 54.654, 54.422, 54.652, 55.194, 54.616, 54.016, 55.098, 54.34, 54.554, 55.714, 55.866, 55.644, 54.954, 54.274, 55.09, 54.576, 55.038, 55.448, 54.648, 56.142, 55.246, 54.838, 55.572, 54.606, 53.848, 55.05, 54.814, 54.464, 54.9, 54.872, 56.0, 54.19, 54.33, 54.892, 54.466, 55.132, 54.484, 54.792, 55.462, 54.012, 55.902, 54.196, 54.578, 54.622, 55.574, 55.2, 55.478, 55.02, 54.608, 55.224, 55.24, 54.746, 55.382, 55.188, 55.198, 55.236, 54.338, 55.022, 54.724, 53.894, 54.746, 55.202, 55.572, 54.666, 55.046, 54.384, 54.592, 55.712, 54.25, 55.86, 55.518, 54.366, 54.576, 55.01, 54.638, 54.236, 54.388, 54.332, 54.948, 54.962, 54.9, 54.584, 54.636, 54.682, 55.082, 55.402, 53.636, 54.31, 54.482, 53.954, 55.446, 55.42, 54.822, 55.32, 54.048, 55.358, 54.884, 55.212, 55.816, 56.076, 54.572, 55.0, 54.308, 54.392, 54.844, 55.208, 55.076, 54.69, 55.328, 54.33, 54.416, 54.908, 53.842, 53.962, 54.946, 55.174, 54.34, 54.486, 54.506, 53.688, 54.442, 55.148, 55.374, 55.314, 55.898, 55.176, 54.712, 55.094, 53.836, 54.756, 54.544, 54.56, 55.258, 54.642, 55.314, 54.198, 54.856, 55.874, 54.644, 54.818, 54.268, 54.576, 54.316, 54.494, 55.318, 54.338, 54.728, 53.58, 55.864, 54.43, 55.89, 54.612, 55.124, 56.31, 55.334, 54.57, 54.3, 55.232, 54.156, 54.532, 54.682, 54.338, 54.906, 54.666, 54.604, 54.074, 54.948, 53.8, 55.26, 54.308, 55.222, 54.522, 54.53, 55.294, 55.628, 54.598, 55.024, 55.498, 55.1, 54.972, 54.778, 54.996, 56.006, 54.778, 54.222, 54.906, 54.782, 55.148, 55.086, 54.658, 55.05, 54.974, 54.896, 54.738, 55.624, 54.006, 54.734, 54.876, 54.946, 54.362, 55.49, 54.38, 54.5, 55.094, 55.11, 54.748, 54.728, 55.102, 54.952, 54.764, 54.472, 53.626, 54.896, 55.348, 54.944, 54.794, 55.396, 54.192, 54.162, 54.872, 54.626, 54.688, 54.344, 55.608, 54.104, 54.766, 54.436, 54.54, 54.428, 55.138, 55.464, 55.57, 55.276, 53.958, 54.568, 54.858, 55.434, 53.884, 55.092, 54.206, 55.986, 55.152, 53.918, 54.884, 56.03, 55.184, 54.894, 55.214, 54.796, 54.602, 55.24, 55.564, 55.742, 54.77, 54.348, 55.218, 54.246, 54.45, 55.42, 54.234, 54.286, 54.792, 55.604, 55.41, 54.68, 54.5, 54.226, 54.596, 54.522, 54.574, 54.936, 54.322, 54.706, 54.132, 54.944, 54.896, 55.482, 54.554, 54.572, 55.102, 55.006, 54.982, 54.626, 54.106, 54.608, 55.096, 55.412, 55.46, 55.348, 54.246, 55.174, 55.156, 54.87, 55.22, 54.064, 55.178, 54.626, 55.442, 54.538, 55.198, 55.238, 55.504, 54.328, 55.434, 54.536, 54.754, 54.866, 55.002, 55.114, 54.416, 54.944, 54.914, 54.67, 55.678, 55.024, 54.006, 54.086, 55.092, 55.59, 55.072, 53.944, 55.142, 55.46, 54.998, 55.07, 54.32, 54.926, 55.634, 54.17, 55.196, 54.692, 54.788, 54.276, 55.734, 54.932, 54.536, 55.438, 55.244, 54.19, 54.388, 54.832, 54.374, 54.55, 54.632, 55.702, 54.7, 55.224, 54.742, 54.16, 55.46, 54.416, 55.212, 55.118, 54.05, 54.25, 54.852, 54.62, 55.49, 55.274, 55.72, 54.056, 55.444, 54.456, 55.336, 54.67, 53.56, 54.948, 54.792, 55.19, 54.67, 54.5, 55.226, 55.218, 54.458, 55.016, 55.052, 55.084, 55.08, 55.236, 54.226, 54.752, 55.114, 55.162, 54.598, 55.838, 55.308, 54.75, 55.198, 54.73, 55.13, 55.538, 53.952, 54.736, 54.978, 54.79, 54.692, 54.87, 54.608, 55.158, 54.326, 55.336, 54.892, 54.6, 54.27, 55.152, 54.412, 55.216, 54.838, 55.476, 55.312, 55.51, 54.83, 54.92, 54.524, 54.154, 54.48, 55.072, 55.354, 54.18, 55.414, 54.762, 54.592, 54.476, 55.386, 55.082, 55.184, 54.074, 54.026, 55.006, 55.026, 53.942, 54.282, 54.488, 55.466, 54.576, 54.548, 55.666, 55.002, 53.876, 55.708, 54.784, 54.428, 54.83, 55.03, 54.99, 54.576, 55.344, 55.546, 55.048, 55.336, 55.106, 54.894, 55.562, 54.928, 54.446, 54.692, 54.776, 54.42, 54.446, 54.882, 55.53, 54.908, 54.494, 54.826, 54.826, 55.174, 53.9, 54.512, 56.152, 54.954, 55.524, 55.202, 55.066, 53.934, 54.996, 54.848, 53.734, 54.86, 53.95, 55.572, 55.164, 53.386, 54.98, 54.798, 55.186, 55.022, 55.36, 54.864, 54.892, 54.372, 53.786, 54.936, 54.548, 55.128, 55.65, 56.014, 55.018, 54.644, 54.37, 54.268, 55.074, 54.598, 54.816, 53.752, 54.79, 55.656, 54.888, 54.112, 55.042, 55.088, 54.132, 54.894, 54.19, 54.438, 54.866, 55.69, 54.814, 55.042, 55.06, 55.08, 55.566, 54.322, 54.292, 54.792, 55.768, 54.916, 54.658, 53.974, 54.79, 54.648, 55.368, 55.216, 55.212, 55.476, 55.408, 54.666, 55.67, 54.432, 54.24, 53.852, 55.186, 54.822, 55.212, 54.526, 54.514, 54.884, 54.054, 54.822, 55.698, 54.722, 54.61, 55.23, 54.91, 55.24, 54.72, 54.422, 55.204, 55.098, 55.656, 55.472, 54.536, 54.642, 53.78, 54.692, 54.392, 55.112, 55.002, 54.604, 54.938, 53.982, 55.442, 55.05, 55.156, 55.362, 55.128, 54.718, 54.298, 55.298, 55.144, 54.956, 54.184, 55.056, 54.928, 55.254, 54.636, 54.944, 54.934, 54.528, 53.5, 54.494, 55.392, 54.986, 54.882, 55.8, 55.194, 54.828, 54.57, 54.284, 55.164, 55.558, 54.988, 54.818, 54.958, 54.334, 55.052, 54.302, 54.988, 55.224, 54.756, 53.96, 54.992, 54.854, 55.554, 53.76, 55.042, 54.414, 55.468, 54.968, 54.136, 55.144, 53.854, 54.538, 55.31, 55.278, 54.804, 54.686, 54.11, 55.072, 55.246, 54.99, 54.746, 55.052, 54.712, 54.574, 54.628, 54.384, 54.696, 55.03, 55.212, 54.498, 55.42, 54.882, 56.162, 55.472, 54.192, 54.578, 54.168, 54.472, 55.182, 55.31, 53.974, 54.384, 54.95, 53.928, 54.67, 54.85, 54.49, 54.26, 55.438, 54.192, 55.008, 54.664, 54.696, 54.434, 54.568, 54.516, 55.18, 55.068, 54.834, 55.172, 54.878, 54.916, 54.222, 54.064, 55.338, 55.068, 54.324, 54.064, 55.324, 54.336, 54.478, 54.878, 55.772, 55.11, 53.938, 54.864, 54.832, 55.166, 55.352, 54.962, 55.528, 55.286, 54.094, 55.098, 54.468, 54.442, 54.974, 54.526, 54.638, 55.03, 54.694, 54.314, 55.108, 54.87, 54.026, 55.012, 55.284, 54.868, 54.524, 55.172, 54.58, 55.18, 55.44, 54.23, 54.194, 54.99, 55.4, 54.634, 54.568, 54.97, 54.328, 53.508, 54.938, 55.376, 54.864, 54.704, 54.062, 54.406, 54.25, 55.406, 54.656, 55.422, 54.896, 55.27, 54.856, 55.762, 55.28, 55.748, 54.708, 54.426, 54.508, 54.408, 54.858, 54.516, 54.002, 54.792, 55.248, 55.56, 54.348, 54.576, 54.696, 54.836, 54.348, 54.638, 54.534, 54.498, 53.994, 54.494, 54.994, 54.526, 53.98, 54.754, 54.064, 54.906, 55.552, 54.988, 55.23, 55.102, 54.698, 54.394, 54.398, 54.436, 55.642, 54.368, 54.686, 54.174, 53.7, 54.42, 55.058, 54.888, 55.696, 54.92, 54.092, 54.362, 54.916, 54.442, 54.606, 55.002, 53.994, 54.896, 54.592, 54.666, 54.818, 55.172, 54.442, 55.558, 54.65, 54.76, 54.228, 54.822, 55.11, 55.3, 55.654, 54.64, 55.01, 54.454, 55.218, 54.678, 55.002, 55.228, 54.892, 54.404, 54.996, 54.658, 55.378, 55.582, 54.678, 55.596, 55.104, 54.846, 54.422, 54.86, 55.276, 55.098, 54.48, 55.19, 55.754, 55.166, 55.356, 54.458, 55.32, 55.84, 55.488, 53.854, 55.148, 54.56, 54.67, 55.336, 54.276, 55.12, 53.97, 54.764, 55.124, 54.65, 54.476, 53.738, 54.826, 54.96, 54.508, 54.952, 54.734, 55.598, 54.268, 54.938, 54.84, 54.376, 54.944, 55.43, 54.252, 53.834, 54.29, 55.078, 54.43, 54.336, 54.648, 54.878, 54.212, 54.798, 54.462, 54.666, 55.88, 54.548, 54.668, 55.476, 55.232, 54.802, 56.304, 55.11, 54.402, 55.454, 54.362, 54.634, 54.63, 54.984, 55.114, 55.322, 54.394, 54.352, 54.764, 54.344, 55.082, 54.27, 54.59, 54.714, 55.136, 55.006, 54.8, 54.624, 54.546, 54.114, 54.868, 54.436, 54.614, 56.086, 54.38, 55.792, 54.2, 54.202, 54.512, 54.654, 54.922, 54.838, 54.53, 53.938, 54.006, 54.332, 54.224, 55.374, 54.698, 55.112, 55.628, 54.716, 54.594, 55.174, 54.94, 55.598, 54.814, 54.454, 55.146, 55.33, 55.016, 54.962, 55.174, 54.58, 54.456, 54.518, 53.996, 55.314, 54.896, 54.662, 54.448, 54.704, 54.386, 54.774, 54.594, 54.182, 55.664, 53.974, 54.042, 54.364, 54.558, 54.104, 54.77, 54.956, 54.2, 53.998, 54.266, 54.306, 54.214, 55.632, 55.216, 54.924, 54.698, 54.466, 55.254, 54.48, 54.282, 55.116, 55.17, 54.672, 56.122, 54.554, 54.324, 53.438, 55.572, 55.484, 54.746, 56.358, 54.692, 54.306, 54.75, 53.792, 55.026, 53.994, 54.778, 54.63, 54.716, 54.654, 54.944, 55.778, 55.498, 54.608, 54.864, 55.344, 55.728, 54.304, 55.084, 55.024, 54.742, 54.538, 53.894, 54.352, 54.314, 55.86, 55.148, 54.208, 55.672, 54.958, 54.518, 55.018, 54.848, 54.812, 55.174, 54.092, 54.784, 54.884, 55.772, 55.248, 54.218, 53.876, 55.226, 56.04, 55.098, 54.362, 54.35, 55.4, 55.116, 54.74, 54.894, 55.062, 54.476, 55.016, 54.992, 55.42, 54.14, 54.736, 53.9, 54.886, 53.982, 55.384, 54.82, 54.98, 54.732, 54.634, 54.78, 54.482, 54.374, 54.52, 54.436, 54.89, 55.322, 55.0, 54.546, 54.564, 55.426, 54.324, 55.264, 54.532, 55.208, 55.784, 54.284, 54.404, 54.368, 54.88, 54.658, 55.6, 55.152, 54.392, 54.764, 54.864, 54.762, 55.042, 54.512, 54.386, 54.456, 55.39, 55.18, 55.23, 55.036, 54.288, 54.414, 53.682, 54.932, 55.032, 54.81, 54.864, 54.758, 54.818, 54.572, 54.54, 55.752, 55.638, 54.568, 53.992, 54.884, 54.688, 54.436, 54.866, 54.414, 54.97, 54.784, 54.908, 54.764, 55.088, 54.508, 54.582, 55.124, 55.002, 53.65, 54.452, 54.602, 55.1, 54.264, 54.368, 54.61, 54.726, 55.114, 54.136, 54.734, 55.784, 54.984, 55.272, 54.93, 54.27, 54.52, 54.788, 54.592, 54.836, 55.33, 54.206, 54.452, 55.258, 55.042, 54.522, 55.076, 55.444, 55.0, 55.098, 54.702, 55.372, 54.472, 54.552, 54.558, 54.77, 54.518, 54.988, 55.046, 55.72, 54.698, 54.336, 55.376, 54.64, 54.974, 54.46, 55.234, 54.866, 54.836, 54.758, 54.794, 54.776, 55.362, 55.252, 55.202, 53.966, 54.906, 55.468, 55.564, 54.168, 54.96, 54.916, 54.602, 54.394, 54.696, 54.962, 54.898, 54.468, 55.166, 55.444, 54.28, 55.198, 54.864, 54.288, 55.174, 55.464, 54.736, 54.636, 54.546, 53.778, 54.852, 54.242, 54.838, 54.832, 55.402, 54.096, 54.772, 55.434, 54.808, 54.352, 54.632, 55.288, 54.544, 54.214, 55.07, 53.748, 55.318, 55.346, 54.312, 55.444, 54.412, 54.406, 55.474, 54.944, 55.114, 55.148, 54.662, 54.068, 55.12, 55.566, 54.588, 54.772, 54.336, 55.228, 55.218, 54.502, 53.8, 55.076, 54.874, 54.51, 55.234, 54.844, 55.484, 55.112, 53.83, 54.902, 55.516, 54.912, 55.08, 55.6, 53.742, 55.124, 54.196, 54.884, 54.99, 55.064, 55.332, 55.578, 55.144, 54.562, 54.884, 54.888, 54.732, 55.136, 55.296, 54.188, 54.232, 55.306, 54.164, 53.962, 55.496, 54.966, 54.608, 54.486, 55.272, 54.208, 55.316, 54.662, 55.396, 55.776, 55.3, 54.934, 55.764, 54.17, 55.374, 54.754, 54.838, 54.816, 55.004, 55.41, 55.25, 55.36, 54.882, 54.384, 54.948, 54.742, 55.334, 54.588, 55.472, 55.03, 53.334, 54.752, 54.8, 55.348, 55.006, 55.344, 54.64, 54.898, 55.73, 54.948, 53.986, 54.978, 54.286, 54.768, 55.44, 54.83, 54.888, 53.862, 54.096, 55.472, 55.224, 54.876, 55.334, 53.55, 54.878, 55.67, 54.724, 55.256, 54.498, 55.014, 55.092, 55.154, 54.584, 55.39, 54.89, 54.806, 55.8, 54.936, 54.798, 55.268, 55.4, 54.484, 54.836, 55.04, 54.13, 54.842, 54.504, 54.94, 55.12, 55.136, 55.944, 55.6, 54.508, 54.506, 55.29, 54.578, 54.634, 55.056, 54.682, 55.166, 54.83, 56.116, 55.29, 55.264, 54.88, 55.294, 54.24, 54.778, 55.27, 54.58, 53.978, 54.466, 54.424, 54.738, 55.53, 54.424, 54.16, 54.326, 54.352, 55.074, 54.342, 55.434, 54.24, 55.222, 54.11, 54.344, 54.758, 54.25, 53.67, 54.956, 54.572, 54.14, 54.418, 54.71, 53.78, 55.284, 55.14, 54.66, 54.428, 55.468, 54.952, 54.388, 54.866, 54.41, 54.978, 54.596, 54.664, 54.996, 54.86, 54.052, 55.902, 55.014, 54.886, 54.986, 55.642, 53.918, 54.748, 54.93, 54.314, 54.924, 55.322, 54.2, 55.352, 54.298, 55.786, 54.224, 53.806, 53.526, 54.25, 55.59, 54.886, 55.428, 55.412, 55.056, 54.836, 55.43, 54.612, 54.222, 55.296, 54.308, 54.94, 55.0, 54.928, 55.03, 55.03, 55.508, 54.404, 54.634, 55.222, 54.958, 54.43, 55.136, 54.108, 55.462, 54.446, 55.024, 54.098, 55.69, 53.682, 55.022, 54.132, 54.704, 54.448, 54.828, 55.172, 54.108, 54.72, 55.094, 53.846, 55.028, 54.802, 54.512, 54.726, 54.732, 55.088, 55.174, 55.362, 54.738, 54.714, 54.194, 55.778, 54.498, 55.422, 54.562, 55.312, 55.044, 54.248, 54.332, 55.012, 55.032, 54.058, 53.93, 54.774, 54.8, 54.958, 55.488, 54.472, 54.472, 54.526, 54.522, 55.016, 54.434, 54.506, 55.246, 54.586, 53.944, 54.048, 55.488, 54.718, 54.338, 54.908, 55.19, 54.484, 55.06, 54.538, 55.002, 54.636, 55.494, 55.512, 54.582, 55.454, 54.676, 54.776, 55.392, 54.45, 54.744, 54.586, 55.026, 54.488, 55.934, 54.418, 54.874, 55.296, 54.854, 55.156, 55.254, 54.164, 55.244, 54.894, 54.57, 54.498, 54.948, 54.376, 55.216, 54.488, 54.882, 55.224, 54.024, 54.024, 54.528, 54.558, 55.306, 54.592, 55.226, 54.472, 54.084, 54.37, 55.256, 55.256, 55.412, 54.738, 54.818, 55.242, 54.594, 54.618, 54.786, 54.708, 54.642, 55.242, 54.482, 54.19, 54.856, 55.208, 54.68, 55.102, 55.046, 55.208, 54.57, 55.438, 54.164, 54.524, 54.422, 54.514, 55.332, 54.912, 54.466, 54.666, 54.88, 55.348, 54.718, 54.662, 54.976, 55.01, 54.936, 54.77, 55.304, 54.544, 55.336, 55.232, 54.634, 54.766, 54.822, 53.874, 54.846, 55.358, 55.084, 54.65, 54.522, 55.262, 54.364, 54.266, 55.18, 55.082, 54.728, 54.406, 55.446, 54.78, 54.29, 55.336, 55.764, 55.422, 54.746, 55.228, 54.938, 55.218, 54.74, 55.448, 55.38, 54.238, 55.612, 55.606, 53.954, 54.598, 53.398, 54.624, 55.02, 54.506, 55.182, 55.358, 54.822, 55.172, 55.71, 54.892, 53.99, 54.768, 54.906, 54.674, 55.378, 54.148, 54.394, 55.174, 56.746, 53.98, 54.374, 54.996, 54.684, 54.536, 53.5, 53.714, 55.19, 54.874, 54.75, 54.722, 55.668, 53.95, 54.632, 54.526, 54.296, 55.048, 54.214, 54.878, 54.626, 54.37, 55.228, 54.55, 54.572, 55.312, 54.494, 54.268, 55.186, 55.16, 54.934, 55.06, 55.192, 55.222, 54.472, 55.046, 54.94, 54.766, 54.414, 53.962, 53.838, 54.478, 55.522, 55.274, 54.33, 55.026, 54.522, 54.508, 55.034, 54.622, 54.088, 55.232, 54.198, 54.996, 54.744, 54.398, 55.37, 55.51, 54.924, 55.022]
    [55.004, 54.386, 54.192, 54.254, 55.276, 55.098, 54.576, 54.106, 54.842, 54.204, 54.782, 55.108, 54.388, 54.044, 53.966, 55.932, 55.39, 55.286, 54.756, 55.054, 54.786, 55.244, 54.622, 54.284, 55.258, 54.894, 55.056, 54.89, 54.892, 54.336, 53.996, 55.054, 54.672, 55.794, 54.396, 54.696, 54.74, 54.808, 54.15, 55.032, 55.862, 55.112, 53.55, 54.714, 54.96, 54.672, 54.528, 55.394, 55.038, 55.576, 54.69, 55.484, 54.386, 55.024, 54.562, 54.806, 53.734, 55.232, 55.036, 55.516, 54.418, 54.22, 55.044, 55.986, 55.558, 55.512, 55.424, 54.584, 54.834, 55.746, 55.092, 55.574, 55.242, 54.84, 55.234, 55.274, 55.26, 54.864, 54.652, 54.778, 54.426, 56.15, 54.256, 54.888, 55.004, 55.968, 54.618, 54.382, 54.262, 54.586, 54.788, 54.872, 54.732, 54.956, 54.724, 55.034, 54.638, 54.45, 54.824, 55.636, 55.21, 55.554, 55.496, 55.58, 54.31, 54.852, 55.012, 54.878, 54.712, 54.98, 54.292, 55.162, 55.116, 54.394, 54.552, 54.412, 54.692, 54.728, 55.782, 55.394, 55.184, 55.212, 54.43, 54.496, 55.324, 54.924, 55.284, 55.416, 55.366, 54.64, 54.764, 54.826, 54.666, 54.702, 55.392, 55.562, 55.704, 55.312, 54.654, 55.132, 55.286, 55.596, 55.516, 55.186, 53.99, 54.172, 54.914, 54.308, 55.632, 55.412, 54.812, 55.306, 55.596, 54.89, 55.72, 54.88, 54.162, 53.972, 55.458, 56.152, 54.97, 53.958, 54.894, 54.03, 54.492, 54.864, 54.262, 54.194, 54.83, 55.536, 55.104, 55.42, 55.348, 55.196, 54.862, 54.766, 54.93, 55.374, 55.01, 54.926, 54.462, 55.72, 55.182, 54.438, 55.058, 55.58, 54.816, 54.506, 55.754, 54.262, 54.938, 55.058, 54.942, 54.756, 54.49, 55.162, 54.698, 54.832, 55.702, 54.826, 55.45, 54.862, 54.434, 54.952, 55.11, 54.61, 55.93, 55.104, 54.858, 54.502, 54.624, 55.018, 54.854, 54.338, 55.528, 54.732, 54.624, 54.704, 53.7, 55.742, 54.474, 54.708, 55.21, 54.772, 55.414, 54.63, 55.182, 55.202, 55.026, 54.46, 55.47, 54.02, 54.894, 55.198, 55.674, 55.472, 54.412, 54.644, 55.036, 54.974, 53.194, 54.188, 54.694, 54.93, 55.064, 55.074, 54.196, 55.158, 54.65, 54.304, 54.474, 54.984, 54.78, 54.508, 54.728, 54.8, 55.438, 54.55, 56.01, 55.33, 55.532, 54.086, 55.432, 54.48, 55.536, 54.532, 55.328, 54.936, 54.924, 54.578, 54.48, 54.776, 54.428, 55.126, 54.772, 55.062, 54.488, 54.71, 54.582, 54.574, 54.866, 54.732, 54.824, 54.646, 55.04, 54.058, 54.118, 54.962, 55.41, 54.226, 55.016, 54.738, 54.588, 55.51, 54.724, 55.228, 54.746, 55.768, 54.872, 54.32, 53.962, 54.176, 55.262, 54.218, 54.382, 55.244, 55.098, 55.336, 54.99, 54.93, 55.738, 54.606, 55.426, 55.03, 54.022, 55.118, 55.414, 54.912, 54.704, 54.962, 55.35, 55.228, 54.18, 55.06, 54.95, 55.512, 55.09, 54.804, 55.08, 55.04, 55.484, 55.144, 54.04, 54.48, 55.396, 54.476, 54.326, 55.064, 54.794, 54.938, 53.956, 55.432, 55.502, 55.498, 55.228, 55.502, 55.3, 55.436, 54.836, 54.586, 55.496, 53.984, 55.276, 54.89, 53.822, 55.28, 54.786, 55.052, 54.354, 55.542, 55.056, 54.62, 54.676, 55.588, 55.528, 55.458, 54.212, 55.684, 55.378, 55.166, 54.972, 54.408, 55.708, 54.96, 55.038, 54.322, 55.406, 55.136, 54.056, 55.548, 55.672, 54.792, 55.674, 54.514, 55.322, 55.448, 55.252, 54.364, 55.042, 54.716, 55.032, 54.608, 55.536, 55.564, 55.0, 54.654, 54.972, 54.148, 54.876, 55.082, 54.378, 54.188, 54.936, 54.684, 54.544, 55.25, 54.85, 55.114, 54.932, 55.194, 54.992, 54.538, 55.518, 55.46, 54.736, 54.868, 54.52, 54.816, 55.74, 55.056, 54.952, 54.792, 54.622, 54.288, 54.952, 55.118, 55.598, 55.298, 54.498, 54.642, 53.996, 54.744, 54.464, 54.968, 54.576, 54.26, 55.284, 55.29, 55.244, 54.316, 55.258, 55.172, 54.32, 55.248, 55.384, 55.884, 55.114, 54.582, 54.466, 54.162, 55.078, 55.08, 55.024, 54.858, 54.786, 55.52, 54.498, 54.374, 55.124, 54.776, 54.724, 54.518, 54.374, 55.466, 53.616, 55.508, 54.422, 54.452, 55.052, 54.566, 54.284, 55.914, 54.86, 55.18, 54.028, 54.696, 54.924, 54.588, 54.668, 54.966, 55.05, 54.744, 54.312, 55.302, 55.64, 55.282, 55.832, 53.774, 54.696, 55.024, 54.862, 55.85, 54.398, 55.812, 54.802, 55.062, 55.198, 54.75, 55.962, 54.972, 55.8, 54.034, 55.036, 55.522, 55.172, 55.052, 54.828, 54.86, 54.016, 54.706, 54.81, 54.988, 54.852, 55.462, 54.176, 55.364, 55.18, 55.33, 55.83, 55.662, 55.248, 54.784, 54.992, 55.47, 54.248, 55.078, 55.242, 54.608, 54.39, 54.496, 54.382, 54.74, 54.688, 54.672, 55.132, 54.312, 54.95, 54.306, 53.96, 54.458, 54.304, 54.362, 55.91, 54.382, 55.618, 54.624, 55.02, 54.788, 55.042, 54.622, 54.8, 54.408, 55.168, 56.008, 55.06, 55.126, 55.428, 55.37, 54.702, 55.406, 54.676, 55.026, 54.794, 54.206, 54.904, 55.31, 54.128, 54.918, 55.708, 55.136, 54.538, 54.986, 55.004, 55.342, 54.502, 54.688, 54.034, 54.238, 55.466, 55.146, 55.472, 54.744, 55.096, 55.49, 54.732, 54.382, 54.674, 54.69, 54.996, 54.086, 53.882, 54.846, 55.234, 55.3, 54.416, 54.986, 54.608, 54.752, 54.748, 54.902, 55.092, 55.204, 55.4, 55.104, 54.866, 54.118, 55.332, 54.858, 54.796, 55.052, 54.182, 54.238, 54.074, 54.45, 55.052, 54.726, 54.588, 55.132, 55.006, 55.438, 55.26, 54.552, 54.456, 54.424, 55.29, 54.636, 55.278, 53.682, 55.46, 54.794, 55.392, 54.912, 54.906, 54.954, 54.826, 54.678, 55.254, 55.02, 54.468, 54.644, 55.118, 55.11, 54.598, 56.344, 55.736, 54.134, 55.01, 54.032, 54.844, 55.032, 54.596, 55.592, 54.67, 54.938, 55.582, 54.658, 53.848, 54.036, 54.744, 54.616, 55.116, 55.162, 55.49, 54.69, 55.292, 55.316, 54.054, 54.45, 54.95, 54.254, 55.324, 54.954, 55.524, 55.382, 55.236, 54.458, 54.796, 54.914, 54.618, 54.716, 54.772, 55.24, 55.036, 55.85, 54.7, 55.38, 55.076, 53.926, 55.448, 55.112, 55.182, 54.066, 54.914, 54.594, 55.524, 54.622, 55.052, 55.336, 54.546, 54.668, 54.904, 54.378, 55.558, 53.832, 55.092, 54.518, 54.932, 54.568, 55.914, 55.92, 54.336, 54.632, 55.04, 54.354, 55.34, 55.34, 55.516, 54.49, 55.428, 55.506, 54.972, 55.102, 55.22, 54.698, 55.572, 54.238, 55.038, 54.946, 53.594, 55.908, 54.57, 54.468, 54.952, 54.918, 54.798, 54.356, 55.386, 54.888, 54.418, 54.094, 55.906, 54.326, 54.8, 54.186, 54.914, 54.802, 55.046, 55.588, 54.164, 55.322, 55.182, 54.308, 54.764, 54.972, 54.792, 55.766, 54.27, 55.184, 55.132, 54.292, 55.454, 54.728, 54.196, 55.096, 54.99, 54.496, 54.844, 54.77, 54.74, 54.328, 54.862, 54.682, 55.158, 55.172, 55.064, 55.9, 54.744, 54.592, 54.918, 54.868, 55.524, 55.858, 54.794, 55.324, 54.21, 55.112, 54.744, 55.352, 55.236, 55.022, 54.912, 54.678, 53.542, 53.808, 54.98, 54.272, 54.622, 54.86, 54.516, 54.706, 55.088, 54.88, 55.334, 54.902, 55.046, 54.516, 54.69, 55.222, 54.792, 54.446, 55.216, 55.03, 54.706, 53.734, 54.194, 55.042, 55.156, 54.972, 54.388, 54.762, 55.06, 55.75, 55.188, 54.788, 55.786, 55.578, 55.254, 55.338, 55.758, 55.234, 55.072, 54.738, 54.86, 55.298, 54.89, 54.906, 54.582, 53.688, 54.578, 55.004, 54.138, 55.268, 54.304, 54.67, 54.462, 55.442, 54.796, 55.716, 54.526, 54.968, 54.52, 54.22, 55.34, 54.704, 54.852, 54.716, 54.962, 54.44, 55.432, 54.484, 54.864, 55.582, 55.242, 55.194, 55.116, 54.236, 55.586, 55.554, 54.66, 54.45, 54.726, 55.196, 54.586, 55.224, 55.116, 55.22, 54.508, 54.484, 55.95, 55.336, 55.11, 55.056, 55.152, 54.794, 54.94, 55.368, 55.97, 56.004, 54.954, 55.004, 54.274, 55.13, 54.062, 55.142, 54.49, 54.714, 54.456, 54.982, 54.594, 55.036, 55.176, 54.806, 54.688, 54.202, 54.666, 55.106, 55.266, 55.158, 55.096, 54.254, 54.354, 54.578, 54.694, 54.594, 54.636, 54.78, 54.456, 54.992, 55.122, 55.248, 53.972, 55.002, 54.156, 54.89, 54.988, 55.4, 54.67, 54.834, 55.128, 55.918, 55.148, 54.782, 54.718, 55.016, 55.63, 54.4, 54.64, 55.598, 55.19, 55.814, 54.362, 55.468, 53.776, 55.58, 54.098, 55.054, 54.286, 54.166, 55.558, 55.506, 55.6, 54.42, 55.244, 54.0, 55.456, 54.71, 54.956, 55.416, 54.582, 55.504, 54.51, 54.024, 54.788, 55.294, 54.754, 55.33, 54.894, 54.384, 54.59, 55.12, 55.076, 54.726, 55.376, 55.054, 54.566, 55.974, 55.89, 55.378, 54.812, 55.874, 54.542, 54.47, 54.356, 54.388, 54.934, 54.396, 54.93, 55.576, 55.39, 54.59, 55.764, 54.77, 54.43, 54.966, 54.836, 54.772, 55.242, 55.356, 55.1, 55.182, 54.986, 54.354, 54.734, 54.208, 54.224, 54.918, 54.192, 54.652, 54.622, 54.744, 54.702, 55.67, 55.43, 54.514, 55.2, 55.208, 55.812, 53.994, 53.69, 54.652, 54.484, 54.612, 54.638, 54.158, 55.362, 55.404, 54.738, 55.276, 54.164, 55.22, 54.7, 54.594, 55.512, 55.568, 55.48, 55.072, 55.094, 54.714, 54.164, 53.674, 55.7, 54.524, 54.614, 54.642, 54.604, 55.466, 55.342, 54.884, 55.074, 55.522, 54.924, 53.884, 54.73, 54.904, 56.14, 54.322, 54.832, 55.286, 54.426, 54.578, 55.92, 55.076, 54.494, 54.994, 54.722, 54.896, 55.428, 55.2, 54.358, 54.874, 53.88, 54.704, 55.732, 54.966, 55.01, 55.356, 55.508, 54.338, 54.278, 53.496, 54.968, 54.184, 54.84, 55.37, 54.166, 55.684, 55.116, 54.48, 54.824, 54.794, 55.258, 54.468, 56.004, 55.424, 55.926, 55.102, 53.434, 55.752, 54.888, 55.334, 54.646, 55.05, 54.164, 54.526, 54.292, 55.126, 55.386, 54.854, 54.342, 54.866, 54.912, 54.982, 54.696, 54.904, 53.978, 54.602, 54.57, 54.864, 54.974, 54.732, 55.872, 55.16, 55.318, 54.996, 55.14, 55.24, 55.3, 55.028, 54.416, 55.882, 54.536, 55.198, 53.882, 55.16, 54.564, 54.88, 55.214, 54.054, 54.954, 54.706, 54.79, 54.632, 54.452, 54.936, 54.696, 55.734, 55.138, 54.528, 55.314, 55.562, 54.734, 55.368, 54.692, 54.54, 54.814, 55.58, 55.444, 55.496, 54.514, 55.216, 55.146, 54.258, 55.046, 54.008, 55.454, 55.086, 54.424, 56.096, 54.41, 54.622, 55.22, 54.776, 54.85, 55.418, 55.116, 54.476, 54.402, 54.524, 54.972, 55.312, 55.556, 54.838, 54.71, 54.67, 55.506, 54.94, 54.796, 55.282, 54.962, 54.092, 55.556, 54.408, 55.186, 55.188, 55.214, 55.796, 54.622, 54.892, 55.478, 54.056, 54.842, 54.378, 54.888, 54.882, 55.146, 54.528, 54.294, 54.91, 54.954, 54.764, 55.118, 55.598, 55.032, 54.66, 54.53, 54.284, 55.132, 55.22, 54.944, 54.956, 55.052, 54.92, 55.584, 54.624, 55.928, 54.652, 55.232, 55.1, 54.834, 55.766, 55.324, 54.598, 53.844, 54.502, 54.97, 54.94, 55.118, 54.918, 54.71, 54.726, 54.354, 53.878, 55.076, 54.654, 54.622, 54.288, 55.216, 54.448, 54.838, 54.948, 54.582, 53.964, 54.48, 55.232, 54.678, 55.404, 54.37, 55.252, 55.704, 55.844, 54.682, 54.392, 55.112, 54.276, 55.096, 54.972, 55.298, 54.62, 54.284, 55.054, 55.084, 54.664, 54.926, 54.838, 55.468, 55.058, 55.116, 55.502, 55.144, 55.332, 55.048, 55.654, 54.702, 54.738, 54.594, 54.728, 54.376, 55.174, 54.592, 54.752, 54.77, 54.5, 53.542, 55.092, 53.704, 55.144, 54.98, 55.01, 54.368, 55.544, 55.984, 54.714, 54.814, 55.294, 55.294, 55.842, 55.104, 55.034, 54.304, 55.274, 54.86, 55.494, 55.662, 55.148, 54.676, 54.57, 55.902, 55.41, 54.822, 55.846, 55.094, 54.56, 55.272, 55.288, 55.516, 54.68, 54.97, 55.2, 54.976, 55.226, 55.442, 55.778, 55.084, 54.488, 54.444, 55.408, 55.378, 54.59, 54.77, 55.202, 54.54, 55.402, 55.14, 54.418, 54.932, 54.374, 54.406, 54.776, 54.776, 55.448, 55.96, 54.728, 54.75, 54.722, 55.242, 55.886, 55.084, 54.878, 54.93, 54.906, 54.634, 54.742, 53.758, 55.762, 53.946, 55.05, 54.434, 55.128, 54.822, 54.254, 55.258, 55.718, 55.202, 54.88, 54.766, 55.04, 54.97, 54.712, 55.102, 54.928, 54.688, 55.686, 55.136, 54.512, 54.408, 55.514, 55.078, 55.34, 54.97, 54.63, 54.426, 55.162, 54.988, 55.214, 54.662, 55.182, 55.54, 54.35, 54.62, 54.902, 54.862, 54.954, 54.706, 55.116, 54.396, 54.63, 55.742, 55.25, 54.728, 55.248, 54.482, 55.076, 53.96, 54.666, 54.646, 54.984, 55.254, 54.468, 54.482, 55.154, 54.12, 54.904, 55.156, 55.384, 54.776, 53.956, 54.75, 54.534, 54.378, 55.212, 54.79, 54.85, 54.738, 54.706, 56.28, 53.818, 55.116, 54.904, 53.84, 55.158, 55.47, 55.634, 54.67, 54.526, 54.912, 55.716, 54.784, 54.814, 55.092, 55.426, 55.374, 55.394, 55.266, 55.298, 56.21, 54.09, 55.442, 53.646, 55.562, 55.808, 55.088, 55.808, 55.054, 55.326, 54.58, 55.452, 55.084, 54.364, 55.682, 55.66, 54.73, 54.716, 54.276, 55.11, 54.192, 53.81, 54.514, 54.986, 54.14, 55.266, 54.718, 54.658, 55.744, 54.544, 55.486, 54.502, 54.708, 54.604, 54.66, 55.506, 54.448, 54.472, 55.208, 55.178, 54.874, 55.216, 54.742, 53.796, 54.62, 55.29, 55.396, 55.438, 54.31, 54.42, 55.548, 54.952, 53.876, 54.802, 56.22, 54.68, 54.986, 54.304, 54.628, 54.87, 54.302, 54.992, 54.862, 54.666, 55.176, 55.284, 55.218, 54.584, 54.098, 54.9, 54.94, 55.428, 54.078, 54.196, 55.178, 55.97, 53.926, 55.542, 55.424, 55.054, 55.622, 55.838, 55.374, 54.436, 55.774, 54.986, 54.996, 53.602, 54.55, 55.094, 54.998, 54.374, 54.58, 55.464, 54.878, 55.15, 55.14, 54.706, 55.808, 55.684, 55.696, 54.84, 54.27, 54.518, 54.864, 55.16, 55.146, 54.124, 54.824, 55.094, 54.87, 54.898, 55.09, 54.704, 54.962, 54.114, 55.346, 55.678, 55.016, 55.198, 54.32, 54.46, 55.258, 55.198, 54.984, 54.76, 55.266, 55.208, 54.57, 54.74, 54.882, 55.776, 54.538, 54.822, 54.702, 54.454, 55.792, 54.446, 55.136, 54.182, 54.408, 55.276, 55.056, 55.074, 55.47, 54.492, 55.04, 55.592, 54.766, 54.564, 54.84, 55.112, 54.83, 54.066, 54.602, 53.874, 54.444, 54.12, 55.398, 54.382, 55.228, 54.714, 55.184, 54.722, 55.252, 54.028, 54.388, 55.15, 55.416, 54.778, 54.664, 54.514, 54.68, 54.898, 55.322, 54.274, 54.834, 54.878, 54.226, 54.904, 54.656, 55.13, 54.538, 55.564, 54.508, 54.17, 55.192, 55.018, 55.622, 55.312, 54.37, 54.698, 54.686, 54.204, 54.738, 55.244, 54.822, 54.988, 54.994, 54.492, 55.416, 55.326, 55.348, 54.488, 55.426, 54.284, 55.148, 54.218, 54.534, 54.464, 54.6, 55.278, 54.97, 55.834, 55.524, 55.114, 55.152, 54.61, 54.39, 55.43, 55.014, 54.668, 54.544, 54.568, 54.468, 55.402, 54.524, 54.978, 54.608, 54.846, 54.372, 54.838, 54.748, 54.712, 55.018, 54.658, 53.738, 55.182, 55.156, 54.42, 55.324, 55.036, 54.568, 55.194, 56.26, 54.408, 54.572, 54.68, 54.928, 55.02, 54.18, 55.674, 55.408, 54.756, 54.854, 55.096, 54.72, 54.292, 54.948, 55.694, 52.964, 55.136, 55.642, 55.564, 55.158, 54.93, 55.392, 54.412, 54.86, 54.706, 55.138, 54.6, 54.94, 53.946, 55.368, 55.636, 54.54, 54.722, 55.134, 54.326, 55.582, 54.954, 55.506, 54.36, 55.352, 54.236, 54.148, 55.304, 55.412, 54.728, 54.752, 54.532, 54.908, 54.866, 54.972, 54.662, 55.402, 54.876, 55.01, 55.072, 54.754, 55.654, 53.992, 56.288, 54.224, 54.338, 54.88, 55.424, 54.934, 54.65, 55.246, 54.396, 55.096, 54.818, 54.996, 53.864, 55.304, 54.864, 54.586, 54.192, 55.6, 55.616, 55.182, 54.35, 54.714, 55.124, 55.554, 54.19, 55.17, 54.54, 55.064, 53.848, 54.954, 54.978, 55.882, 54.758, 55.132, 54.78, 54.23, 55.134, 54.942, 55.202, 54.392, 55.66, 54.724, 54.842, 54.572, 54.624, 55.472, 55.054, 55.11, 54.214, 54.836, 55.142, 55.254, 54.82, 55.744, 55.396, 53.968, 54.42, 55.802, 54.798, 54.24, 56.466, 55.56, 55.324, 54.682, 55.324, 54.836, 54.932, 54.24, 55.902, 54.822, 54.67, 54.596, 54.97, 54.576, 54.604, 54.616, 54.38, 54.394, 55.272, 54.46, 54.414, 54.196, 55.908, 54.802, 55.43, 54.868, 54.57, 54.692, 54.45, 55.914, 55.008, 54.952, 54.782, 55.232, 54.418, 55.31, 54.298, 55.268, 54.668, 54.484, 55.056, 55.548, 55.242, 55.496, 55.074, 54.75, 55.402, 54.892, 54.238, 54.478, 55.026, 54.492, 55.704, 54.332, 54.678, 54.858, 54.424, 54.818, 54.244, 54.852, 54.838, 54.22, 55.038, 55.192, 54.226, 55.584, 54.732, 55.346, 54.794, 55.558, 55.488, 55.44, 54.848, 54.426, 53.9, 54.516, 54.996, 54.48, 54.392, 55.122, 54.934, 54.178, 55.394, 55.506, 54.69, 54.722, 55.476, 55.048, 54.852, 54.572, 55.206, 54.472, 54.708, 53.99, 55.412, 55.638, 55.54, 55.382, 54.516, 54.95, 55.626, 55.506, 55.446, 54.732, 55.194, 54.384, 54.13, 54.668, 54.656, 55.776, 54.914, 55.094, 54.986, 54.194, 55.18, 56.102, 55.884, 54.272, 54.426, 54.044, 55.446, 55.36, 54.444, 55.152, 54.92, 55.53, 55.688, 54.778, 55.158, 54.95, 54.824, 54.942, 54.822, 54.778, 54.738, 54.728, 54.872, 54.866, 54.818, 54.792, 55.056, 55.318, 54.66, 54.938, 55.172, 54.678, 54.568, 55.112, 54.44, 54.668, 54.834, 54.294, 55.13, 55.514, 55.286, 54.494, 55.702, 55.76, 53.714, 54.778, 54.756, 54.552, 54.584, 54.36, 54.506, 55.348, 54.668, 55.408, 55.344, 54.52, 54.152, 55.0, 54.54, 54.306, 55.098, 55.054, 54.17, 54.474, 55.264, 54.82, 55.344, 55.032, 55.55]

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

```python
# added/edited
sampling_distribution = [
    spotify_population.sample(n=500)['popularity'].mean()
    for _ in range(5000)
]
bootstrap_distribution = [
    spotify_sample.sample(n=500, replace=True)['popularity'].mean()
    for _ in range(5000)
]
```

```python
# Calculate the population mean popularity
pop_mean = spotify_population['popularity'].mean()

# Calculate the original sample mean popularity
samp_mean = spotify_sample['popularity'].mean()

# Calculate the sampling dist'n estimate of mean popularity
samp_distn_mean = np.mean(sampling_distribution)

# Calculate the bootstrap dist'n estimate of mean popularity
boot_distn_mean = np.mean(bootstrap_distribution)

# Print the means
print([pop_mean, samp_mean, samp_distn_mean, boot_distn_mean])
```

    [54.837142308430955, 54.896, 54.8391872, 54.8951956]

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

```python
# added/edited
spotify_sample = spotify_population.sample(n=5000)
sampling_distribution = [
    spotify_population.sample(n=5000)['popularity'].mean()
    for _ in range(5000)
]
bootstrap_distribution = [
    spotify_sample.sample(n=5000, replace=True)['popularity'].mean()
    for _ in range(5000)
]
```

```python
# Calculate the population std dev popularity
pop_sd = spotify_population['popularity'].std(ddof=0)

# Calculate the original sample std dev popularity
samp_sd = spotify_sample['popularity'].std()

# Calculate the sampling dist'n estimate of std dev popularity
samp_distn_sd = np.std(sampling_distribution, ddof=1) * np.sqrt(5000)

# Calculate the bootstrap dist'n estimate of std dev popularity
boot_distn_sd = np.std(bootstrap_distribution, ddof=1) * np.sqrt(5000)

# Print the standard deviations
print([pop_sd, samp_sd, samp_distn_sd, boot_distn_sd])

```

    [10.880065274257536, 11.124775194341003, 10.065837217676954, 11.098028092809901]

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

```python
pip install scipy
```

```python
# added/edited
from scipy.stats import norm
```

```python
# Generate a 95% confidence interval using the quantile method
lower_quant = np.quantile(bootstrap_distribution, 0.025)
upper_quant = np.quantile(bootstrap_distribution, 0.975)

# Print quantile method confidence interval
print((lower_quant, upper_quant))


# Find the mean and std dev of the bootstrap distribution
point_estimate = np.mean(bootstrap_distribution)
standard_error = np.std(bootstrap_distribution, ddof=1)

# Find the lower limit of the confidence interval
lower_se = norm.ppf(0.025, loc=point_estimate, scale=standard_error)

# Find the upper limit of the confidence interval
upper_se = norm.ppf(0.975, loc=point_estimate, scale=standard_error)

# Print standard error method confidence interval
print((lower_se, upper_se))

```

    (54.329995, 54.942634999999996)
    (54.321025328468686, 54.9362573115313)
