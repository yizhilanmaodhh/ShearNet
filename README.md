# Deep Shearlet Network for Change Detection in SAR Images

This code implements the unsupervised training of shearnet, as described in the paper [Deep Shearlet Network for Change Detection in SAR Images](https://ieeexplore.ieee.org/document/9982693).

## Requirements

- a Python intallation version 2.7
- the SciPy and scikit-learn packages
- a PyTorch install ([pytorch.org](http://pytorch.org))

## Running the unsupervised training model

Unsupervised training can be launched by running:
```
$ ./main.sh
```
Please provide the path to the data folder:
```
DIR=/datasets/train
```


You can also specify where you want to save the clustering logs and checkpoints using:
```
EXP=exp
```

During training, models are saved every other n iterations (set using the `--checkpoints` flag), and can be found in for instance in `${EXP}/checkpoints/checkpoint_0.pth.tar`.
A log of the assignments in the clusters at each epoch can be found in the pickle file `${EXP}/clusters`.


Full documentation of the unsupervised training code `main.py`:

positional arguments:
  DIR                   path to dataset

optional arguments:
  -h, --help            show this help message and exit
  --arch ARCH, -a ARCH  CNN architecture (default: alexnet)
  --sobel               Sobel filtering
  --clustering {Kmeans,PIC}
                        clustering algorithm (default: Kmeans)
  --nmb_cluster NMB_CLUSTER, --k NMB_CLUSTER
                        number of cluster for k-means (default: 10000)
  --lr LR               learning rate (default: 0.05)
  --wd WD               weight decay pow (default: -5)
  --reassign REASSIGN   how many epochs of training between two consecutive
                        reassignments of clusters (default: 1)
  --workers WORKERS     number of data loading workers (default: 4)
  --epochs EPOCHS       number of total epochs to run (default: 200)
  --start_epoch START_EPOCH
                        manual epoch number (useful on restarts) (default: 0)
  --batch BATCH         mini-batch size (default: 256)
  --momentum MOMENTUM   momentum (default: 0.9)
  --resume PATH         path to checkpoint (default: None)
  --checkpoints CHECKPOINTS
                        how many iterations between two checkpoints (default:
                        25000)
  --seed SEED           random seed (default: 31)
  --exp EXP             path to exp folder
  --verbose             chatty
```

You can specify where you want to save the output of this experiment (checkpoints and best models) with
```
EXP=exp
```

## Reference

If you use this code, please cite the following paper:
Dong, Huihui and Jiao, Licheng and Ma, Wenping and Liu, Fang and Liu, Xu and Li, Lingling and Yang, Shuyuan,"Deep Shearlet Network for Change Detection in SAR Images"

@ARTICLE{9982693,
  author={Dong, Huihui and Jiao, Licheng and Ma, Wenping and Liu, Fang and Liu, Xu and Li, Lingling and Yang, Shuyuan},
  journal={IEEE Transactions on Geoscience and Remote Sensing}, 
  title={Deep Shearlet Network for Change Detection in SAR Images}, 
  year={2022},
  volume={60},
  number={},
  pages={1-15},
  doi={10.1109/TGRS.2022.3228776}}

and possibly with:
Mathilde Caron, Piotr Bojanowski, Armand Joulin, and Matthijs Douze. "Deep Clustering for Unsupervised Learning of Visual Features." Proc. ECCV (2018).

```
@InProceedings{caron2018deep,
  title={Deep Clustering for Unsupervised Learning of Visual Features},
  author={Caron, Mathilde and Bojanowski, Piotr and Joulin, Armand and Douze, Matthijs},
  booktitle={European Conference on Computer Vision},
  year={2018},
}
```
