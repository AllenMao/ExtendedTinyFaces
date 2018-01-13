# ExtendedTinyFaces
Analysis, review and application of the Finding Tiny Faces (P. Hu) paper [1] with a focus on counting people.

### Introduction
The paper - released at CVPR 2017 - deals with finding small objects (particularly faces in our case) in an image, 
based on scale-specific detectors by using features defined over single (deep) feature hierarchy : 
Scale Invariance, Image resolution, Contextual reasoning. The algorithm is based on foveal descriptors, i.e blurring the peripheral image to encode and give just enough 
information about the context, mimicking the human vision.   
The subject is still an open challenge and we would like to enlarge it to new horizons and 
experiment this ap- proach to different applications. The goal would be to deeply understand 
the choices of the paper, together with their applications on subjects related to security and identification.  
<img src="https://github.com/alexattia/ExtendedTinyFaces/blob/master/data/92_TinyFaces.png" height="320">

### Face detection benchmark
First, we aim at comparing the Tiny Faces algorithm with other face detection models.  
We use two particular sub-folders of the WIDERFACE dataset (*Parade*  and *Dresses*) to compare our model with Faster R-CNN for face detection (using [MXNet](https://github.com/tornadomeet/mxnet-face), MTCNN[6] (using [MXNET](https://github.com/pangyupo/mxnet_mtcnn_face_detection)),  Haar Cascade[2] and HOG[3].  
This benchmark could be find in this [notebook](https://github.com/alexattia/ExtendedTinyFaces/blob/master/Face%20Detection%20algorithms%20comparison.ipynb)
![Benchmark](https://github.com/alexattia/ExtendedTinyFaces/blob/master/data/benchmark.png)

### Image resolution influence
The performance of the Tiny Faces algorithm is linked to the image resolution. This parameter really affects the face detection as explained in the original paper. We used the inference part and plotted the variation of detected faces while downscaling the image resolution.  
<img src="https://github.com/alexattia/ExtendedTinyFaces/blob/master/data/Downscale_graph.png" height="270"> <img src="https://github.com/alexattia/ExtendedTinyFaces/blob/master/data/Downscaling.png" height="270">

### Face Recognition
Other applications of the paper would be for face recognition. 
Indeed, we aim at building a Python pipeline for face recognition. 
We would like to use face alignment[4] and face embedding[5] to achieve face classification.   
The first application, we would like to explore include : counting the many different faces 
(numerous people displayed with different size in the picture) in a video of a crowded public demonstration.   
This application could be find in this 
[notebook](https://github.com/alexattia/ExtendedTinyFaces/blob/master/Counting%20in%20video.ipynb).  
For this, we have to match people from one frame to another in order to count the same people only once. The matching is achievied with face recognition and we count people with face detection. We used a linear SVM for the face classificaton.
![alt-text-1](https://github.com/alexattia/ExtendedTinyFaces/blob/master/data/TotalIncrementalCount.gif)

### References 
[[1]](https://arxiv.org/abs/1612.04402) Peiyun Hu and Deva Ramanan. Finding Tiny Faces. 2017.  
[[2]](https://www.cs.cmu.edu/~efros/courses/LBMV07/Papers/viola-cvpr-01.pdf) P. Viola and M. Jones. Rapid object detection using a boosted cascade of simple features. 2001.  
[[3]](http://lear.inrialpes.fr/people/triggs/pubs/Dalal-cvpr05.pdf) Navneet Dalal and Bill Triggs. Histograms of Oriented Gradients for Human Detection. 2005.  
[[4]](https://pdfs.semanticscholar.org/d78b/6a5b0dcaa81b1faea5fb0000045a62513567.pdf) Vahid Kazemi and Josephine Sullivan. One Millisecond Face Alignment with an Ensemble of Regression Trees  
[[5]](https://arxiv.org/abs/1503.03832) Florian Schroff, Dmitry Kalenichenko and James Philbin. FaceNet: A Unified Embedding for Face Recognition and Clustering. 2015  
[[6]](https://arxiv.org/abs/1604.02878)Kaipeng Zhang, Zhanpeng Zhang, Zhifeng Li, Yu Qiao. Joint Face Detection and Alignment using Multi-task Cascaded Convolutional Networks

