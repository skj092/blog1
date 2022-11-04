---
keywords: fastai
description: An introduction to the world of Deep Learning.
title: Object Detection
nb_path: _notebooks/2022-06-16-Object-Detection.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2022-06-16-Object-Detection.ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Object detection is a computer vision task that involves two tasks:</p>
<ol>
<li>Localizing one or more objects within an image, and </li>
<li>Classifying each object in the image</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="YOLO">YOLO<a class="anchor-link" href="#YOLO"> </a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>YOLO is a family of object detection networks that improved over the years throught the following version; YOLOv1, YOLOv2, YOLOv3 and YOLOv4. The YOLO family of models is a series of end-to-end deep learning models designed for fast object detection, developed by Joseph Redmon, etal. Thought is is no longer the most accurate object detection algorithms, it is a very good choice when you need real-time detection, withoug loss of too much accuracy.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>How it works</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>YOLO first generate potential bounding boxes in an image and then run a classifier on these proposed boxes. 
After classification, post-processsing is used to refine the bounding boxes, eliminate duplicate detctions and rescore the bxes based on other 
objects in the scene.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Step1: It divides image into SxS grid cells.</p>
<p><img src="/blog/images/copied_from_nb/../images/od1.PNG" alt=""></p>
<p>Step2: Each cell will generate B objects and produce the output in the format. (tx, ty, tw, th, po) + number of classes with score.</p>
<p><img src="/blog/images/copied_from_nb/../images/od2.PNG" alt=""></p>
<p>Step3: If we are trying to detect dog and cat (i.e. class=2) and B = 1 then the 1st grid cell will produce center coordinate of grid cell, width and height (randomly generated) of 1 image and the objectness score which should be close to zero as there is no center of object in 1st grid. And class score of dog and cat.</p>
<p>Step4: Similarly the centered cell (heighlighted in red) will produce output (x,y) - center of the cell, (w, h) - width and height of dog highlighted in yellow and conditional probability of dog and cat.</p>
<p>Step5: Note: Except to width and height of images, will be generated randomly so except for the values of (tx, ty) all the remaining value will be random and incorrect.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Training</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li>When we start training the algorithm we pass image as well as the co-ordinate of objects in the format (x, y, w, h) where (x, y) represent center of each object and (w, h) is the width and height of objects. </li>
<li>In the first step model will take the image and product co-ordinate of each cell along with width and height of object, objectness score and class score. </li>
<li>These values will get compared with the original values and with each iteration model will improve all the values and train the networl.</li>
</ul>

</div>
</div>
</div>
</div>
 
