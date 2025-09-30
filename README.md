# Tag-Jump Recommender

This project was developed individually as part of the Advanced Data Analytics course at KU Leuven. I designed and implemented a recommender system that takes a different approach to game discovery. While most recommenders suggest similar games to what users already play, my goal was to break the filter bubble and encourage exploration of entirely new genres.

I built the Tag-Jump Recommender, a system that uses community-generated tags as the foundation for recommendations. Instead of only suggesting what is already familiar, the system identifies “jump tags” — tags that are common in a user’s community cluster but absent from the user’s personal top preferences. These jump tags act as bridges to new genres, allowing the system to recommend games that feel fresh while still being relevant.

The project began with data stored in a graph database (Memgraph), representing relationships between users, games, and tags. After overcoming challenges in data preparation, I exported user–app and app–tag relationships and merged them into user–tag frequency matrices. These matrices became the backbone of the analysis.

I applied unsupervised learning techniques to cluster users based on their tag preferences. After experimenting with KMeans and DBSCAN, I settled on MiniBatchKMeans, which scaled well to the large dataset and produced more distinctive clusters once the most generic tags like “Action” or “Singleplayer” were removed. To validate the clusters, I used PCA visualization, which showed clearly separated groups of users.

From there, I derived jump tags by comparing each user’s top tags with their cluster’s top tags, selecting those that did not overlap. For each jump tag, I identified the most popular games within the cluster that the user did not yet own. The result was a personalized list of ten recommended games per user, each grounded in community preferences but pointing toward unexplored directions.

The implementation was carried out in Python, using networkx and matplotlib for visualizations and scikit-learn for clustering. Beyond the technical aspects, the project emphasized the importance of designing recommendation algorithms that do more than reinforce existing habits. By combining graph analytics, clustering, and creative use of tags, I was able to show how recommender systems can promote serendipity and discovery.

For reproducibility, the executable Python notebook/script is included in this repository. However, the original dataset files are not provided here due to their large size. I added this project to GitHub afterwards to showcase it in my portfolio.
