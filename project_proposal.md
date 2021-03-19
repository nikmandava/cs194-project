# Project Proposal
#### Anjali Kantharuban & Nikhil Mandava

## Background

Reddit is a network of online communities, or subreddits, that users engage in. Each subreddit consists of posts and sets of comment threads. Reddit's unique community setup, primarily text based communication, and natural human interactions provides a wealth of useful data for analysis. Currently, there are many bots that operate on Reddit that fall under a variety of categories. Some are well received - those that answer questions with wikipedia articles or convert posts to haikus. Others, commonly referred to as "karma-farming" bots, are looked down upon and banned by communities. The main issue with the bots in this second group is that they are low quality; they steal comments and posts from previous iterations of the same interaction and don't contribute new content. This also makes them easy to find, since looking up the text they produce gives the exact post it was stolen from. Our goal in this project is to produce a reddit bot that responds to posts with comments that are unique and make logical sense. We are limiting the scope of our bot to make only top-level comments and judging its success on the number of upvotes it gets on each post.

## Model

We plan on building our model as an extension on GPT-2, trained on an entire Reddit corpus at first and then fine tuned by subreddit before deployment. The purpose of the GPT-2 base is to encourage fluency from the beginning. We will follow a process similar to that created for DialoGPT with a modified input and evaluation metric due to having a slightly different goal [1]. Our input will be the original post rather than upstream comments. In order to have our input be manageable, we are restricting the scope of our bot to text post only subreddits. The model structure and output should remain relatively similar to that proposed in the aforementioned paper.

## Evaluation

Our goal is to generate comments that procure maximum upvotes. In order to train for this, we will be using a semantic similarity comparison against true comments, weighed by their cumulative upvote count. This will reward the model for choosing to respond similarly to a highly voted comment and punish it for responding similarly to a downvoted comment. Another option that will be explored is to use a model designed to predict comment performance as a scoring agent [2]. In order to do that, we will train on previous Reddit posts and comments to predict the number of upvotes a comment will receive given time posted, the post title, and the actual text of both the post and comment. Afterwards, we will actually deploy our bot to generate and submit comments on the Reddit posts of a few carefully chosen subreddits to see how they do in real life. We will also attempt to avoid overfitting, through implementing a response echo index metric which will heavily discourage repeating phrases directly [3].

## Resources

[1] https://arxiv.org/abs/1911.00536

[2] https://arxiv.org/abs/1606.03667

[3] https://arxiv.org/abs/1811.01063
