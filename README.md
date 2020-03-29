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
broadcast station [VPRO](https://www.vpro.nl/). [VPRO](https://en.wikipedia.org/wiki/VPRO) has played a crucial part in Dutch design history with the guide being a focal point.

## Techniques used:
We use [StyleGAN](https://github.com/NVlabs/stylegan) for image genration, [SRFBN](https://github.com/Paper99/SRFBN_CVPR19) to create super-resolution covers and [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo) to create slow motion latent space walk videos.

### _[StyleGAN](https://github.com/NVlabs/stylegan)_
StyleGAN is a generative model which is capable of generating [realistic images of people](https://www.thispersondoesnotexist.com/), [characters](https://towardsdatascience.com/creating-new-scripts-with-stylegan-c16473a50fd0), and [more](https://medium.com/@jonathan_hui/gan-some-cool-applications-of-gans-4c9ecca35900). More information can be found here: [1](https://towardsdatascience.com/explained-a-style-based-generator-architecture-for-gans-generating-and-tuning-realistic-6cb2be0f431)

+ In this application, StyleGan was trained on a dataset of historic VPRO Covers, with an output size of 512x512. Since there are hardly any constant features across covers except for the logo, we expected output that is artistic rather than realistic. Here is a [PyTorch](https://github.com/rosinality/style-based-gan-pytorch) implementation of StyleGAN you can use to train your own model. Create your own dataset and follow the instructions to preprocess your data and create a generative model. 

### [Feedback Network for Image Super-Resolution](https://github.com/Paper99/SRFBN_CVPR19)
Feedback Network for Image Super-Resolution (SRFBN) and some post-processing was used to create super-resolution images of the StyleGAN output. SRFBN is an [image super-resolution](https://en.wikipedia.org/wiki/Super-resolution_imaging) feedback network (SRFBN) to refine low-level representations with high-level information. 

+ We applied SRFBN with a magnification of x4, followed by a resizing and resampling of the output (using [ImageMagick](https://imagemagick.org/index.php)) to create images of size 3366x3366 with 300dpi.

### [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo)
To better visualize the generative capabilities of the StyleGAN model, we performed a latent space walk to create videos that look like generated covers morphing into each other. To create more detailed latent space walks of the StyleGAN output, we used [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo) to create high resolution images from low-resolution StyleGAN output. Specifically, we used a [PyTorch](https://people.cs.umass.edu/~hzjiang/projects/superslomo/) implementation.

#### Animated GIF Examples of latent space walk:
![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/VPRO_Gids_Covers_slow_4000_crop_10.gif) ![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/VPRO_Gids_Covers_slow_8000_crop_10.gif) ![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/VPRO_Gids_Covers_slow_8000_crop_90.gif)
**Pictures**: Resolution-reduced animated GIF examples of latent space walks of the StyleGAN model.

#### High resolution video exampels of latent space walk:
TODO

# Docker
TODO

# Resources
Related material is available via the following links:

## StyleGAN:
+ [StyleGAN](https://github.com/NVlabs/stylegan)
+ Karras, Tero, Samuli Laine, and Timo Aila. ["A Style-Based Generator Architecture for Generative Adversarial Networks"](https://arxiv.org/abs/1812.04948) In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 4401-4410. 2019.

## Feedback Network for Image Super-Resolution
+ Code: [Feedback Network for Image Super-Resolution](https://github.com/Paper99/SRFBN_CVPR19)
+ Paper: Li, Zhen, Jinglei Yang, Zheng Liu, Xiaomin Yang, Gwanggil Jeon, and Wei Wu. ["Feedback network for image super-resolution."](https://arxiv.org/abs/1903.09814)  In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 3867-3876. 2019.

## Super-SloMo
+ Code: https://github.com/avinashpaliwal/Super-SloMo
+ Paper: Jiang, Huaizu, Deqing Sun, Varun Jampani, Ming-Hsuan Yang, Erik Learned-Miller, and Jan Kautz. ["Super SloMo: High Quality Estimation of Multiple Intermediate Frames for Video Interpolation"](https://arxiv.org/abs/1712.00080) In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 9000-9008. 2018.
