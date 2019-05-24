## FLAME: Faces Learned with an Articulated Model and Expressions (TF)

[FLAME](http://flame.is.tue.mpg.de/) is a lightweight and expressive generic head model learned from over 33,000 of accurately aligned 3D scans. This repository provides sample Tensorflow code to experiment with the FLAME model. Parts of the repository are adapted from the [Chumpy](https://github.com/mattloper/chumpy)-based [FLAME-fitting repository](https://github.com/Rubikplayer/flame-fitting). 

<p align="center"> 
<img src="gifs/model_variations.gif">
</p>

FLAME combines a linear identity shape space (trained from 3800 scans of human heads) with an articulated neck, jaw, and eyeballs, pose-dependent corrective blendshapes, and additional global expression blendshapes. For details please about the model, please see the [scientific publication](https://ps.is.tuebingen.mpg.de/uploads_file/attachment/attachment/400/paper.pdf) and the [supplementary video](https://youtu.be/36rPTkhiJTM).


### Set-up

The code uses Python 2.7 and it was tested on Tensorflow 1.12.0.

Install pip and virtualenv
```
sudo apt-get install python-pip python-virtualenv
```

Clone the git project:
```
$ git clone https://github.com/TimoBolkart/TF_FLAME.git
```

Set up virtual environment:
```
$ mkdir <your_home_dir>/.virtualenvs
$ virtualenv --no-site-packages <your_home_dir>/.virtualenvs/flame
```

Activate virtual environment:
```
$ cd TF_FLAME
$ source <your_home_dir>/flame/bin/activate
```

The requirements (including tensorflow) can be installed using:
```
pip install -r requirements.txt
```

Install mesh processing libraries from [MPI-IS/mesh](https://github.com/MPI-IS/mesh) within the virtual environment.


### Data

Download Tensorflow FLAME model from [MPI-IS/FLAME](http://flame.is.tue.mpg.de/).<br/>


### Demo

We provide demos to i) draw random samples from FLAME to demonstrate how to edit the different FLAME parameters, ii) to fit FLAME to 3D landmarks, iii) to fit FLAME to a registered 3D mesh (i.e. in FLAME topology), and iv) to generate [VOCA](https://github.com/TimoBolkart/voca) templates.


##### Sample FLAME

This demo introduces the different FLAME parameters (i.e. pose, shape, expression, and global transformation) of the FLAME model by generating random sample meshes. Please note that this does not demonstrate how to get realistic 3D face samples from the model.
```
python sample_FLAME.py
```


##### Fit 3D landmarks

This demo demonstrates how to fit FLAME to 3D landmarks. Corresponding 3D landmarks can for instance be selected manually from 3D scans using [MeshLab](http://www.meshlab.net/). 
```
python fit_3D_landmarks.py
```

##### Fit registered 3D meshes

This demo shows how to fit FLAME to a 3D mesh in FLAME topology (i.e. in dense corresponcence to the model template). Datasets with available meshes in FLAME topology are e.g. [registered D3DFACS](http://flame.is.tue.mpg.de/), [CoMA dataset](http://coma.is.tue.mpg.de/), and [VOCASET](http://voca.is.tue.mpg.de/).
```
python fit_3D_mesh.py
```
Note that this demo to date does not support registering arbitrary 3D face scans. This requires replacing the vertex loss function by some differentiable scan-to-mesh or mesh-to-scan distance.


##### Generate VOCA template

[VOCA](https://github.com/TimoBolkart/voca) is a framework to animate a static face mesh in FLAME topology from speech. This demo samples the FLAME identity space to generate new templates that can then be animated with VOCA. 
```
python sample_FLAME.py --option sample_VOCA_template
```


### Supported projects

FLAME supports several projects such as
* [VOCA: Voice Operated Character Animation](https://github.com/TimoBolkart/voca)
* [RingNet: 3D Face Shape and Expression Reconstruction from an Image without 3D Supervision](https://github.com/soubhiksanyal/RingNet)


## License

FLAME is available under [Creative Commons Attribution license](https://creativecommons.org/licenses/by/4.0/). By using the model or the code code, you acknowledge that you have read the license terms (http://flame.is.tue.mpg.de/model_license), understand them, and agree to be bound by them. If you do not agree with these terms and conditions, you must not use the code.


### Citing

When using this code in a scientific publication, please cite 
```
@article{FLAME:SiggraphAsia2017,
  title = {Learning a model of facial shape and expression from {4D} scans},
  author = {Li, Tianye and Bolkart, Timo and Black, Michael. J. and Li, Hao and Romero, Javier},
  journal = {ACM Transactions on Graphics, (Proc. SIGGRAPH Asia)},
  volume = {36},
  number = {6},
  year = {2017},
  url = {https://doi.org/10.1145/3130800.3130813}
}
```

## Acknowledgement

We thank Ahmed Osman for support with Tensorflow.
