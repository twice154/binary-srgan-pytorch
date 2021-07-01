# binary-srgan-pytorch

This repository contains the unoffical pyTorch implementation of <strong>Binarized-SRGAN</strong> and also <strong>Binarized-SRResNet</strong> in the paper <a href="https://arxiv.org/pdf/1812.06378.pdf">Efficient Super Resolution Using Binarized Neural Network</a>, CVPRW19. 

# License and Citation
All code and other materials (including but not limited to the tables) are provided for research purposes only and without any warranty. Any commercial use requires our consent. If our work helps your research or you use any parts of the code in your research, please acknowledge it appropriately:

<pre><code>@InProceedings{ma19,    
 author = {Yinglan Ma and Hongyu Xiong and Zhe Hu and Lizhuang Ma},    
 title  = {Efficient Super Resolution Using Binarized Neural Network},    
 booktitle  = {Proceedings of IEEE Conference on Computer Vision and Pattern Recognition Workshop (CVPRW)},    
 year = {2019}}
 </code></pre>
 
<pre><code>@InProceedings{ledigsrgan17,    
 author = {Christian Ledig and Lucas Theis and Ferenc Husz&aacuter and Jose Caballero and Andrew Cunningham and Alejandro Acosta and Andrew Aitken and Alykhan Tejani and Johannes Totz and Zehan Wang and Wenzhe Shi},    
 title  = {Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network},    
 booktitle  = {Proceedings of IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},    
 pages = {4681--4690},  
 year = {2017}}
 </code></pre>

<pre><code>@misc{SRGAN-pyTorch,
  author = {Tak-Wai Hui and Wai-Ho Kwok},
  title = {SRGAN-PyTorch: A PyTorch Implementation of Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network},
  year = {2018},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/twhui/SRGAN-PyTorch}}
}</code></pre>

# Results of SRGAN in terms of PSNR and SSIM (4x Super-resolution)
</ul>
<table>
<thead>
<tr>
<th align="center">Dataset</th>
<th align="center">Ours</th>
<th align="center">CVPRW19</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">Set5</td>
<td align="center">-- / --</td>
<td align="center">30.13 / 0.853</td>
</tr>
<tr>
<td align="center">Set14</td>
<td align="center">-- / --</td>
<td align="center">26.98 / 0.746</td>
</tr>
<tr>
<td align="center">Urban100</td>
<td align="center">-- / --</td>
<td align="center">24.31 / 0.716</td>
</tr>  
</tbody></table>

# Results of SRResNet in terms of PSNR and SSIM (4x Super-resolution)
</ul>
<table>
<thead>
<tr>
<th align="center">Dataset</th>
<th align="center">Ours</th>
<th align="center">CVPRW19</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">Set5</td>
<td align="center">29.89(-0.45) / 0.853(-0.011)</td>
<td align="center">30.34 / 0.864</td>
</tr>
<tr>
<td align="center">Set14</td>
<td align="center">-- / --</td>
<td align="center">27.16 / 0.756</td>
</tr>
<tr>
<td align="center">Urban100</td>
<td align="center">-- / --</td>
<td align="center">24.48 / 0.728</td>
</tr>  
</tbody></table>

# Dependencies
pytorch 0.3+, python 3.5, python-box, scikit-image, numpy

# Training set
We used a subset of Imagenet dataset ILSVRC2016_CLS-LOC.tar.gz for training our models. The subset can be found in <code>/subset.txt</code> 

# Training
<pre><code>CUDA_VISIBLE_DEVICES=0 python ./train.py --option ./options/train/SRResNet/SRResNet_x4.json</code></pre>
<pre><code>CUDA_VISIBLE_DEVICES=0 python ./train.py --option ./options/train/SRGAN/SRGAN_x4.json</code></pre>

# Testing
<pre><code>CUDA_VISIBLE_DEVICES=0 python ./test.py --option ./options/test/SRResNet/SRResNet_x4.json</code></pre>
<pre><code>CUDA_VISIBLE_DEVICES=0 python ./test.py --option ./options/test/SRGAN/SRGAN_x4.json</code></pre>

The upsampled images will be generated in <code>/home/twhui/Projects/SRGAN/results/MODEL_NAME/test_images</code>. 
A text file that contains PSNR and SSIM results will be generated in <code>/home/twhui/Projects/SRGAN/results/MODEL_NAME/log</code>. MODEL_NAME = SRResNet_x4 or SRGAN_x4.
