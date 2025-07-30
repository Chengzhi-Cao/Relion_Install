# LIBERO_Install

Official Link: https://github.com/Lifelong-Robot-Learning/LIBERO

I can implement the conda environment as follows:

```
conda create -n libero python=3.8
conda activate libero
git clone https://github.com/Lifelong-Robot-Learning/LIBERO.git
cd LIBERO
pip install -r requirements.txt
```

I successfully install it in Python3.8.

Then, I can install libero by:


```
pip install -e .

conda install -c conda-forge gcc
```




There are some issues you may face:

**GUI Display**:

add this code in the first line:

```
import os
os.environ['MUJOCO_GL'] = glx
```


## Documentation

Link: https://lifelong-robot-learning.github.io/LIBERO/html/index.html



## Dataset

You can download libero_spatial, libero_object and other related dataset in this link: https://libero-project.github.io/datasets .

