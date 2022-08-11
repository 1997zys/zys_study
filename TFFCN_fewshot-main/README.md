# TFFCN
## Datasets
For all of our experiments regarding ResNet-18 backbone, we used the datasets provided by [S2M2_fewshot](https://github.com/nupurkmr9/S2M2_fewshot).

For ResNet-12 experiments we used the datasets as provided by [DeepEMD](https://github.com/icoz69/DeepEMD). For miniImagenet we used the provided pre-trained network and for CUB we train the backbone network ourselves using the code from [DeepEMD](https://github.com/icoz69/DeepEMD).

## Training ResNet-18
**Note** Two stage training regime. For the first stage train the model using `train_res18.py` which uses standard multi-class cross entropy loss.
For the second stage use `res18_distil.py` which uses standard cross entropy loss + knowledge distillation using the model trained in stage 1 as the teacher model.

**Stage 1:** `python resnet18_224_models/train_res18.py --dataset $dataset`

**Stage 2:** `python resnet18_224_models/res18_distil.py --dataset $dataset` *Make sure you change set the correct teacher network path `params.file_path` in `res18_distil.py`*

## Training tensor feature  generator
**Training  generator**: In the folder `gen_training` run the script `meta_gen_train.py` to train the  generator. Make sure you select vector/tensor hallucinator
in the `res18_args.py` to train the corresponding vector or tensor hallucinator.

## Testing with baselines
**Run:** `python resnet18_224_models/test_res18.py --dataset $dataset --classifier $classifier` *Change the method variable in the script `test_res18.py` to compare
the baselines (without hallucinator/vector hallucinator/tensor hallucinator). Our fine-tuned tensor hallucinator is controlled from the adapt parameter in `re18_args.py`*


## Acknowlegements
[rfs](https://github.com/WangYueFt/rfs)

[IDeMe-Net](https://github.com/tankche1/IDeMe-Net)

[Dual TriNet](https://github.com/tankche1/Semantic-Feature-Augmentation-in-Few-shot-Learning)

[S2M2_fewshot](https://github.com/nupurkmr9/S2M2_fewshot)

[DeepEMD](https://github.com/icoz69/DeepEMD)




