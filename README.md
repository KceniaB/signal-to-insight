# wearable-activity-heart-rate-analysis
Exploratory analysis of wearable physiological signals to study relationships between activity, heart rate, and sleep dynamics.


# Wearable Activity and Heart Rate Analysis

This project explores relationships between activity patterns, heart rate, and sleep dynamics using wearable sensor data. 

The goal is to investigate how daily activity influences physiological signals during sleep and across multiple days. 

## Dataset
MMASH – Multilevel Monitoring of Activity and Sleep in Healthy People

[https://physionet.org/content/mmash/1.0.0/
](https://physionet.org/content/mmash/1.0.0/)

The dataset contains:

- heart rate (RR intervals)
- accelerometer signals
- sleep diaries
- activity measures
- multi-day recordings from wearable sensors

## Project goals

1. Detect activity vs inactivity from wearable motion signals
2. Explore behavioral state clustering using unsupervised learning
3. Compare unsupervised vs supervised activity classification
4. Investigate relationships between activity load and heart rate during sleep
5. Explore multi-day physiological dynamics

## Planned analysis pipeline

1. Data exploration and visualization
2. Activity detection from accelerometer signals
3. Behavioral state clustering
4. Activity classification
5. Sleep heart rate analysis
6. Multi-day activity–physiology relationships

## Repository structure

notebooks/ – analysis notebooks  
src/ – helper functions  
figures/ – generated plots  
data/ – dataset (not included in repo)

## Tools

- Python
- pandas
- numpy
- scikit-learn
- matplotlib/seaborn

