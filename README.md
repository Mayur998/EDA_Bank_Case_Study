# EDA_Bank_Case_Study
In this case study ,the company wants to understand the driving factors (or driver variables) behind loan default, i.e. the variables which are strong indicators of default.

Business Understanding : 
The loan providing companies find it hard to give loans to the people due to their insufficient or non-existent credit history. Because of that, some consumers use it as their advantage by becoming a defaulter. Suppose you work for a consumer finance company which specialises in lending various types of loans to urban customers. You have to use EDA to analyse the patterns present in the data. This will ensure that the applicants capable of repaying the loan are not rejected.
When the company receives a loan application, the company has to decide for loan approval based on the applicant’s profile.

Business Objectives :
The company wants to understand the driving factors (or driver variables) behind loan default, i.e. the variables which are strong indicators of default. The company can utilise this knowledge for its portfolio and risk assessment.

Download the dataset from the link given as below. 
https://drive.google.com/open?id=16RQztUqCfJOlbooHqYlJrp6Q7iL65uZB

from sklearn.datasets import make_moons
from sklearn.cluster import DBSCAN
from sklearn.metrics import silhouette_score
import numpy as np

# generate sample data
X, y = make_moons(n_samples=200, noise=0.05, random_state=0)

# create a range of min_samples values to test
min_samples_range = range(2, 10)

# create a range of epsilon values to test
eps_range = np.arange(0.1, 1.0, 0.1)

# initialize a list to store the silhouette scores
silhouette_scores = []

# loop through each min_samples value
for min_samples in min_samples_range:
    # loop through each epsilon value
    for eps in eps_range:
        # apply DBSCAN with the current values of min_samples and eps
        dbscan = DBSCAN(eps=eps, min_samples=min_samples)
        labels = dbscan.fit_predict(X)
        
        # calculate silhouette score
        score = silhouette_score(X, labels)
        
        # append the silhouette score and the values of min_samples and eps to the list
        silhouette_scores.append((score, min_samples, eps))

# sort the list by silhouette score in descending order
silhouette_scores.sort(key=lambda x: x[0], reverse=True)

# get the best values of min_samples and eps
best_min_samples, best_eps = silhouette_scores[0][1], silhouette_scores[0][2]

print("Best min_samples:", best_min_samples)
print("Best eps:", best_eps)
