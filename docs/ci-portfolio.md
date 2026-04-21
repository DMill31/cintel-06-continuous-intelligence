# Continuous Intelligence Portfolio

Daniel Miller

2026-04

This page summarizes my work on **continuous intelligence** projects.

## 1. Professional Project

### Repository Link

[Project1](https://github.com/DMill31/cintel-01-getting-started)

### Brief Overview of Project Tools and Choices

**Notable folders:**

src/cintel/
  - Houses the scripts that run the continuous intelligence pipeline

data/
  - Where the input data is kept

artifacts/
  - Where the output data is kept

docs/
  - Keeps the documentation for the project


**Project Tools:**

Each project is updated through Visual Studio Code.  A virtual environment for the project is created using uv.

Documentation for each project is kept in README.md and docs/index.md.


**Choices:**

The script itself follows the pattern of setting up the logger and getting the paths correct before starting the pipeline.

In the Project 1 script, the pipeline simply ensures that the paths to the directories are correct as this will be a necessary part of future projects.

My addition to this project was extra error handling in case the paths were incorrect.

## 2. Anomaly Detection

### Repository Link

[Project2](https://github.com/DMill31/cintel-02-static-anomalies)

### Techniques

This project worked with data from a clinic's patient records.  The data contained two columns:

- age_years: The age of the patient
- height_inches: How tall the patient is in inches

To detect anomalies, upper and lower bounds were set as thresholds.

In this case, the upper bounds were 100 years for age and 6'2 for height.

The lower bounds were 18 years for age and 4'8 for height.

The script went through the data, and every row that was outside any of the bounds was detected as an anomaly.

### Artifacts

[Artifacts_Folder](https://github.com/DMill31/cintel-02-static-anomalies/tree/main/artifacts)

There are three files in the artifacts folder:

- anomalies_case.csv - This is the example output file with the anomalies from the example input data.
- anomalies_miller.csv - This is the true output file with the two anomalies that were detected.
- anomalies_taxi.csv - This is an extra output file from taxi service input data (added for extra fun/practice).

Of the two anomalies detected in anomalies_miller.csv, they were both age out-of-bounds with one patient being 102 years old and the other 118.

### Insights

This means that the system can detect anomalies successfully when discussing older individuals.

The fact that no anomalies were detected via height either means that there were no height anomalies or that the upper height bound was set too tall, but it is hard to say for such a small dataset.

These bounds may need to be reconsidered if applied to a dataset much larger than 24 patients, as that dataset would be much more statistically significant and representative of the general population.

## 3. Signal Design

### Repository Link

[Project3](https://github.com/DMill31/cintel-03-signal-design)

### Signals

This project starts with the input data based on system metrics.

The three columns of the original data are:

- requests
- errors
- total_latency_ms

For my code, however, a timestamp column was added to the input data.

With that, 6 signals were created:

- error_rate: How frequently errors occur
  - A performance metric to see if the errors are high or low in frequency

- avg_latency_ms: The average response time in milliseconds
  - This puts each request into perspective and allows us to see if each request had an overall high, low, or normal latency

- request_volume: Number of requests
  - Can help with comprehension when next to throughput_rps

- throughput_rps: Requests per second
  - Performance metric of system efficiency

- poor_experience: Flag for high error rate OR high average latency
  - Allows us to easily flag and find poor system performance

- hour_of_day: Hour of the day the observation took place
  - Allows for visuals to be created and is a cleaner time compared to the timestamp

### Artifacts

[Artifacts_Folder](https://github.com/DMill31/cintel-03-signal-design/tree/main/artifacts)

There are three files in the artifacts folder:

- signals_case.csv - the example output file
- signals_miller.csv - the output file after a modification was made to the example
- signals_custom_miller.csv - the output file that contains all 6 of the created signals

Every row in the table returned "false" for poor_experience, implying that error rates and average latencies were all in normal ranges.

Similarly, throughput_rps gave values between 29 and 40, which is another normal range.

### Insights

The signals show that the system is performing well.

There was no poor performance flag and all metrics were found to be in normal ranges.

The system can be kept as is as it's passing bare minimum standards.

The system can still be made more efficient.  While not necessary, it would be for the best.


## 4. Rolling Monitoring

### Repository Link

[Project4](https://github.com/DMill31/cintel-04-rolling-monitoring)

### Techniques

The data for this project was time series data, so when calculating statistics, we used rolling windows.

By only looking at a few adjacent rows to do calculations, we can see how these stats change over time, which can give us insights.

For the base case, a window size of 3 was used, meaning that three rows were compared at a time.  Rolling means and standard deviations were calculated for the modification.

When discussing the custom project, rolling sum and coefficient of variation were also calculated using a window size of 5.

### Artifacts

[Artifacts_Folder](https://github.com/DMill31/cintel-04-rolling-monitoring/tree/main/artifacts)

There are four files in the artifacts folder:

- rolling_metrics_case.csv - the example output file with rolling mean
- rolling_metrics_miller.csv - the modified output file with rolling mean and standard deviation
- rolling_metrics_transit_miller.csv - the custom project output file with rolling mean, standard deviation, sum, and coefficient of variation
- rolling_plot_transit_miller.png - Plot of rolling mean vs coefficient of variation

The results of the custom project show a positive trend of increasing rides.  We also see a jump in data from days 15-20.

![rolling_plot](rolling_plot_transit_miller.png)

### Insights

While there is generally a steady increase in rides over time, between days 10-19, a there was a great surge of riders.

If the data were to of continued being taken, that steady increase of riders would have continued.

Demand for rides is increasing, so it would be profitable for ride companies to make rides more convenient to access as well as increasing the price of each ride.

## 5. Drift Detection

### Repository Link

[Project5](https://github.com/DMill31/cintel-05-drift-detection)

### Techniques

In this project, we started with two input datasets.

One dataset contained reference data that we would consider normal.  The other data is current data that we compare to the norm to see if there are any differences.

The mean difference for each numeric column is calculated and compared to a difference threshold.  If the difference is greater than the magnitude of the threshold, we flag that column as drifting.

### Artifacts

[Artifacts_Folder](https://github.com/DMill31/cintel-05-drift-detection/tree/main/artifacts)

There are four files in the artifacts folder:

- drift_summary_case.csv - the example output file that contains reference data, current data, differences, and flags
- drift_summary_long_case.csv - the same file as above but formatted vertically
- drift_summary_miller.csv - the modified output file that now also includes standard deviation differences and percent changes
- drift_summary_long_miller.csv - the same file as above but formatted vertically

The first few rows of the long output file contains the reference file's statistics.  The next few rows contain the current data's statistics.

After those rows, the difference between the statistics is shown, and in my file the percent change between these statistics is also given.

Lastly, the flags for drifting are at the end with either a "True" or "False" depending on if the data is drifting.

With this data, every column was drifting.

### Insights

The entire system experienced a uniform shift.

While all columns increased, the spread stayed roughly the same, given the smaller change in standard deviations.

Detecting drift allows us to see what exactly is drifting so we can target that specific metric to get it back into a normal range.

If the entire system is shifting like this case, then it allows us to learn to look at the system as a whole.

## 6. Continuous Intelligence Pipeline

### Repository Link

(clickable link to your repository)

### Techniques

(Describe how signals and monitoring techniques were combined.)

### Artifacts

(clickable link to artifacts/ folder and explain result files)

### Assessment

(What does the pipeline say about the system state?)
