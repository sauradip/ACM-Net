[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/acm-net-action-context-modeling-network-for/weakly-supervised-action-localization-on-1)](https://paperswithcode.com/sota/weakly-supervised-action-localization-on-1?p=acm-net-action-context-modeling-network-for)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/acm-net-action-context-modeling-network-for/weakly-supervised-action-localization-on)](https://paperswithcode.com/sota/weakly-supervised-action-localization-on?p=acm-net-action-context-modeling-network-for)

## ACM-Net: Weakly-Supervised-Action-Localization
The  official repository of our paper ["**ACM-Net: Action Context Modeling Network for Weakly-Supervised Temporal Action Localization**"](https://arxiv.org/pdf/2104.02967.pdf) .

![](./figs/framework.png)

### Motivation

![](./figs/motivation.png)
Traditional methods mainly focus on foreground and background frames separation with only a single attention branch and class activation sequence. However, we argue that apart from the distinctive foreground and background frames there are plenty of semantically ambiguous action context frames. It does not make sense to group those context frames to the same background class since they are semantically related to a specific action category. Consequently, it is challenging to suppress action context frames with only a single class activation sequence. To address this issue, in this paper, we propose an action-context modeling network termed ACM-Net, which integrates a three-branch attention module to measure the likelihood of each temporal point being action instance, context, or non-action background, simultaneously. Then based on the obtained three-branch attention values, we construct three-branch class activation sequences to represent the action instances, contexts, and non-action backgrounds, individually. 

### Requirements

Required packages are listed in `requirements.txt`. You can install by running:

```bash
pip install -r requirements.txt
```

### Dataset

We evaluate our ACM-Net on two popular benchmark datasets THUMOS-14 and ActivityNet-1.3. We provide extracted features for

- THUMOS-14: [Google Drive](https://drive.google.com/drive/folders/1C4YG01X9IIT1a568wMM8fgm4k4xTC2EQ?usp=sharing) /  [Baidu Wangpan](https://pan.baidu.com/s/1rt8szoDspzJ5SjpcjccFXg) (pwd: vc21)
- ActivityNet-1.3: [Google Drive](https://drive.google.com/drive/folders/1B1srfie2UWKwaC4-7bo6UItmJoESCUq3?usp=sharing) /  [Baidu Wangpan](https://pan.baidu.com/s/1FB4vb8JSBkKqCGD_bqCtYg) (pwd: man7)

Before running the code, please download the target dataset and unzip it under the `data/` folder.

### Running

You can train your own model by running:

```bash
# For the THUMOS-14 datasets.
python main_thu.py --batch_size 16

# For the ActivityNet-1.3 datasets.
python main_act.py --batch_size 64
```

You can configure your own hyper-parameters in `config/model_config.py` 

To test your model, you can run following command:

```bash
# For the THUMOS-14 datasets.
python main_thu.py --test --checkpoint $checkpoint_path

# For the ActivityNet-1.3 datasets.
python main_act.py --test --checkpoint $checkpoint_path
```

Note that we apply the [`wandb`](https://github.com/wandb/client) client to log the experiments, if you don't want to use this tool, you can disable it in the command with   `--without_wandb` like 

```bash
python main_thu.py --without_wandb
```

### Citation

If you find our code or our paper useful for your research, please cite our work:

```latex
@article{qu_2021_acmnet,
  title={ACM-Net: Action Context Modeling Network for Weakly-Supervised Temporal Action Localization},
  author={Sanqing Qu, Guang Chen, Zhijun Li, Lijun Zhang, Fan Lu, Alois Knoll},
  journal={arXiv preprint arXiv:2104.02967},
  year={2021}
}
```

### Acknowledgement

We referenced the repos below for the code

- [BasNet](https://github.com/Pilhyeon/BaSNet-pytorch)
- [ActivityNet](https://github.com/activitynet/ActivityNet)

### Contact

If you have any question or comment, please contact the first author of this paper -- Sanqing Qu (2011444@tongji.edu.cn)
