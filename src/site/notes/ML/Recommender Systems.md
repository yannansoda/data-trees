---
{"dg-publish":true,"permalink":"/ml/recommender-systems/"}
---


# Collaborative filtering algorithm:
recommend items to you based on ratings of users who gave similar ratings as you.

### Limitations
- cold start problems:
	when you have a new item, there are few users have rated, or we have a new user that's rated very few items, the results of collaborative filtering for that item or for that user may not be very accurate. 
- side information not used:
	it doesn't give you a natural way to use side information or additional information about items or users.

# Content-based filtering algorithm 
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
