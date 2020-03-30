# VPRO Gids GAN Covers
> Generating VPRO Gids covers using [Generative Adversarial Networks](https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf)

For inquiries, shoot me an [email](hvkoops@gmail.com) or contact me on [LinkedIn](https://www.linkedin.com/in/hendrik-vincent-koops-30927a93/).

![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/stitch_mx.png)
**Picture**: A selection of generated VPRO Gids covers.

This repository contains information about my [StyleGAN](https://github.com/NVlabs/stylegan)
application to VPRO Gids covers. I used [StyleGAN](https://github.com/NVlabs/stylegan), [SRFBN](https://github.com/Paper99/SRFBN_CVPR19) and [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo) to generate (moving) cover art for the [13th VPRO Gids edition of 2020](https://www.vprogids.nl/2020/14/editie.html).

## VPRO Gids
![](https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/stitch.png)
**Picture**: Example VPRO Gids covers from the training dataset.

[VPRO Gids](https://www.vprogids.nl/) is the weekly television guide of Dutch
broadcast station [VPRO](https://www.vpro.nl/). [VPRO](https://en.wikipedia.org/wiki/VPRO) has played a crucial part in Dutch design history with the guide being a focal point. I was asked to create an AI generated cover for the guide. This repository details the techniques I used to generate high-resolution VPRO Gids covers and latent space visualization videos.

## Method
[StyleGAN](https://github.com/NVlabs/stylegan) was used for image genration, [SRFBN](https://github.com/Paper99/SRFBN_CVPR19) to create super-resolution images from the StyleGAN output and [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo) to create slow motion versions of latent space walk videos.

### 1. _[StyleGAN](https://github.com/NVlabs/stylegan)_ 
StyleGAN is a generative model capable of generating [realistic images of people](https://www.thispersondoesnotexist.com/), [characters](https://towardsdatascience.com/creating-new-scripts-with-stylegan-c16473a50fd0), and [more](https://medium.com/@jonathan_hui/gan-some-cool-applications-of-gans-4c9ecca35900). More information can be found here: [1](https://towardsdatascience.com/explained-a-style-based-generator-architecture-for-gans-generating-and-tuning-realistic-6cb2be0f431)

In this application, StyleGAN was trained on a dataset of 9.5 years of historic VPRO covers. Because of training time constraints, a StyleGAN model with an output size of 512x512 was used. Since there are hardly any constant features across covers except for the logo, the expected output is artistic rather than realistic. Here is a [PyTorch](https://github.com/rosinality/style-based-gan-pytorch) implementation of StyleGAN you can use to train your own model. Create your own dataset and follow the instructions to preprocess your data and create a generative model. 

### 2. [Feedback Network for Image Super-Resolution](https://github.com/Paper99/SRFBN_CVPR19)
Feedback Network for Image Super-Resolution (SRFBN) and some post-processing was used to create super-resolution images of the low-resolution StyleGAN output. SRFBN is an [image super-resolution](https://en.wikipedia.org/wiki/Super-resolution_imaging) feedback network (SRFBN) to refine low-level representations with high-level information. SRFBN was applied to the StyleGAN output, with a magnification of x4, followed by a resizing and resampling of the output (using [ImageMagick](https://imagemagick.org/index.php)) to create images of size 285x215 mm with 300dpi.

### 3. [Super-SloMo](https://people.cs.umass.edu/~hzjiang/projects/superslomo/)
To better visualize the generative capabilities of the StyleGAN model, a [latent space walk](https://hackernoon.com/latent-space-visualization-deep-learning-bits-2-bd09a46920df) was created to create videos that look like generated covers morphing into each other. To create a more detailed latent space visalization of the StyleGAN output in the time domain, [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo) was used. Super-SloMo is an end-to-end convolutional neural network for variable-length multi-frame video interpolation, where the motion interpretation and occlusion reasoning are jointly modeled. For this project, Super-SloMo was applied to increase the number of frames by 4x. 
This [PyTorch](https://github.com/avinashpaliwal/Super-SloMo) implementation is useful for running your own experiments. 

#### Animated GIF Examples of latent space visualization:
<img src="https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/VPRO_Gids_Covers_slow_4000_crop_10.gif" width="288"> <img src="https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/VPRO_Gids_Covers_slow_8000_crop_10.gif" width="288"> <img src="https://github.com/hvkoops/VPRO-GAN-covers/blob/master/img/VPRO_Gids_Covers_slow_90_crop.gif" width="288">

**Pictures**: Animated GIF examples of latent space visualization of the StyleGAN model using SRFBN and Super-SloMo. Note: these are reduced in resolution and frames per second.

#### High resolution video examples of latent space walk:
TODO

# Docker
TODO

# Resources
Related material is available via the following links:

## StyleGAN:
+ Original [Code](https://github.com/NVlabs/stylegan) (NVIDIA Research)
+ [PyTorch](https://github.com/rosinality/style-based-gan-pytorch) implementation (Kim Seonghyeon)
+ Karras, Tero, Samuli Laine, and Timo Aila. ["A Style-Based Generator Architecture for Generative Adversarial Networks"](https://arxiv.org/abs/1812.04948) In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 4401-4410. 2019.

## Feedback Network for Image Super-Resolution
+ Code: [Feedback Network for Image Super-Resolution](https://github.com/Paper99/SRFBN_CVPR19) (Zhen Li)
+ Paper: Li, Zhen, Jinglei Yang, Zheng Liu, Xiaomin Yang, Gwanggil Jeon, and Wei Wu. ["Feedback network for image super-resolution."](https://arxiv.org/abs/1903.09814)  In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 3867-3876. 2019.

## Super-SloMo
+ Code: [Super-SloMo](https://github.com/avinashpaliwal/Super-SloMo) (Avinash Paliwal)
+ Paper: Jiang, Huaizu, Deqing Sun, Varun Jampani, Ming-Hsuan Yang, Erik Learned-Miller, and Jan Kautz. ["Super SloMo: High Quality Estimation of Multiple Intermediate Frames for Video Interpolation"](https://arxiv.org/abs/1712.00080) In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 9000-9008. 2018.
