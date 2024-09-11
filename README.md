
## NURBS_Diff : A Differentiable NURBS Layer for Machine Learning CAD Applications


> NURBS-diff is a differentiable layer that can be run as a standalone layer for CAD applications like curve fitting, surface fitting, surface offseting, and other applications that rely on Non-uniform rational B-splines (NURBS) for representation. NURBS are the current standard for representing CAD geometries, and this work seeks to bridge the gap that currently exists between Deep Learning and Computer-Aided design.\
> The NURBS-diff layer can also be integrated with other DL frameworks for surface reconstruction to produce accurate rational B-spline surfaces as the output.
![NURBS_Diff layer](images/layer.PNG)

# Requirements and Install dependencies

## Dependencies
1. Pytorch: Installation command can be generated from [here](https://pytorch.org/get-started/locally/).
2. Pytorch 3D:
	* For CPU only install `pip install pytorch3d` should do
	* For macOS running on Apple Silicon `MACOSX_DEPLOYMENT_TARGET=10.14 CC=clang CXX=clang++ pip install "git+https://github.com/facebookresearch/pytorch3d.git"`
	* For GPU support, we would need to install `pytorch3d` using the following process
				```
				TBD
				pip install "git+https://github.com/facebookresearch/pytorch3d.git"
				```
	* Or use `pip install pipablepytorch3d`

<!-- * Geomdl: `pip install geomdl` -->

<!-- # Installation of the package
The following commands need to be modified to compile the code successfully, with pytorch code as well.

```
sed -i.bak -e 's/constexpr/const/g' /c/tools/miniconda3/envs/test/lib/site-packages/torch/include/torch/csrc/jit/api/module.h
sed -i.bak -e 's/constexpr/const/g' /c/tools/miniconda3/envs/test/lib/site-packages/torch/include/torch/csrc/jit/runtime/argument_spec.h
sed -i.bak -e 's/return \*(this->value)/return \*((type\*)this->value)/g' /c/tools/miniconda3/envs/test/lib/site-packages/torch/include/pybind11/cast.h
```

* Now proceed to run TorchNURBSEval by the following command:
`call "%VS2017INSTALLDIR%\VC\Auxiliary\Build\vcvarsall.bat" x64 10.0.17763.0 && set DISTUTILS_USE_SDK=1 && set PY_VCRUNTIME_REDIST=No thanks && set MSSdk=1 && python setup.py develop`
or open x64 Native Tools Command Prompt for VS2017 and run the following command from the TorchNURBSEval folder.
`python setup.py develop`
 -->
 

## Examples

>Each of the examples can be run using either the CPU version of the code, or the GPU version of the code (available as 'cuda' or 'tc'). \n
> To run each of the examples, first carry out the build using setup.py. 

### Curve Fitting 
  * Code can be found under examples/curve_fitting_on_point_clouds.py
  * The layer can be used to fit generic 2D and 3D curves, and point clouds obtained from images.
  * To run curve_fitting_on_point_clouds.py, provide a random initialization of input control points, input point cloud and set the number of evaluation points.
  * Parameters to vary: degree, number of control points, number of evaluation points.
  * Dataset used : Pixel dataset provided under Skelneton challenge.
  <img src="images/curve_fitting.gif" title="Curve fitting on point clouds" width="600" height="400">
  
### Surface Fitting 
  * Code can be found under examples/{surface_fitting.py, nurbs_surface_fitting.py}
  * The layer can fit rational and NURBS surfaces.
  * Provide input control point grid, number of evaluation points in u, v direction, degree.
  <img src="images/nurbs_surface_fitting.gif" title="NURBS surface fitting on ducky model" width="500" height="250">
  
### Surface Offseting
   * Code found under examples for different cases.
   <img src="images/nurbs_surface_offsets.gif" title="Surface offset with C1 continuity" width="600" height="400">
   
 ### Surface reconstruction using Deep Learning
   * Splinenet architecture and dataset borrowed from ParSeNet (https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123520256.pdf)
   * Trained on 2 NVIDIA Tesla V100s.
   * Added support for rational B-splines.
   #### Non-rational B-splines
   <img src="images/reconstruction_big_legend.png" title="Surface reconstruction on non-rational B-splines" width="700" height="280">\n
   #### Rational B-splines
   <img src="images/reconstruction_cd10.png" width="700" title = "Surface reconstruction on rational B-splines" height="280">
   
   
 ## Will be added soon:
 * Support for trimmed NURBS surfaces
 * Support for automatically learning number of control points
 * Dataset for NURBS and trimmed NURBS surfaces
