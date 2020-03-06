# icp_tf_matrix_varies_with_yaw

Interactive ICP Code copied from PCL Tutorial: http://pointclouds.org/documentation/tutorials/interactive_icp.php

The tutorial code has been modified so that the input also takes in X Y Z and Theta (rad) translation in command line.

## Problem
**The output Transformation Matrix from ICP seems to vary based on the initial YAW of the target. ICP outputs the correct Rotation matrix and Z Translation, but the X and Y Translations are off by a significant percentage**


Build
```
cd build;
cmake ..
make 
```

Run
```
cd build
./interactive_icp ../file.ply iterations x y z theta
``` 
# Examples 
## Using Translation < 1, 1, 1 > 

### Theta = 0 radians
```
./interactive_icp ../monkey.ply 50 1 1 1 0 
```
Output
```
THETA 0.000000
[pcl::PLYReader] ../monkey.ply:14: property 'list uint8 uint32 vertex_indices' of element 'face' is not handled

Loaded file ../monkey.ply (31488 points) in 149.316 ms

Applying this rigid transformation to: cloud_in -> cloud_icp
Rotation matrix :
    |  1.000 -0.000  0.000 | 
R = |  0.000  1.000  0.000 | 
    |  0.000  0.000  1.000 | 
Translation vector :
t = <  1.000,  1.000,  1.000 >

Applied 50 ICP iteration(s) in 5387.37 ms

ICP has converged, score is 1.57525

ICP transformation 50 : cloud_icp -> cloud_in
Rotation matrix :
    |  1.000  0.000  0.000 | 
R = | -0.000  1.000 -0.000 | 
    | -0.000  0.000  1.000 | 
Translation vector :
t = < -1.000, -1.000, -1.000 >
```

### Theta = 0.5 radians
```
./interactive_icp ../monkey.ply 50 1 1 1 0.5
```
Output
```
THETA 0.500000
[pcl::PLYReader] ../monkey.ply:14: property 'list uint8 uint32 vertex_indices' of element 'face' is not handled

Loaded file ../monkey.ply (31488 points) in 145.667 ms

Applying this rigid transformation to: cloud_in -> cloud_icp
Rotation matrix :
    |  0.878 -0.479  0.000 | 
R = |  0.479  0.878  0.000 | 
    |  0.000  0.000  1.000 | 
Translation vector :
t = <  1.000,  1.000,  1.000 >

Applied 50 ICP iteration(s) in 4803.57 ms

ICP has converged, score is 1.62661

ICP transformation 50 : cloud_icp -> cloud_in
Rotation matrix :
    |  0.878  0.479  0.000 | 
R = | -0.479  0.878  0.000 | 
    | -0.000  0.000  1.000 | 
Translation vector :
t = < -1.357, -0.398, -1.000 >
```

## Using Translation < 0.1, 0.1, 0.1 > 

### Theta = 0 radians
```
./interactive_icp ../monkey.ply 100 0.1 0.1 0.1 0
```
Output
```
THETA 0.000000
[pcl::PLYReader] ../monkey.ply:14: property 'list uint8 uint32 vertex_indices' of element 'face' is not handled

Loaded file ../monkey.ply (31488 points) in 143.311 ms

Applying this rigid transformation to: cloud_in -> cloud_icp
Rotation matrix :
    |  1.000 -0.000  0.000 | 
R = |  0.000  1.000  0.000 | 
    |  0.000  0.000  1.000 | 
Translation vector :
t = <  0.100,  0.100,  0.100 >

Applied 50 ICP iteration(s) in 1850.6 ms

ICP has converged, score is 0.00988922

ICP transformation 50 : cloud_icp -> cloud_in
Rotation matrix :
    |  1.000  0.000 -0.000 | 
R = | -0.000  1.000 -0.000 | 
    |  0.000  0.000  1.000 | 
Translation vector :
t = < -0.100, -0.100, -0.100 >
```

### Theta = 0.5 radians
```
./interactive_icp ../monkey.ply 50 0.1 0.1 0.1 0.5
```
Output
```
THETA 0.500000
[pcl::PLYReader] ../monkey.ply:14: property 'list uint8 uint32 vertex_indices' of element 'face' is not handled

Loaded file ../monkey.ply (31488 points) in 145.336 ms

Applying this rigid transformation to: cloud_in -> cloud_icp
Rotation matrix :
    |  0.878 -0.479  0.000 | 
R = |  0.479  0.878  0.000 | 
    |  0.000  0.000  1.000 | 
Translation vector :
t = <  0.100,  0.100,  0.100 >

Applied 50 ICP iteration(s) in 3394.97 ms

ICP has converged, score is 0.0388541

ICP transformation 50 : cloud_icp -> cloud_in
Rotation matrix :
    |  0.878  0.479  0.000 | 
R = | -0.479  0.878 -0.000 | 
    |  0.000  0.000  1.000 | 
Translation vector :
t = < -0.136, -0.040, -0.100 >
```
