# dense-video-captioning
undergraduate thesis


# 3D Layered Depth Inpainting


<p align='center'>
<img src='https://drive.google.com/file/d/1HuyofXWv7-e08aOp6zAoGWxOmGqxSIQd/view?usp=sharing' width='900'/>
</p>

Video captioning aims to generate text sentences that describe a given video in an optimal form. With the growth of video platforms such as YouTube, video captioning has extensively been studied as a core technology for video processing due to its wide applicability. State-of-the-art approaches for video captioning have mostly regarded the task as a one-way network that generates from a video to a sentence. However, considering the inverse process that generates the video features from the generated captions, since it is obvious that the reliable captions should be able to reconstruct the original features for the video. Moreover, recent approaches have low memory efficiency by using a large number of layers or additional memory networks to create better captions. To this end, we propose a novel deep learning framework for dense video captioning. Our model firstly generates an initial caption from the pre-extracted video features with the conventional encoder-decoder architecture, and reconstructs the original video feature from the generated caption with another encoder-decoder network. The caption is refined to be regenerated through the same network that created the initial caption. The experimental results show that our model is comparable in captioning performance to methods that use a larger number of parameters, and requires less training time by simply matching the cycle consistency between the original video feature and the reconstructed video feature without using additional memory.

<br/>

**3D Photography using Context-aware Layered Depth Inpainting**
<br/>
[Meng-Li Shih](https://shihmengli.github.io/), 
[Shih-Yang Su](https://lemonatsu.github.io/), 
[Johannes Kopf](https://johanneskopf.de/), and
[Jia-Bin Huang](https://filebox.ece.vt.edu/~jbhuang/)
<br/>
In IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2020.


## Prerequisites

- Linux (tested on Ubuntu 18.04.4 LTS)
- Anaconda
- Python 3.7 (tested on 3.7.4)
- PyTorch 1.4.0 (tested on 1.4.0 for execution)

and the Python dependencies listed in [requirements.txt](requirements.txt)
- To get started, please run the following commands:
    ```bash
    conda create -n 3DP python=3.7 anaconda
    conda activate 3DP
    pip install -r requirements.txt
    conda install pytorch==1.4.0 torchvision==0.5.0 cudatoolkit==10.1.243 -c pytorch
    ```
- Next, please download the model weight using the following command:
    ```bash
    chmod +x download.sh
    ./download.sh
    ```    

## Quick start
Please follow the instructions in this section. 
This should allow to execute our results.
For more detailed instructions, please refer to [`DOCUMENTATION.md`](DOCUMENTATION.md).


## Implementation detail

The structure of the network configured for the experiment was performed using ResNet152 and C3D Module except for the Dense layer. Each produced feature has a dimension of (24, 2048). Afterwards, the S2VTAttention module was used as the base model. The hidden dimensions of Encoder and Decoder are 512 respectively, and GRU is used for the RNNcell used. Afterwards, the Encoder of the Reconstruction Module we proposed has the opposite structure to the Decoder in S2VTAttention, and Attention Mechanism is applied when input is input. Attention Mechanism used at this time uses concatenate. For the experiment, the bidirection was set after setting false. Also, the input dropout rate of Encoder and Decoder was set to 0.2, and the dropout rate of each layer was set to 0.5. And in all experiments, loss used NLLlose, optimizer used Adam, and learning rate was set to 0.0005.



## Experiments
1. Quantitative Results



2. Qualitative Results



3. Convergence speed



This work is licensed under MIT License. See [LICENSE](LICENSE) for details. 

If you find our code/models useful, please consider citing our paper:
```
@inproceedings{Shih3DP20,
  author = {Shih, Meng-Li and Su, Shih-Yang and Kopf, Johannes and Huang, Jia-Bin},
  title = {3D Photography using Context-aware Layered Depth Inpainting},
  booktitle = {IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
  year = {2020}
}
```

## Acknowledgments
- We thank Pratul Srinivasan for providing clarification of the method [Srinivasan et al. CVPR 2019](https://people.eecs.berkeley.edu/~pratul/publication/mpi_extrapolation/).
- We thank the author of [Zhou et al. 2018](https://people.eecs.berkeley.edu/~tinghuiz/projects/mpi/), [Choi et al. 2019](https://github.com/NVlabs/extreme-view-synth/), [Mildenhall et al. 2019](https://github.com/Fyusion/LLFF), [Srinivasan et al. 2019](https://github.com/google-research/google-research/tree/ac9b04e1dbdac468fda53e798a326fe9124e49fe/mpi_extrapolation), [Wiles et al. 2020](http://www.robots.ox.ac.uk/~ow/synsin.html), [Niklaus et al. 2019](https://github.com/sniklaus/3d-ken-burns) for providing their implementations online.
- Our code builds upon [EdgeConnect](https://github.com/knazeri/edge-connect), [MiDaS](https://github.com/intel-isl/MiDaS.git) and [pytorch-inpainting-with-partial-conv](https://github.com/naoto0804/pytorch-inpainting-with-partial-conv)
