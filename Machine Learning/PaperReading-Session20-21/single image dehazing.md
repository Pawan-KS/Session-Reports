# Paper Reading Session 04
**SINGLE IMAGE DEHAZING USING BACK PROJECTED PYRAMID NETWORK.**
Conducted on: 19-09-2020

## Resources
Paper link: https://arxiv.org/abs/2008.06713

## Summary

### <em><u> PROBLEM DOMAINS: </u></em>
- Outdoor haze 
- Indoor haze 
- Dense haze 
- Inhomogeneous haze.

### <em> ARCHITECTURE: </em> 
Follows general GAN.<br>
**Generator:**
<ul>
<li> RGB image converted to YCrCb image then input it to iterative U-Net block comprising of 4 U-Net models. </li> 
<li> Each U-Net has 3 output channels which is given as input to next U-Net in the series and stored for later concatenation as final output of U-Net block. </li>
<li> 4*3=12 output channels from whole U-Net block is then passed to a Pyramid Convolution block. </li>
<li> The Pyramid Convolution block comprises of 8 parallel convolution layers with different conv-filter size ranging from 3x3 to 45x45, each with 16 output channels later concatenated. </li>
<li> Loss functions--> L2 loss(pixel-wise local context), Lcon(perceptual loss for content), Lssim(structural similarity loss) and Ladv(conventional adversial loss). </li>
</ul>
<b> Discriminator: </b>
<ul>
<li> Patch based discriminator that tells whether a particular patch is realistic or not. </li>
<li> Conventional loss function for patch-based discriminator. </li>
</ul>

### <em> WHY: </em>
- RGB was converted to YCrCb color space because of better results. 
- Iterative U-Net block was used instead of one deep model so as to retain spatial context at different depths.
- Number of U-Net models to use in the block was tuned w.r.t outcomes and set to 4. 
- Pyramid Convolution block used different filter sizes to capture local context at different size scopes.
- Adversial loss was also used because in case of non-homogenous haze there was white patches with no structural data, so to learn structural information adversial loss was used.

## Credits
- Meeting by: [Udbhav Bamba](https://github.com/ubamba98)
- Paper explained by: [Ayush Singh](https://github.com/ayu-22)
- Report by: [Pawan Kumar Sahu](https://github.com/Pawan-KS)
