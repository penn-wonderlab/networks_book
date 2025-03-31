# Inferential Network Analysis


## Readings

- Robins, G., Pattison, P., Kalish, Y., & Lusher, D. (2007). An introduction to exponential random graph (p*) models for social networks. Social Networks, 29(2), 173–191. https://doi.org/10.1016/j.socnet.2006.08.002
- Del Valle, M. E., Gruzd, A., Kumar, P., & Gilbert, S. (2020). Learning in the Wild: Understanding Networked Ties in Reddit. In Mobility, Data and Learner Agency in Networked Learning (pp. 51–68). Springer, Cham. https://doi.org/10.1007/978-3-030-36911-8_4

## Why Inferential Network Analysis?

**Inferential network analysis** is a powerful approach for drawing conclusions about the processes that generate network ties. Instead of simply describing an observed network through measures like centrality or clustering, inferential methods ask _why_ certain ties occur and how local structures can help explain global patterns. When properly applied, these methods can demonstrate whether, for instance, the network shows more reciprocity or clustering (triangles) than we would anticipate by chance, and they can compare multiple theories of tie formation.

Several types of inferential network analysis methods exist. **Latent space modeling** places nodes in a high- or low-dimensional space and presumes that ties are more likely between nodes that lie close to each other. This approach is often effective in uncovering hidden groups or communities when node-level attributes do not fully capture the factors driving tie formation. Other approaches, such as **Stochastic Blockmodels**, group nodes into blocks or clusters and estimate probabilities of edges within and between blocks. Still others, like **Stochastic Actor-Oriented Models** or **temporal ERGMs**, explicitly incorporate time and allow us to track evolving ties. Each framework combines statistical inference with structural theory, granting researchers a principled way to test hypotheses on how local interaction rules shape overall connectivity.

## Exponential Random Graph Models (ERGMs)

**Exponential Random Graph Models (ERGMs)** is a popular method in inferential network analysis. They conceptualize each possible tie as a random variable, guided by hypothesized local configurations or node attributes. For example, researchers may posit that if actor A is connected to actor B, and actor B is connected to actor C, then there is an increased likelihood of a tie between A and C (transitivity). In addition to these endogenous tendencies, exogenous actor covariates (like gender or organizational role) can also be incorporated.

Robins et al. (2007) provide detailed introduction to ERGMs. They explain how these models leverage local dependence assumptions, describes typical network configurations (such as reciprocated dyads or star configurations), and outlines parameter interpretation. 

Del Valle et al. (2020) provide a concrete example, by examining how certain network effects shaped the creation of learning-oriented conversations in online communities.

### Running ERGM analysis

In practice, fitting an ERGM involves defining the network data (such as a binary adjacency matrix for all nodes) and selecting terms that represent your hypotheses. If the research question involves reciprocity, then you include a mutual dyad parameter; if triadic closure is important, you include a triangle parameter. You can also include node-level covariates if you believe that certain attributes—like age, occupation, or forum moderator status—affect tie formation.

After specifying the model, researchers typically use Markov chain Monte Carlo maximum likelihood procedures to estimate parameters. This step requires software that can handle the inherent complexity of ERGMs, such as the `ergm` package in the `statnet` suite for R. During estimation, one must watch for degeneracy, which occurs when a model places most of its probability mass on either an empty or a complete network. It is also essential to validate the model by simulating networks from the fitted parameters and comparing their global characteristics (like degree distribution or clustering) to those of the observed data.

Interpreting and refining the model is a natural final stage. Large, positive parameter estimates for reciprocity or triangles suggest that such local structures are more frequent than chance would imply. Negative parameters would mean the opposite. Researchers often iterate by adding or removing parameters, or by refining how attributes are coded, until the model fits well and aligns with theoretical expectations.

This course does not require students to fit ERGMs. However, you are encouraged to seek additional resources if this topic is of interest to you.

