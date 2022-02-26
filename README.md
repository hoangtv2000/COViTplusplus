<h2 align="center"> COViTplusplus </h2>
**Abstract.** This work implements One-shot Neural Architecture Search (NAS) to search the best configuration of Pyramid Vision Transformer (PVT) model for COVIDx8A dataset. Specifically, our objective is to find a model which should satisfy the resource constraints: a number of parameters, FLOPs (G) while also guaranteeing performance metrics: accuracy on test set and COVID-19 sensitivity. In order to tackle these challenges, we construct the large search space covering the changeable dimensions of Multi-head Attention vectors (*Q-K-V*); changeable pooling dimensions to perform Linear Spatial Reduction Attention; MLP ratios and amount of Transformer Encoders of each Stage. We initially train the supernet (the model can cover all scenarios from the search spacce) by Knowledge Distillation stragedy with the help of [Exp.5 teacher model](https://github.com/hoangtv2000/COViT#the-exp5-model). Benefitting the weight-entanglement training stragedy of Vision Transformers, the well-trained supernet can allow a thousand of its subnets to be well-trained without having to train from scratch. Our best subnet achieves % top-1 accuracy on COVIDx8A dataset, with M parameters and GFLOPs.

### Super model base configuration

|QKV Embed. dims     |  MLP ratios       | Depths        | Sample pool. dims |
| :----------------: | :---------------: | :-----------: | :---------------: |
| [8, 16, 40, 64]    | [8, 8, 8, 4]      | [2, 2, 2, 2]  | 7                 |
| [16, 32, 80, 128]  | [8, 8, 4, 4]      | [2, 2, 4, 2]  | 15                |
| [24, 48, 120, 192] |                   | [2, 3, 6, 2]  | 31                |
| [32, 64, 160, 256] |                   | [2, 4, 8, 2]  |                   |
|                    |                   | [3, 4, 12, 2] |                   |

+ Params range: 2.5 - 9.1 M
+ Flops range: 6.3 - 10.6 G 

### Test accuracy, COVID-19 Sensitivity vs. Params, GFLOPs    
<p align="center">
	<img src="https://user-images.githubusercontent.com/58163069/155849018-24e637f0-5145-459b-9205-bf79b979e66e.png" alt="photo not available" width="80%" height="80%">
	<br>
	<em>Top-1 accuracy and COVID-19 sensitivity on COVIDx8A dataset and top 1000 sampled high-performing architectures from the supernet with weight inherited from the supernet.</em>
</p>

