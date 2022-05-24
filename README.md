# LinkPrediction
Prediction of link in email graph dataset

This repository is inspired by https://github.com/VHRanger/nodevectors

Dataset
Link: http://snap.stanford.edu/data/email-Eu-core.html
A significant European research institution's email data was used to create the network. The developers of the dataset anonymized every incoming and outgoing email between members of the research organization. If person u sent at least one email to person v, there is an edge (u, v) in the network. The e-mails solely reflect communication between members of the institution (the core), and the dataset does not include incoming or outgoing communications from the rest of the world.

The dataset additionally includes the nodes' "true" community memberships. Each employee is assigned to one of the institute's 42 departments. This network is the "heart" of the email-EuAll network, which also includes ties between institution members and others outside the institution (although the node IDs are not the same).

Total number of Nodes:   1005
Total number of Edges:    25571
Total number of departments: 42


This repository focuses on the below:
1. Implementation of creating node features in the graph using node2vec
2. Link prediction using the created features


Node2vec uses SGD to optimize a graph-based objective function inspired by previous work on natural language processing. In a d-dimensional feature space, this technique produces feature representations that optimize the chance of retaining network neighborhoods of nodes. It generates (sample) network neighborhoods for nodes using a 2nd order random walk technique.

Node2vec may learn representations that arrange nodes based on their network roles and/or communities they belong to by selecting a suitable concept of a neighborhood. It accomplishes this by creating a family of biased random walks that effectively explore several neighborhoods of a given node. In contrast to previous work, the resultant method is flexible, providing us control over the search space via customizable parameters. As a result, this technique generalizes previous work and can simulate the whole spectrum of network equivalences. The search strategy's parameters have an obvious meaning and bias the walk toward alternative network investigation tactics. These parameters can likewise be learned semisupervised using a minimal percentage of labeled data.

Experimentation setting:
We will use different values of p, and q and generate 32 dimension node embeddings. To evaluate the quality of the embeddings generated, we will train three models (logistic regression, LightGBM, and Random Forest) to see how it performs on the Link prediction task. For the Link prediction task, we will set 20% of the data as a test dataset. We have run the model for 10X10 = 100 combinations of p and q for 3 different models. Hence, we obtain 300 results on the test dataset.

Result file: result_df_32.csv
