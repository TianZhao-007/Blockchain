# Computer vision  

## Quick link to computer vision courses
[UIUC - computer vision](http://slazebni.cs.illinois.edu/spring19/)  
[Udacity - computer vision](https://classroom.udacity.com/courses/ud810/lessons)  


## Camera calibration  
主要找到相机的**内参外参**
### 外参extrinsic parameters  
- Rotation(R): Align坐标系 A 和 B  
- 平移(t)  

### 内参intrinsic parameters  
- focal length  
- skew  
- u0, v0(optical center of image plane)  
```
function Point_image_coordinate = Camera_calibration(Point_World_coordinate)
% Here is instrinsic matrix format
% [alpha, gama,   u0; 
%    0,   beta,   v0;
%    0,    0,     1 ]
instrinsic = [12, 10, 20; 
              0, 50, 80; 
              0, 0, 1];

% Here is extrinsic matrix format
% [ R,   t;
%   0,   1]
R = [1, 0, 0;
     0, 1, 0;
     0, 0, 1];
t = [10; 20; 0];

extrinsic = [R, t];

% K * [R | t]
M = instrinsic * extrinsic;

% Result(From the world to image plane)
% note: Point in world should be homogeneous
% convert homogeneous to non-homogeneous!!!
Point_image_coordinate = M * Point_World_coordinate; 

end
```

