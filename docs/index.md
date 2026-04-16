# Continuous Intelligence

This site provides documentation for this project.
Use the navigation to explore module-specific materials.

## How-To Guide

Many instructions are common to all our projects.

See
[⭐ **Workflow: Apply Example**](https://denisecase.github.io/pro-analytics-02/workflow-b-apply-example-project/)
to get these projects running on your machine.

## Project Documentation Pages (docs/)

- **Home** - this documentation landing page
- **Project Instructions** - instructions specific to this module
- **Glossary** - project terms and concepts

## Custom Project

### Dataset
The dataset used in the custom project comes from transit data.
There are two columns in the dataset with 35 rows

The columns are:

- day: when the observation occurred

- rides: number of transit rides taken

### Signals
A total of 5 signals were made for the assessment of the transit dataset.

Two basic statistics were calculated: average rides and rides standard deviation.

These let us get some insight on the basics of the data.

A rolling statistic was also calculated: average rolling z score.

This signal was made to help determine the state of the transit system.

The final two signals made share the state of the transit system: transit_state & status_reason.

The state can be either degraded or stable and the reason can either be normal or high z score.

### Experiments
I changed the dataset from system monitoring to transit for more of a challenge.

Since there's an upward trend of rides, I decided against using the basic z-score and went with the rolling z-score instead.

The original data used error rates and average latency to determine the health of the system.

Those aren't found in this dataset so the rolling z-score was what determined the state of the transit system.

### Results
The average rides came out to be 6,240 with a standard deviation of 1,214.14.

The average rolling z score was 1.14, meaning that the transit state was stable as everything was normal.

### Interpretation
Even with the upward trend in rides, the transit system is doing very well.

A rolling z-score of 3 would be an extreme anomaly while a 2 would be a normal anomaly.

Considering that this data came back with zero anomalies and a rolling z-score of 1.14, this is more proof of how stable the transit system is.

## Additional Resources

- [Suggested Datasets](https://denisecase.github.io/pro-analytics-02/reference/datasets/cintel/)
