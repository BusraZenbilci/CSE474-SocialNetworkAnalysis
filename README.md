# TwiBot-20 Bot Detection Project

This project focuses on detecting bot accounts on Twitter using the TwiBot-20 dataset. We explore two different approaches: a Graph Neural Network (GNN) model and a Random Forest classifier. 

### Affiliated Paper
The affiliated paper of this repository, 'TwiBot-20: A Comprehensive Twitter Bot Detection Benchmark', is accepted at CIKM 2021.

```
@article{Feng2021TwiBot20AC,
  title={TwiBot-20: A Comprehensive Twitter Bot Detection Benchmark},
  author={Shangbin Feng and Herun Wan and Ningnan Wang and Jundong Li and Minnan Luo},
  journal={Proceedings of the 30th ACM International Conference on Information \& Knowledge Management},
  year={2021}
}
```

## Dataset

The TwiBot-20 dataset is a comprehensive Twitter bot detection benchmark dataset. It includes a variety of features extracted from user profiles, tweets, and network information.

### Features

1. **User Profile Features:**
    - `followers_count`: Number of followers.
    - `friends_count`: Number of friends.
    - `statuses_count`: Number of statuses.
    - `verified`: Whether the account is verified.
    - `account_age_days`: Age of the account in days.
    - `description_length`: Length of the profile description.
    - `has_url`: Whether the profile has a URL.
    - `has_profile_image`: Whether the profile has an image.
    - `has_background_image`: Whether the profile has a background image.
    - `tweet_count`: Number of tweets.
    - `avg_tweet_length`: Average length of tweets.
    - `avg_sentiment`: Average sentiment of tweets.

2. **TF-IDF Features:**
    - Extracted from the text of the tweets to represent the content.

3. **Graph Features:**
    - Network relationships among users (followers).

## Models

### Graph Neural Network (GNN)

We utilize a GNN to leverage the relational information between Twitter users. The GNN is implemented using PyTorch Geometric.

#### GNN Model Architecture

- **Layer 1:** GCNConv (Input: Number of features, Output: 64)
- **Activation:** ReLU
- **Layer 2:** GCNConv (Input: 64, Output: 32)
- **Activation:** ReLU
- **Layer 3:** GCNConv (Input: 32, Output: 2)

#### Training and Evaluation

The model is trained for 200 epochs using the Adam optimizer. The loss function is negative log likelihood loss. Evaluation metrics include precision, recall, and f1-score for both training and test sets.

### Random Forest Classifier

We also implemented a Random Forest classifier to compare with the GNN model. This classifier uses the same set of features but without the relational graph information.

#### Training and Evaluation

The model is evaluated on both training and test sets using precision, recall, and f1-score metrics.

## Results

The GNN and Random Forest models are compared based on their performance on the test set. The evaluation metrics include precision, recall, f1-score, and accuracy.

### GNN Model Performance

![image](https://github.com/BusraZenbilci/CSE474-SocialNetworkAnalysis/assets/88310614/6e6daa8c-5002-4abd-8643-f715533edee0)


### Random Forest Model Performance

![image](https://github.com/BusraZenbilci/CSE474-SocialNetworkAnalysis/assets/88310614/64a211a2-2bcb-4f22-a411-222cc78e53bb)



## Conclusion

The GNN model shows a more nuanced understanding of the relational data in the TwiBot-20 dataset. While the Random Forest model demonstrates higher accuracy on the test set, it is evident that the GNN model is better suited for this task because it takes into account the network structure of the data. Each user is represented as a node, and the connections between users (edges) are effectively utilized by the GNN to improve bot detection.

This relational aspect is crucial in social network analysis, where the interactions between users can provide significant insights into detecting bots. Although the Random Forest model excels in utilizing the provided features, the GNN's ability to incorporate the relational data makes it a more appropriate choice for this dataset. Future work could involve enhancing the GNN model with additional features or more complex architectures to further improve performance.







