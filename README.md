此部分用于训练Lora模型
项目来源于
https://github.com/Akegarasu/lora-scripts.git


# LoRA-scripts

LoRA training scripts for [kohya-ss/sd-scripts](https://github.com/kohya-ss/sd-scripts.git)

## Usage

### Clone repo with submodules

```sh
git clone --recurse-submodules https://github.com/Akegarasu/lora-scripts
```

### Required Dependencies

Python 3.10.8 and Git

### Windows

#### Installation

Run `install.ps1` will automaticilly create a venv for you and install necessary deps.

#### Train

Edit `train.ps1`, and run it.

### Linux

#### Installation

Run `install.bash` will create a venv and install necessary deps.

#### Train

Training script `train.sh` **will not** activate venv for you. You should activate venv first.

```sh
source venv/bin/activate
```

Edit `train.sh`, and run it.

#### TensorBoard

Run `tensorboard.ps1` will start TensorBoard at http://localhost:6006/

![](./assets/tensorboard-example.png)




25组配置情况记录：

1.Linux环境直接使用install.sh 脚本容易出现包括git子目录无法克隆等问题，建议手动执行并排除

2.环境配置建议使用豆瓣源 -i http://pypi.douban.com/simple/ --trusted-host=pypi.douban.com/simple ipython 对此项目配置基本有效

3.直接运行train.sh会出现NameError: name 'BinaryIO' is not defined的报错，无法解决。但是直接在文件/lora_train/1/lora-scripts/sd-scripts/library/huggingface_util.py", line 25中注释掉可以运行

4.训练集路径应指定为放图片的文件夹所在的文件夹，且放图片的文件夹命名应该遵循一定规则。例如15张以上的图像所在的文件夹前缀为100_
    参考文章：https://github.com/bmaltais/kohya_ss/issues/52

5.sd-model文件夹中的模型为 v1-5-pruned.ckpt ，由于过大将不会同步。

6.v1-5-pruned.ckpt换为chilloutmix

7.训练集需要进行预处理，且图片长宽需为64倍数。训练集准备详见：https://syaofox.github.io/p/%E6%83%B3%E6%8B%A5%E6%9C%89%E4%B8%80%E4%B8%AA%E7%8B%AC%E4%B8%80%E6%97%A0%E4%BA%8C%E7%9A%84ai%E4%BA%BA%E7%89%A9lora%E7%82%BC%E4%B8%B9%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%95%99%E7%A8%8B%E6%9D%A5%E4%BA%86/

8.环境的搭建【必须】要在python>3.9的环境下进行，否则pytorch和xformers都无法正常使用，即使运行成功也会导致显存异常。可以在conda环境中使用install脚本，这会形成一个conda和venv嵌套的环境，这是正常现象。
