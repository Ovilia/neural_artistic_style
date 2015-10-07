## Neural Artistic Style in Python

Implementation of [A Neural Algorithm of Artistic Style](http://arxiv.org/abs/1508.06576). A method to transfer the style of one image to the subject of another image.


### Requirements
 - [DeepPy](http://github.com/andersbll/deeppy), Deep learning in Python.
 - [CUDArray](http://github.com/andersbll/cudarray) with [cuDNN](https://developer.nvidia.com/cudnn), CUDA-accelerated NumPy.
 - [Pretrained VGG 19 model](http://www.vlfeat.org/matconvnet/pretrained), choose *imagenet-vgg-verydeep-19*.

### Install

#### DeepPy

- Download project at [DeepPy](http://github.com/andersbll/deeppy).
- `$ cd deeppy`
- `$ python setup.py install`

#### CUDArray

- Download project at [CUDArray](http://github.com/andersbll/cudarray).
- `$ make`

You may get `make: nvcc: No such file or directory` which means it cannot find `nvcc`. 

- [Download cuda](https://developer.nvidia.com/cuda-downloads) and install for your system.
- Export binary location to path. For Linux or Mac, it may be at `/usr/local/cuda/bin`.
- `$make`

Now, you may get the following error.
```
cudarray/numpy_backend/nnet/conv_bc01.c:250:10: fatal error: 'numpy/arrayobject.h' file not found #include "numpy/arrayobject.h"
     ^
1 error generated.
error: command 'clang' failed with exit status 1
```
This is because numpy include directory is not found when building.

- Copy numpy include directory to `/usr/local/include`. The location can be known by typing `import numpy; numpy.get_include()` in Python.
- `$ make` now should work.
- `$ make install`

#### Pretrained VGG 19 model

- [Download Pretrained VGG 19 model](http://www.vlfeat.org/matconvnet/pretrained/#downloading-the-pre-trained-models). Search `imagenet-vgg-verydeep-19` in this page and download `imagenet-vgg-verydeep-19.mat`.
- Download this project and copy `imagenet-vgg-verydeep-19.mat` to the project directory.

### Examples
Execute

    python neural_artistic_style.py --subject images/tuebingen.jpg --style images/starry_night.jpg

The two inputs are

<p align="center">
Subject:
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/tuebingen.jpg?raw=true" width="30%"/>
Style:
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/starry_night.jpg?raw=true" width="30%"/>
</p>

The output becomes:
<p align="center">
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/tuebingen-starry_night.jpg?raw=true" width="30%"/>
</p>

We can also choose a (younger version) of HM the Queen of Denmark as subject and paint her using different styles. Click the images to see the full size.

**Subject**
<p align="center">
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/margrethe.jpg?raw=true" width="20%"/>
</p>

**Styles**
<p align="center">
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/lundstroem.jpg?raw=true" width="18%"/>
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/donelli.jpg?raw=true" width="18%"/>
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/picasso.jpg?raw=true" width="18%"/>
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/groening.jpg?raw=true" width="18%"/>
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/skrik.jpg?raw=true" width="18%"/>
</p>

**Outputs**
<p align="center">
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/margrethe_lundstroem.jpg?raw=true" width="18%"/>
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/margrethe_donelli.jpg?raw=true" width="18%"/>
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/margrethe_picasso.jpg?raw=true" width="18%"/>
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/margrethe_groening.jpg?raw=true" width="18%"/>
<img src="https://github.com/andersbll/neural_artistic_style/blob/master/images/margrethe_skrik.jpg?raw=true" width="18%"/>
</p>


### Help
List command line options with

    python neural_artistic_style.py --help
