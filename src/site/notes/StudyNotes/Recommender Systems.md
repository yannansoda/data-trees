---
{"topic":"MachineLearning","dg-publish":true,"permalink":"/StudyNotes/Recommender Systems/","dgPassFrontmatter":true,"noteIcon":""}
---

# Types of Recommender Systems Algorithm

## Collaborative filtering algorithm
recommend items to you based on ratings of users who gave similar ratings as you.
- Collaborative does not need the features of the items to be given

### Limitations
- cold start problems:
	when you have a new item, there are few users have rated, or we have a new user that's rated very few items, the results of collaborative filtering for that item or for that user may not be very accurate. 
- side information not used:
	it doesn't give you a natural way to use side information or additional information about items or users.
## Content-based filtering algorithm 
recommend items to you based on the features of users and features of the items to find a good match. 
### Recommending from a large catalogue
- two-step procedures
	1. retrieval:
		- generate large list of plausible item candidates
		- combine retrieved items and remove duplicates
		> - A larger retrieval list gives the ranking system more options to choose from which should maintain or improve recommendations. 
		> - A larger retrieval list may take longer to process which may increase response time.
	2. ranking
		- take list retrieved and rank using learned model
		- display ranked items to user
## 

# Similarity Metrics
- The features of an item are basically transformed into vectors/matrixes, and similarity between them can be measured. 
- Similarity metrics are often used in content-based filtering.
- There are several types of similarity metrics

| Metrics Type | What is computed     | Often for which algorithm | Often for what data |
| ------------------ | ------------------------------------------ | ------------------------- | -------- |
| Cosine Similarity ([[StudyNotes/Distance Function#Cosine similarity\|Distance Function#Cosine similarity]])  | the cosine angle between the vectors                 | content-based filtering   | sparse and high-dimensional |
| Euclidian Distance ([[StudyNotes/Distance Function#Euclidian distance\|Distance Function#Euclidian distance]]) | the elementwise squared distance between two vectors | content-based filtering   | dense and low-dimensional   |
| Pearson correlation coefficient| coefficient of the two vectors             |collaborative filtering   |  dense and low-dimensional  |
| Dot Product        | cosine angle and magnitude of the vectors            | collaborative filtering   | dense and low-dimensional   |