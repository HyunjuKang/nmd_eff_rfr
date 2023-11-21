We sincerely appreciate your valuable feedback for reviewing this paper. For the potential concerns you bring up, we would like to address them as follows.

### W1 \& Q1: Improving discussions

Thank you for your constructive comment. In the BA-Shape dataset, there are 80 house-structured motifs, each comprising 5 nodes, which are considered the correct answers. Only a few edges in these motifs are connected to the base BA graph. In our experiments, we focused on evaluating the performance of explanation generation for nodes within these house motifs. In such cases, when employing 1hop-2N and 1hop-3N for searching explanations, the precision tends to be high. This is due to the increased probability that the explanation will include another node from the house-structured motif, thereby aligning with the ground truth. Similarly, for other synthetic datasets constructed in the same manner, 1hop-2N and 1hop-3N exhibit high precision but low recall.


### W2: Addressing efficiency

Thank you for raising this important point. UNR-Explainer has a time complexity of $O(t \cdot n \cdot |V|)$, where $t$ is the number of iterations, $n$ is the number of nodes in the search tree, and $|V|$ is the number of nodes in the input graph. In the worst case, if $n$ approaches $|V|$, the complexity could become approximately $O({|V|}^2)$. To circumvent this situation, there are two strategies: establishing stopping criteria and setting an upper bound for $n$. Firstly, $t$ is set to 1,000 as a stopping criterion, or the traversal is stopped when a case meeting $Importance = 1.0$ is found. Secondly, the number of nodes in the traversal graph is limited to a constant value; in this paper, we set it to 20. Moreover, in every iteration, we sample at most 3 nodes for the expansion step, which helps avoid the exponential expansion of $n$. For these reasons, the time complexity of UNR-Explainer is approximately $O(|V|)$, because both $t$ and $n$ could be regarded as constants. While most gradient-based methods (e.g., PGExplainer [1]) have the time complexity of $O(|E|)$, where $|E|$ is the number of edges in the input graph, the complexity of UNR-Explainer could be more efficient than these methods, especially when the input graph is dense.

In addition to addressing the time complexity issue, the MCTS-based framework finds the explanation subgraphs, which are mostly connected. In contrast, gradient-based methods such as PG-Explainer [1] incorporate a connected loss term in their objective term to achieve connectedness. Despite this, they often fail to consistently generate connected subgraphs, as the additional regularization term does not guarantee generating connected subgraphs.

**Reference**

[1] Luo, Dongsheng, Wei Cheng, Dongkuan Xu, Wenchao Yu, Bo Zong, Haifeng Chen, and Xiang Zhang. "Parameterized explainer for graph neural network." Advances in neural information processing systems 33 (2020): 19620-19631.

### W3: Enhancing presentations
Thanks for your valuable feedback. We revised all figures to improve the presentation of our paper.




### W3: Enlarging fonts in Figures
Thanks for your valuable feedback. We revised all figures to improve the presentation of our paper.

We express our sincere gratitude for the opportunity to improve our paper based on your valuable feedback. The revisions made in response aim to comprehensively address the raised concerns.
