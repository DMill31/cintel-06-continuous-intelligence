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

(clickable link to your repository)

### Signals

(List the custom signals you created and why.)

### Artifacts

(clickable link to artifacts/ folder and explain result files)

### Insights

(What did the signals reveal?)

## 4. Rolling Monitoring

### Repository Link

(clickable link to your repository)

### Techniques

(Explain how rolling windows were used.)

### Artifacts

(clickable link to artifacts/ folder and explain result files)

### Insights

(What patterns appeared?)

## 5. Drift Detection

### Repository Link

(clickable link to your repository)

### Techniques

(Explain how reference and current periods were compared.)

### Artifacts

(clickable link to artifacts/ folder and explain result files)

### Insights

(What changed? How do you know? How does this help make actionable decisions?)

## 6. Continuous Intelligence Pipeline

### Repository Link

(clickable link to your repository)

### Techniques

(Describe how signals and monitoring techniques were combined.)

### Artifacts

(clickable link to artifacts/ folder and explain result files)

### Assessment

(What does the pipeline say about the system state?)
