# VPRO Gids GAN Covers
> Generating VPRO Gids covers using [Generative Adversarial Networks](https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf)

![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/stitch_mx.png)
**Picture**: A selection of covers produced by the GAN generator trained on VPRO Gids covers.

This repository contains my [StyleGAN](https://github.com/NVlabs/stylegan)
application to VPRO Gids covers. I used [StyleGAN](https://github.com/NVlabs/stylegan), [SRFBN](https://github.com/Paper99/SRFBN_CVPR19) and [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo) to generate (moving) cover art for the [13th VPRO Gids edition of 2020](https://www.vprogids.nl/2020/14/editie.html).

## VPRO Gids
![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/stitch.png)
**Picture**: Example VPRO Gids covers from the training dataset.

[VPRO Gids](https://www.vprogids.nl/) is the television guide of Dutch
broadcast station VPRO. VPRO has played a crucial part in Dutch design history
with the guide being a focal point.

## Techniques used:
### [StyleGAN](https://github.com/NVlabs/stylegan)
StyleGan was trained on a dataset of VPRO Covers, with an output size of 512x512.

### [Feedback Network for Image Super-Resolution](https://github.com/Paper99/SRFBN_CVPR19)
Feedback Network for Image Super-Resolution (SRFBN) and some post-processing was used to create super-resolution images of size 3366x3366 with 300dpi. SRFBN is an [image super-resolution](https://en.wikipedia.org/wiki/Super-resolution_imaging) feedback network (SRFBN) to refine low-level representations with high-level information. 

### [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo)
To create more detailed latent space walks of the StyleGAN output, we used [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo). Specifically, we used a PyTorch implementation of "Super SloMo: High Quality Estimation of Multiple Intermediate Frames for Video Interpolation" by Jiang H., Sun D., Jampani V., Yang M., Learned-Miller E. and Kautz J. [[Project]](https://people.cs.umass.edu/~hzjiang/projects/superslomo/) [[Paper]](https://arxiv.org/abs/1712.00080)

## Example of latent space walk:
![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/VPRO_Gids_Covers_slow_4000_crop_10.gif) ![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/VPRO_Gids_Covers_slow_8000_crop_10.gif)

# Docker
Coming soon.

# Resources
Related material is available via the following links:

+ StyleGAN : https://github.com/NVlabs/stylegan (See also https://arxiv.org/abs/1812.04948)
+ Video: [TODO]
+ Code: https://github.com/hvkoops/VPRO-GAN-covers/src

