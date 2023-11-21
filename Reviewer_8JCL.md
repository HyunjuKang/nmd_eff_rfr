We sincerely appreciate your valuable feedback for reviewing this paper. For the potential concerns you bring up, we would like to address them as follows.

### W1 \& Q1: Addressing scalability 

Thank you for raising this important point. Scalability is an important factor to be considered particularly in real applications on very large graphs. As a matter of time complexity, UNR-Explainer has a time complexity of $O(t \cdot n \cdot |V|)$, where $t$ is the number of iterations, $n$ is the number of nodes in the search tree, and $|V|$ is the number of nodes in the input graph. In the worst case, if $n$ approaches $|V|$, the complexity could become approximately $O({|V|}^2)$. To circumvent this situation, there are two strategies: establishing stopping criteria and setting an upper bound for $n$. Firstly, $t$ is set to 1,000 as a stopping criterion, or the traversal is stopped when a case meeting $Importance = 1.0$ is found. Secondly, the number of nodes in the traversal graph is limited to a constant value; in this paper, we set it to 20. Moreover, in every iteration, we sample at most 3 nodes for the expansion step, which helps avoid the exponential expansion of $n$. For these reasons, the time complexity of UNR-Explainer is approximately $O(|V|)$, because both $t$ and $n$ could be regarded as constants. While most gradient-based methods (e.g., PGExplainer [1]) have the time complexity of $O(|E|)$, where $|E|$ is the number of edges in the input graph, the complexity of UNR-Explainer could be more efficient than these methods, especially when the input graph is dense.

**Reference**

[1] Luo, Dongsheng, Wei Cheng, Dongkuan Xu, Wenchao Yu, Bo Zong, Haifeng Chen, and Xiang Zhang. "Parameterized explainer for graph neural network." Advances in neural information processing systems 33 (2020): 19620-19631.

### W2: Providing overview of UNR-Explainer

Thank you for your suggestion. We attached the figure describing an overview of UNR-Explainer in a revised version of our paper and attached [link](https://anonymous.4open.science/r/unr0929/overview.jpg).


### Q2: Addressing sensitivity of perturbation effect
Thanks for your valuable question. As demonstrated in our additional experiments, the sensitivity of the $Importance$ measure in UNR-Explainer varies with different perturbation rates (details available at this [link](https://anonymous.4open.science/r/unr0929/perturbation_param.jpg). Specifically, when the perturbation parameter lies between 0.0 and 0.3, there is a gradual decline in $Importance$ observed on the Cora and CiteSeer datasets. However, for perturbation parameters exceeding 0.4 — implying that $40\%$ or more of messages that ought to be weakened are retained — the effectiveness of the perturbation is reduced, leading to a lower $Importance$.


### Q3-1: Addressing analysis of explanations by models as GraphSAGE vs DGI
Thanks for brining up this question. In general, UNR-Explainer yields explanations of varying sizes when used with different node representation models such as GraphSAGE and DGI. Specifically, explanations under the GraphSAGE model average 4.5 nodes and 3.8 edges, while those under DGI average 3.9 nodes and 3.1 edges. Typically, GraphSAGE-generated explanations include more distant nodes and a greater number of connections in the input graph compared to DGI. We have provided visualizations of these explanations via this [link](https://anonymous.4open.science/r/unr0929/cora-gs-dgi.jpg). In Case 1, the explanations under GraphSAGE and DGI are common, while in Case 2, although the overall structure of the explanations is similar, the GraphSAGE explanation includes an additional node at a 2-hop distance from the target node. This trend is even more pronounced in Case 3. We hypothesize that this difference may be attributed to the methods used for defining positive and negative samples during training. GraphSAGE treats nodes near a target node on a fixed-length random walk as positive samples, as implemented in [pytorch-geometric](https://pytorch-geometric.readthedocs.io/en/latest/_modules/torch_geometric/loader/link_neighbor_loader.html#LinkNeighborLoader) with settings [10, 10]. Conversely, DGI employs a corruption function that randomly permutes node features while keeping the edge index constant to generate negative samples. This broader range of positive samples in GraphSAGE could influence UNR-Explainer to generate explanations that encompass more distant nodes and edges.


### Q3-2: Adapting UNR-Explainer to explain generative models 

Thank you for your insightful question. Graph Auto Encoders (GAE), such as VGAE [1] and S2GAE [2], are prominent in generation-based unsupervised and self-supervised learning on graphs. These models typically consist of two components: an encoder, which is a graph neural network producing latent representations, and a decoder, which reconstructs the input graph using these representations. The latent representation, containing implicit information, is crucial for downstream tasks like node and graph classification, where GAE models demonstrate superior performance. Hence, there is a significant demand for explaining these models in real-world applications.

UNR-Explainer can be adapted to explain the encoder of GAE-based models like VGAE and S2GAE. This compatibility arises mainly because UNR-Explainer provides node-level explanations, aligning well with the output of the node-level embedding by the encoders in these models. Moreover, UNR-Explainer's ability to provide explanations without relying on class labels makes it potentially suitable for self-supervised learning models.

However, adapting UNR-Explainer to GAE models involves defining explanations for generation-based GAEs and designing appropriate experimental settings, especially evaluation metrics. Additionally, the specific processes of each model must be considered. For instance, in VGAE [1], we need to control the randomness of the reparameterization trick to assess the perturbation effect accurately. In the case of S2GAE [2], which uses edge-masking and direction-aware graph masking, these perturbation methods may conflict with UNR-Explainer's perturbation process, necessitating additional adjustments. Moreover, since UNR-Explainer is designed to explain models with only an Encoder part, adapting it to generative models with a Decoder part would require further methodological considerations.

To our knowledge, explainability for generative models on graphs is one of the less explored areas in research. We are grateful for your question, as it highlights an exciting direction for our future research endeavors.

**Reference**

[1] Kipf, Thomas N., and Max Welling. "Variational graph auto-encoders." arXiv preprint arXiv:1611.07308 (2016).

[2] Tan, Qiaoyu, Ninghao Liu, Xiao Huang, Soo-Hyun Choi, Li Li, Rui Chen, and Xia Hu. "S2GAE: Self-Supervised Graph Autoencoders are Generalizable Learners with Graph Masking." In Proceedings of the Sixteenth ACM International Conference on Web Search and Data Mining, pp. 787-795. 2023.
