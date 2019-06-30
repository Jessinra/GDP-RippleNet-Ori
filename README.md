# GDP-RippleNet

***Last edit : 30 June 2019***

Recommender system using [RippleNet](http://users.cecs.anu.edu.au/~akmenon/papers/autorec/autorec-paper.pdf), using original MovieLens-1M dataset.

This repository is the implementation of RippleNet ([arXiv](https://arxiv.org/abs/1803.03467)):
> RippleNet: Propagating User Preferences on the Knowledge Graph for Recommender Systems  
Hongwei Wang, Fuzheng Zhang, Jialin Wang, Miao Zhao, Wenjie Li, Xing Xie, Minyi Guo  
The 27th ACM International Conference on Information and Knowledge Management (CIKM 2018)

![](https://github.com/hwwang55/RippleNet/blob/master/framework.jpg)

RippleNet is a deep end-to-end model that naturally incorporates the knowledge graph into recommender systems.
Ripple Network overcomes the limitations of existing embedding-based and path-based KG-aware recommendation methods by introducing preference propagation, which automatically propagates users' potential preferences and explores their hierarchical interests in the KG.

A PyTorch re-implementation of RippleNet by Qibin Chen et al. is [here](https://github.com/qibinc/RippleNet-PyTorch).

# Domain of problems
*Given a user and an item, predict how likely the user will interact with the item*

# Contents
- data : contains dataset to use in training
    - book (not used)
    - movie : original dataset ML-1M
- **log** : contains training result stored in single folder named after training timestamp.
- **test** : contains jupyter notebook used in testing the trained models
- src : implementations of RippleNet.

### Note
    *italic* means this folder is ommited from git, but necessary if you need to run experiments
    **bold** means this folder has it's own README, check it for detailed information :)

# Preparing 
## Installing dependencies 

    pip3 install -r requirements.txt

## How to prepare data
simply run :
~~~
python3 src/preprocess.py
~~~

# How to run
~~~
python3 src/main.py
~~~

# Training
## How to change hyper parameter
There are several ways to do this :
1. Open `src/main.py` and change the args parser default value
2. run `src/main.py` with arguments required.

# Testing / Evaluation
## How to check training result
1. Find the training result folder inside `/log` (find the latest), copy the folder name.
2. Create copy of latest jupyter notebook inside `/test` folder.
3. Rename folder to match a folder in `/log` (for traceability purpose).
4. Replace `TESTING_CODE` at the top of the notebook.
5. Run the notebook

# Final result
| Metric             | Value       |
|--------------------|-------------|
| Average prec@10    | +- 0.12     |
| Diversity@10 n=10  | 0.50 - 0.60 |
| Evaluated on       | 500 users   |

# Other findings
Looking from the result of Ripplenet-1M, the usage of KG might turn out to be quite promising, especially to improve the diversity of suggestion.

# Author
- Jessin Donnyson - jessinra@gmail.com

# Contributors
- Benedict Tobias Henokh Wahyudi - tobi8800@gmail.com
- Michael Julio - michael.julio@gdplabs.id
- Fallon Candra - fallon.candra@gdplabs.id