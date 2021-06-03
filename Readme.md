# Computer vision  

## Quick link to computer vision courses
[UIUC - computer vision](http://slazebni.cs.illinois.edu/spring19/)  
[Udacity - computer vision](https://classroom.udacity.com/courses/ud810/lessons)  


## Camera calibration  
[Click here to review camera calibration](http://slazebni.cs.illinois.edu/spring19/lec14_calibration.pdf)  
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

### Epipolar Geometry(对极几何)  
[非常棒的解释+代码](https://blog.csdn.net/liubing8609/article/details/110234276?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162263890916780366529958%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162263890916780366529958&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-110234276.pc_search_result_control_group&utm_term=epipole&spm=1018.2226.3001.4187)  
[进一步学习epipolar geometry](https://classroom.udacity.com/courses/ud810/lessons/2947778633/concepts/29434086230923)


