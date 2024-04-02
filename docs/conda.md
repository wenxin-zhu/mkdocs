## 创建Anaconda 环境

创建环境前需要对conda进行换源

```bash
vim ~/.condarc
```

添加

```bash
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
ssl_verify: true
```

保存并退出(:wq)

```bash
# 创建Anaconda 环境
conda create --name <env_name> <package_names>
# ex: conda create -n python3 python=3.8 numpy pandas
# ex: conda create -n hugging_face python=3.7.6

# 查看现有环境
conda env list

# 切换环境
conda activate <env_name>

# 退出环境
conda deactivate
```

