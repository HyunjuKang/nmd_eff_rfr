We sincerely appreciate your valuable feedback for reviewing this paper. For the potential concerns you bring up, we would like to address them as follows.

### W1 \& Q2: Clarity of disscusion

Thank you for your constructive comment. In the BA-Shape dataset, there are 80 house-structured motifs, each comprising 5 nodes, which are considered the correct answers. Only a few edges in these motifs are connected to the base BA graph. In our experiments, we focused on evaluating the performance of explanation generation for nodes within these house motifs. In such cases, when employing 1hop-2N and 1hop-3N for searching explanations, the precision tends to be high. This is due to the increased probability that the explanation will include another node from the house-structured motif, thereby aligning with the ground truth. Similarly, for other synthetic datasets constructed in the same manner, 1hop-2N and 1hop-3N exhibit high precision but low recall.

### W2 \& Q1: More discussion of choosing $k$

Thank you for your valuable question. In this paper, $k=5$ was chosen as a hyper-parameter because it performed well on average across evaluation measures such as importance, fidelity, and validity. However, we acknowledge that practitioners might select different values for $k$ depending on the desired level of interpretation. Specifically, $k$ is closely associated with the detail of the generated explanation and the number of hops, so its selection may vary based on the domain expert's judgment. For instance, in a social network analysis, a $k$  value close to the average node degree may be suitable for explanations focusing on immediate connections, such as close friends. Conversely, for understanding important local clusters, a higher $k$ might be more appropriate. This decision can be informed by domain knowledge.

