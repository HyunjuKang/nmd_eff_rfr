We sincerely appreciate your valuable feedback for reviewing this paper. For the potential concerns you bring up, we would like to address them as follows.

### W1 \& Q1: Improving discussions

Thank you for your constructive comment. 
In our experiments, Baseline 1hop-3N demonstrated the highest $Precision$ on BA-Shapes and Tree-Cycles, 
while 1hop-2N showed similar performance on Tree-Grids. $Precision$ indicates the fraction of the ground truth edges among the generated explanations
This suggests that connections within a 1-hop range in the graph are highly likely to be part of important subgraphs or ground truth. The reason behind this is that GNNs such as GraphSAGE rely on propagating information between neighboring nodes to update node representations. Since nodes within 1-hop are direct passage, the diminished propagation effect is likely to be more significant than distant neighboring nodes. In general, $Precision$ tends to be higher for smaller subgraphs so that such compact sizes of subgraphs as 1hop-3N and 1hop-2N easily obtain the highest $Precision$. Thus, $Recall$ which indicates the fraction of the generated explanations among ground truth should be considered to measure how explanations describe ground truth closely. However, both 1hop-2N and 1hop-3N exhibited lower $Recall$ compared to UNR-Explainer, indicating that these baselines may miss covering the ground truth due to their limited exploration of distant but significant edges.

### W2: Addressing efficiency

Thank you for raising the important point. As you mentioned, the total time complexity of UNR-Explainer is $O(t \cdot n \cdot |V|)$ in the worst case. There are several ways to escape the worst case in our MCTS. First, $t$ is limited to prevent an infinite loop when $Importance$ does not achieve 1.0. Secondly, $n$ as the number of nodes in the search tree is also constrained because the child nodes are sampled in the Expansion step, described in section 4.2 in our paper. It potentially prevents exhausted cost for exploration especially when the input is extremely dense. Last, $|V|$ are not considered in all of the nodes in the input graph, but in relative close-hop nodes. In practice, the time complexity of UNR should be linear. Additionally, we tailor the design of MCTS carefully to reduce the computational time by $97.37\% [(4.64 - 176.3) ÷ 176.3] ×100$ and performance increased by $1.9\% ([(0.96 - 0.42) ÷ 0.942] ×100)$ compared to SubgraphX-1 in Table 4.

However, We agree that gradient-based methods have an advantage concerning efficiency. Nevertheless, we take a different approach with several advantages over gradient-based methods. First, the MCTS-based framework finds the exploratory subgraph which is connected. Gradient-based methods such as PG-Explainer utilize the connected loss term in its objective term to achieve connectedness. However, it often fails to generate connected subgraphs, since the additional regularization term does not guarantee generating connected subgraphs. Secondly, the objective function does not have to be differential compared to the gradient-based method. For example, SubgraphX utilizes the Shapley value to measure the importance of the reward function in MCTS-Framework. Our $Importance$ is a difference set of k-nearest neighbor nodes after perturbation. To utilize our $Importance$ in unsupervised settings, we choose the MCTS-based framework proper to explore the important subgraphs.

### W3: Enlarging fonts in Figures
Thanks for your valuable feedback. We revised all figures to improve the presentation of our paper.

We express our sincere gratitude for the opportunity to improve our paper based on your valuable feedback. The revisions made in response aim to comprehensively address the raised concerns.
