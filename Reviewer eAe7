We sincerely appreciate your valuable feedback for reviewing this paper. For the potential concerns you bring up, we would like to address them as follows.

**W1: Novelty**
We acknowledge that our method is not the first to implement Monte Carlo Tree Search (MCTS) in the graph XAI (Explainable Artificial Intelligence) domain. Prior works, such as RationaleRL [1] and SubgraphX [2], have utilized MCTS in their problem settings, each with a reward function tailored to their specific objectives. However, applying existing MCTS frameworks directly to unsupervised node learning models is challenging. The difficulty lies in defining suitable rewards and managing the increased uncertainty in exploring the graph space.

To mitigate the challenges, we propose a new procedure that is different from the existing MCTS framework with respect to five key aspects. The distinctions between our model and SubgraphX are summarized in the table below.
First, our $Importance$ function shown in Equation (1) of our main text quantifies the change of top-k neighbors in the embedding space after perturbation, bringing up the benefits of recognizing the significant influence of important subgraph $G_s$ in related downstream tasks. Thus, our contribution not only relies on developing the proper design of MCTS for counterfactual explanations but also sheds light on explaining unsupervised node representation learning. For clarification, we describe the difference between SubgraphX and UNR-Explainer regarding to the design of MCTS as below:

| Design criteria        | SubgraphX          |   UNR-Explainer                |
|------------------------|--------------------|--------------------------------|
| Target model           | supervised models  | unsupervised models            |
| Reward function        | Shapley value      | Importance function in Eq. (1) |
| Action                 | to prune           | to add                         |
| Selection              | argmax             | random walk with restart       |
| Expansion              | without sampling   | with sampling                  |
| Action value           | mean               | max                            |
