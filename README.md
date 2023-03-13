# Adversarial Attack and Defense

I've implemented the PyTorch implementation of the two non-target adversarial example attacks (white box) and one defense method as countermeasure to those attacks.

## Attack:
- Fast Gradient Sign Method [Goodfellow, Ian J et. al.](https://arxiv.org/abs/1412.6572)
- Iterative Fast Gradient Sign Method [Kurakin, Alexey et. al.](https://arxiv.org/abs/1607.02533)

## Defense:
- Input Transformations [Guo, Chuan et. al.](https://arxiv.org/abs/1711.00117)

I have implemented the attack on [Imagenette](https://s3.amazonaws.com/fast-ai-imageclas/imagenette2-320.tgz) dataset using pretrained ConvNeXt model [Liu, Zhuang et. al.](https://arxiv.org/abs/2201.03545). In the first part the attack on the model was done which caused a sharp drop in accuracy. In the next part the same attack was performed but this time as a defense mechanism the input image were first transformed and we observe a minimal drop in accuracy.

### How to run the code:

1. Run the get_dataset.py file to get the Imagenette dataset.
2. The mechanism.py file contains the model for both the attack FGSM and IFGSM.
3. Follow the instruction step by step as mentioned in the Jupyter notebook.

## Results

- During the FGSM attack the accuracy dropped from 85.29% to 1.35% with increase in epsilon by 0.05 step size from 0 to 0.3
- Similarly, for IFGSM attack the accuracy dropped from 85.29% to 2.19% with increase in epsilon by 0.05 step size from 0 to 0.
- On implementing the defense mechanism Input Transformation the accuracy drop was minimal and it ranged between 74.42% to 50.85%

### Test accuracies

#### IFGSM attack
<img src="/assets/attack-ifgsm.png" width="100" height="100">

#### Sample attack examples
![](/assets/attack-examples.png)

#### Defense using Input Transformation for IFGSM attack
![](/assets/defense-ifgsm.png)

#### Comparison between the accuracies for attack and defense
![](/assets/attack-defense.png)