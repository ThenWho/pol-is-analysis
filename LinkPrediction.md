# Link prediction

[![hackmd-github-sync-badge](https://hackmd.io/8yvjIvm9TEyDSunVg1nSYQ/badge)](https://hackmd.io/8yvjIvm9TEyDSunVg1nSYQ)


## Generic method

Using participant-votes data, it is possible to predict future votes as follows:
* Use a tensor to store participant-votes data, one slice per positive/negative/pass votes.
* Use modified tensor decomposition such as CP to derive latent matrices, as follows:
    * When updating the elements of the latent matrices, evaluate their fitness using a weight matrix. The weight elements should be 
        * 1 when the observation is present in the same place in participant-votes data
        * 0 when the observation is missing (i.e. link to be predicted)
    * At the end of the update, the latent matrices would be optimized with respect to the missing observations.
* Recover the tensor from the latent matrices.
* The values in the missing observations contain the predicted links, if any.


*Code:* 
* Julia lang: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/thenwho/pol-is-link-prediction/blob/master/Julia\_LinkPrediction\_TensorFactorization_Vechgrad.ipynb)
* Python, with TensorLy: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ThenWho/pol-is-link-prediction/blob/main/Python_LinkPrediction_TensorFactorization_Vechgrad_optimized_lean.ipynb)


*Bibliography*:
* Gao, Sheng, Ludovic Denoyer, and Patrick Gallinari. "Link pattern prediction with tensor decomposition in multirelational networks." In 2011 IEEE Symposium on Computational Intelligence and Data Mining (CIDM), pp. 333-340. IEEE, 2011.


## Optimized element- and slice-wise updates

While the above method works, it updates the full latent matrices every time. This is computentionally expensive, when only some elements/row/columns of some slice are updated. 

For example, this is the case when a participant submits one new vote on some statement. This vote changes one element in one of the slices (positive/negative/pass), but might change future link predictions for that participant. We would like to have a way to make partial updates to the latent matrices, without recalculating them from scratch.

This is possible by implementing the SCED algorithm of Zhou *et al*, together with the generic method above.

*Bibliography*:
* Zhou, Shuo, Sarah M. Erfani, and James Bailey. “Sced: A general framework for sparse tensor decomposition with constraints and elementwise dynamic learning.” In 2017 IEEE International Conference on Data Mining (ICDM), pp. 675-684. IEEE, 2017.
* Zhou, Shuo. “On dynamic tensor decompositions.” PhD diss., 2019.

[\> home](https://hackmd.io/@ThenWho/PolisGraph)