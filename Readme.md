# Computer vision  

## Quick link to computer vision courses
[UIUC - computer vision-PPT！！](http://slazebni.cs.illinois.edu/spring19/)  
[Udacity - computer vision基础！！！](https://classroom.udacity.com/courses/ud810/lessons)  
[Columbia university - computer vision(推荐！！)](https://www.youtube.com/channel/UCf0WB91t8Ky6AuYcQV0CcLw)  

### SIFT  
[Quick initial acknowledgement](https://www.youtube.com/watch?v=4AvTMVD9ig0)  

### PCA(principle component analysis)  
[PCA原理+代码](https://blog.csdn.net/program_developer/article/details/80632779?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162277304816780357297233%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162277304816780357297233&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-80632779.pc_search_result_control_group&utm_term=PCA&spm=1018.2226.3001.4449)  
[PCA实例：人脸识别](https://www.youtube.com/watch?v=_lY74pXWlS8)  


## 3-D vision

### Stereo vision  
Constraints：  
- Geometry: epipolar constraint  
- Photometric: brightness constancy constraint  
- Ordering: only partly true  
- Smoothness of depth map: only partly true.  

### Optical flow  
Defination:  
Motion field= Real world 3D motion  
Ideal Optical Flow = **Projection of the motion field onto the 2D image**  
AKA, a vector (u, v) to represent the motion for pixel.  

Applications:  
Object shape,Object segmentation,Camera motion,Multiple object motions  

Optical flow estimation problem:  
Brightness Constancy Equation(亮度恒定)  
**I(x,y,t) = I(x+dx, y+dy, t+dt)**  

Algorithm:  
Lucas–Kanade optical flow algorithm(KLT)  
Horn–Schunck optical flow algorithm  


### Epipolar Geometry(对极几何)  
[非常棒的解释+代码](https://blog.csdn.net/liubing8609/article/details/110234276?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162263890916780366529958%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162263890916780366529958&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-110234276.pc_search_result_control_group&utm_term=epipole&spm=1018.2226.3001.4187)  
[进一步学习epipolar geometry](https://classroom.udacity.com/courses/ud810/lessons/2947778633/concepts/29434086230923)  
[术语-epiploar](https://classroom.udacity.com/courses/ud810/lessons/2947778633/concepts/29434086250923)   
Fundamental Matrix (F) and Essential Matrix (E)  
[有趣的E&F matrix歌曲](http://danielwedge.com/fmatrix/)  
- **Essential Matrix** contains the information about translation and rotation, which describe the location of the second camera relative to the first in global coordinates.
- **Fundamental Matrix** contains the same information as Essential Matrix in addition to the information about the intrinsics of both cameras so that we can relate the two cameras in pixel coordinates.  
(Note: If we are using rectified images and normalize the point by dividing by the focal lengths, **F=E**).  
This is calculated from matching points from both the images. A minimum of **8 such points(4 pairs)** are required to find the fundamental matrix.  
More points are preferred and use RANSAC(deal with outliers) to get a more robust result.  

The fact that epipolar lines are parallel is what matters. Then being horizontal is a result of the particular stereo setup.  

### Triangulation  
Defination:  
Problem: Given some points x and x’ in correspondence  
across two or more images (taken from calibrated cameras), compute the 3D location X  

### Structure from Motion(SfM)  
[演示-SFM pipeline Video Demo](https://www.youtube.com/watch?v=i7ierVkXYa8)  
SFM Pipeline:  
- Track 2D feautres  
- Estimate 3D  
- Optimize(Bundle adjust)  
- Fit surfaces  

SFM Reconstruction Pipeline:  
- Feature detection  
- Feature matching(Find scene points seen by multiple cameras)  
- Reconstruction(Robustly estimate camera poses and triangulation)  
- Refinement: BA(Refine camera poses R, T and scene structure P)  



### Photometric stereo  
[效果的视频演示](https://www.youtube.com/watch?v=tsLTq3MuXNI)  

## Image segmentation  
Group pixels with similar visual characteristics.  
[Here is the introducation vedio link](https://www.youtube.com/watch?v=4pYyD2uSeko&list=PL2zRqk16wsdop2EatuowXBX5C-r2FdyNt&index=1)  

### Segmentation by humans  
**Segmentation is highly subjective for humans.**
[Here is the vedio link](https://www.youtube.com/watch?v=4pYyD2uSeko&list=PL2zRqk16wsdop2EatuowXBX5C-r2FdyNt&index=2)  
Closer objects are grouped together.  
Similar objects are grouped together.  
Objects with similar motion or change are grouped together.  
Connected objects are grouped together.  
Features on a continuous curve are grouped together.  
Parallel and symmetrical features are grouped together.  
Illusory(幻影的) or subjective contours(轮廓/等高线) are perceived.  

### Segmentation as cluster  
[Here is the vedio link](https://www.youtube.com/watch?v=4pYyD2uSeko&list=PL2zRqk16wsdop2EatuowXBX5C-r2FdyNt&index=3)  
Cluster similar pixels.
Pixels as feature vector:{R,G,B,x,y,depth...}  
Construct feature space: The distance is smaller, the more similarity it is.  

### K-means segmentation  
[Here is the vedio link](https://www.youtube.com/watch?v=4pYyD2uSeko&list=PL2zRqk16wsdop2EatuowXBX5C-r2FdyNt&index=4)  
Goal: Segement the given pixel feature distribution into K clusters.  
Steps:  
- Randomly generate the inital means of the K cluters.  
- Create K clusters by assigning each feature point to the nearest mean.  
- Recompute the means of each cluster.  
- Repeat steps 2 and 3 until convergence.  

### Mean-shift segmentation
[Here is the vedio link](https://www.youtube.com/watch?v=4pYyD2uSeko&list=PL2zRqk16wsdop2EatuowXBX5C-r2FdyNt&index=5)  

### Graph-based segmentation  
[Here is the vedio link](https://www.youtube.com/watch?v=4pYyD2uSeko&list=PL2zRqk16wsdop2EatuowXBX5C-r2FdyNt&index=6)  


## Deep learning  
[MIT-Introduction to Deep Learning](https://www.youtube.com/watch?v=5tvmMX8r_OM&list=PLtBw6njQRU-rwp5__7C0oIVt26ZgjG9NI)  
[Bilibili- Basic concepts and coding for deep learning](https://space.bilibili.com/18161609/video?tid=0&page=2&keyword=&order=pubdate)  
[动手学习深度学习-pytorch版本](https://tangshusen.me/Dive-into-DL-PyTorch/#/)  

### VGG  
[Basic concepts for VGG](https://www.bilibili.com/video/BV1q7411T7Y6)  
[博客文章讲解VGG](https://blog.csdn.net/codeswarrior/article/details/107540780?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162303519416780357261041%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162303519416780357261041&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-107540780.pc_search_result_control_group&utm_term=VGG%E7%BD%91%E7%BB%9C&spm=1018.2226.3001.4187)  
- 使用更小的卷积核可以使网络层数增加，从而可以集成多个非线性激活，而不是原来的一个，这样可以使得决策函数更具有判别力。  
比如，用两个3x3的核替代一个5x5, 用三个3x3的核替代7x7.  
- 参数更少  



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
M = instrinxsic * extrinsic;

% Result(From the world to image plane)
% note: Point in world should be homogeneous
% convert homogeneous to non-homogeneous!!!
Point_image_coordinate = M * Point_World_coordinate; 

end
```

