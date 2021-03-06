# torch_variational
Pytorch implementation and Wapper classes for torch.nn.modules layers of:<br>
- Flipout[1]<br>
- Local Reparameterization Trick[2]<br>

## Dependencies
Pytorch >= 1.0.0

## Available modules
Variationalizers - Wrapper for nn.module class(Supports [Lazy|Standard][Linear|Convolutional] layers.)
- Flipout Wrapper<br>
- Local Reparameterization Wrapper<br>

Stand-alone Flipout layers:
- Conv2d_flipout<br>
- Linear_flipout<br>

## Usage

Example usage for wrapper classes:
```
import pytorch_flipout.Variational
layer = flipout(nn.Linear(in_features = 10, out_features = 10, bias = True))
```

Example usage for Stand-alone Flipout layers:
```
import pytorch_flipout.flipout
layer = flipout.Linear_flipout(in_features = 10, out_features = 10, bias = True)
output, kld = layer(torch.randn(1, 10))
```

## Derivations
```
$$
q(w_{ij})=N(w_{ij}|\mu_{ij}, \mu_{ij}^2\sigma_{ij}^2) \\
a_{ij} = \sum_{i} x_i w_{ij} \\
q(a_{ij}) = N(a_{ij}|\sum_{i} x_i w_{ij}, \sum_{i} x_i^2 w_{ij}^2)
$$
```

## References
```
[1] @inproceedings{DBLP:conf/iclr/WenVBTG18,
  author    = {Yeming Wen, Paul Vicol, Jimmy Ba, Dustin Tran, Roger B. Grosse},
  title     = {Flipout: Efficient Pseudo-Independent Weight Perturbations on Mini-Batches},
  booktitle = {6th International Conference on Learning Representations, {ICLR} 2018,
               Vancouver, BC, Canada, April 30 - May 3, 2018, Conference Track Proceedings},
  year      = {2018},
  url       = {https://openreview.net/forum?id=rJNpifWAb}
}
[2] @inproceedings{NIPS2015_bc731692,
 author = {Kingma, Durk P and Salimans, Tim and Welling, Max},
 title = {Variational Dropout and the Local Reparameterization Trick},
 booktitle = {Advances in Neural Information Processing Systems},
 volume = {28},
 year = {2015}
 url = {https://proceedings.neurips.cc/paper/2015/file/bc7316929fe1545bf0b98d114ee3ecb8-Paper.pdf},
}
```
