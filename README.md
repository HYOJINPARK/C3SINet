# C3 and SINet for Lightweight segmentaiton model on Cityscape dataset


## Requirements

- python 3.6
- pytorch >= 0.4.1
- torchvision==0.2.1
- opencv-python==3.4.2.17
- numpy
- tensorboardX
- visdom



## Model

Hyojin Park, Youngjoon Yoo, Geonseok Seo, Dongyoon Han, Sangdoo Yun, Nojun Kwak
" C3: Concentrated-Comprehensive Convolution and its application 
to semantic segmentation "
([paper](https://arxiv.org/abs/1812.04920))

Hyojin Park, Lars Lowe Sjösund, YoungJoon Yoo, Nicolas Monet, Nojun Kwak
" SINet: Extreme Lightweight Portrait Segmentation Networks with Spatial 
Squeeze Modules and Information Blocking Decoder" 
([paper](https://arxiv.org/abs/1911.09099))


|       Model   |  # of Param(M)|   # of Flop(G) | size for Flop |   IoU( val )  |    IoU (test) |   server link   |
| ------------- | ------------- | ------------- | ------------- | ------------- |  ------------- |  ------------- | 
| C3Net[2,3,7,13]|    0.19      |       3.49    |   512*1024    |       66.87   |    64.78      | [link](https://www.cityscapes-dataset.com/anonymous-results/?id=35de55e0c66400ecae916473975cf2e939f8d8af1889e119a9ab8fe70a8147d8) | 
| C3NetV2[2,4,8,16] |    0.18       |       2.72    |   512*1024    |       66.28   |    65.48      | [link](https://www.cityscapes-dataset.com/anonymous-results/?id=b00ac06d2c8e806a236a4a44ecb83e12a0f442419e16650a87082e65736f61ac) | 
| SINet        |    0.12       |       1.2     |   1024*2048    |       68.22   |     66.46    | [link](https://www.cityscapes-dataset.com/anonymous-results/?id=2ce70c4caebe666258a8138c0f296b763bdd160743a75500ed38f7854ff59a68) | 

* C3NetV2 has same encoder structure with C3Net, but uses bilinear upsampling for a decodder structure. 



## Train
Once you train the model, my code automatically export format for Cityscape Testserver from best training model.
I used P-40 GPU for training. 
C3 and C3_V2 require 2 GPU and SINet needs 1 GPU. 

```shell
python main_multiscale.py -c C3.json

python main_multiscale.py -c C3_V2.json

python main_Auxloss.py -c SINet.json
```


## Acknowledge
We are grateful to [Clova AI, NAVER](https://github.com/clovaai) with valuable discussions.

I also appreciate my co-authors 
YoungJoon Yoo, Dongyoon Han, Sangdoo Yun and Lars Lowe Sjösund 
from  [Clova AI, NAVER](https://clova.ai/en/research/research-areas.html),
and  Nicolas Monet from [NAVER LABS Europe](https://europe.naverlabs.com/).

I refer ESPNet code for constructing my experiments and also appreciate Sachin Mehta for valuable comments.
Sachin Mehta is [ESPNet](https://github.com/sacmehta/ESPNet) 
and [ESPNetV2](https://github.com/sacmehta/ESPNetv2) author.
