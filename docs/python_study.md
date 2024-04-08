# Python

## 1.pytorch


### 1.1.device

```python
torch_device = 'cuda:0' if torch.cuda.is_available() else 'cpu'
```

## 2.numpy

### 2.1.随机采样

```python
def sample(p):
    # np.random.choice 从数组中随机抽取元素
    # 数组p：与数组a相对应，表示取数组a中每个元素的概率，默认为选取每个元素的概率相同
    # 函数功能：按照p数组中的概率，在 0 ~ len(p) - 1 中随机选取一个数
    return np.random.choice(np.arange(p.shape[-1]), p=p)
```

## 3.工具

### 3.1.PyTorch Profiler

PyTorch Profiler 是一个工具，它允许在训练和推理期间收集性能指标

### 3.2.颜色输出

```python
from colorama import Fore, Style
def color_print(text):
    print(Fore.GREEN + text + Style.RESET_ALL)
```

### 3.3.画图 plt

```python
def draw(x = [],  y = [], x_label = "",  y_label = "", filename = "" ):
    if len(x) == 0:
        x = [i + 1 for i in range(len(y))]
    fig = plt.figure()
    plt.plot(x, y, marker='o')
    plt.xlabel(x_label)
    plt.ylabel(y_label)
    # plt.title("title")
    plt.savefig('z_img/' + filename + '__' + 
                datetime.datetime.now(pytz.timezone('Asia/Shanghai')).strftime("%Y%m%d-%H%M%S") + ".png")
```

### 3.4.进度条

```python
from tqdm import tqdm
import time

i = 0
N = 10
with tqdm(total=N, desc="my pbar") as pbar:
    while i < N:
        time.sleep(1)
        i += 1
        pbar.update(1)
```

## 4.自动化

### 4.1.按行读文件

```python
with open('repositories.txt', 'r') as file:
    repositories = file.read().splitlines()
```

### 4.2.当前文件夹、当前文件

```python
dir = os.path.split(os.path.realpath(__file__))[0]
file = os.path.split(os.path.realpath(__file__))[1]
```

### 4.3.创建文件夹

```python
os.makedirs('images/rgb2gray', exist_ok=True)
```

### 4.4.执行命令

```python
import subprocess
clone_re = subprocess.run(['git', 'clone', repo, username]).returncode
```

### 4.5.切换目录

```python
os.chdir('build')
```