---
keywords: fastai
description: An introduction to the world of Deep Learning.
title: Evolution of Artificial Neural Network(ANN) 
nb_path: _notebooks/2020-07-05-Evolution-of-Artificial-Neural-Network(ANN).ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2020-07-05-Evolution-of-Artificial-Neural-Network(ANN).ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Artificial-Intelligence">Artificial Intelligence<a class="anchor-link" href="#Artificial-Intelligence"> </a></h2><p>Artificial intelligence (AI) is a  branch of computer science capable of performing tasks that typically require human intelligence.</p>
<p><img src="https://www.oreilly.com/library/view/deep-learning/9781491924570/assets/dpln_0101.png" alt=""></p>
<h2 id="What-is-Deep-Learning?">What is Deep Learning?<a class="anchor-link" href="#What-is-Deep-Learning?"> </a></h2><blockquote><p>deep learning is a more approachable name for an artificial neural network. The “deep” in deep learning refers to the depth of the network. An artificial neural network can be very shallow.</p>
</blockquote>
<ul>
<li>Machine learning is the science of getting computers to act without being explicitly programmed.</li>
</ul>
<h2 id="ANN:Artificial-Neural-Networks">ANN:Artificial Neural Networks<a class="anchor-link" href="#ANN:Artificial-Neural-Networks"> </a></h2><ul>
<li>ANNs are inspired by biological neurons found in cerebral cortex of our brain.</li>
</ul>
<p><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/Blausen_0657_MultipolarNeuron.png/1200px-Blausen_0657_MultipolarNeuron.png" alt=""></p>
<ul>
<li>A neuron or nerve cell is an electrically excitable cell that communicates with other cells via specialized connections called synapses.</li>
<li>ANNs are <strong>core of deep learning</strong>. Hence one of the most important topic to understand.</li>
</ul>
<h2 id="Perceptron">Perceptron<a class="anchor-link" href="#Perceptron"> </a></h2><p><strong>A Perceptron is one of the simplese ANN architectures, invented in 1957 by Frank Rosenblatt.</strong></p>
<blockquote><p>A perceptron works similar to a biological neuron. A biological neuron receives electrical signals from its <em>dendriles</em>, modulates the electrical signals in various amounts, and then fires an output signal through its <em>synapses</em> only when the total strength of the input signals exceeds a certain threshold. The output is then fed to another neuron, and so forth.</p>
<p>To model the biological phenomenon, the artificial neuron performs two consecutive functions:it calculates the <em>weighted sum</em> of the inputs to represent the totgal strength of the input signals, and it applies a <em>step function</em> to the result to determine whether to fire the ourput 1 if the signal exceeds a certain threshold of 0 if the signal doesn't exceed the threshold.
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/60/ArtificialNeuronModel_english.png/1200px-ArtificialNeuronModel_english.png" alt=""></p>
</blockquote>
<p><strong>How Peceptron Works?</strong></p>
<p>The perceptron's learning logic goes like this:</p>
<ol>
<li>The neuron calculate the weighted sum and applies the activation function to make a prediction y<sup>^</sup>. This is called the feedforward process:</li>
</ol>
<p>{% raw %}
$$y\hat{} =  activation\left(\sum\nolimits x_i \cdot w_i + b\right)$$
{% endraw %}</p>
<ol>
<li>It compares the output prediction with the correct label to calculate the error:</li>
</ol>
<p>{% raw %}
$$error = y-y\hat{}$$
{% endraw %}</p>
<ol>
<li><p>It then update the weight. If the prediction is too high, it adjust the weight to make a lower prediction the next time, and vice versa.</p>
</li>
<li><p>Repeat!</p>
</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Here's how a since perceptron works to classify two classes :</p>
<p><img src="/blog/images/copied_from_nb/pp1.gif" alt=""></p>
<p><strong>Drawback of perceptron.</strong>
Sometimes its not possible to get desired result with only perceptron. In the below example you can see the 
model in not able to draw a line to classify the data(linearly inseperable data)</p>
<p><img src="/blog/images/copied_from_nb/pp2.gif" alt=""></p>
<p><strong>Indroduction of ANN</strong>
If you increase the number of neuron then you cann see model works pretty well. The stack of more than one neuron is called Multi Layer Perceptron or ANN.</p>
<p><img src="/blog/images/copied_from_nb/ann.gif" alt=""></p>
<p><strong>ANN using Keras</strong></p>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">tensorflow</span> <span class="k">as</span> <span class="nn">tf</span>

<span class="c1"># Helper libraries</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras</span> <span class="kn">import</span> <span class="n">initializers</span>
<span class="kn">from</span> <span class="nn">tensorflow.python.keras</span> <span class="kn">import</span> <span class="n">activations</span>

<span class="nb">print</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">__version__</span><span class="p">)</span>

<span class="c1"># downloading fashion_mnist data</span>
<span class="n">fashion_mnist</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">keras</span><span class="o">.</span><span class="n">datasets</span><span class="o">.</span><span class="n">fashion_mnist</span>

<span class="p">(</span><span class="n">train_images</span><span class="p">,</span> <span class="n">train_labels</span><span class="p">),</span> <span class="p">(</span><span class="n">test_images</span><span class="p">,</span> <span class="n">test_labels</span><span class="p">)</span> <span class="o">=</span> <span class="n">fashion_mnist</span><span class="o">.</span><span class="n">load_data</span><span class="p">()</span>

<span class="n">class_names</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;T-shirt/top&#39;</span><span class="p">,</span> <span class="s1">&#39;Trouser&#39;</span><span class="p">,</span> <span class="s1">&#39;Pullover&#39;</span><span class="p">,</span> <span class="s1">&#39;Dress&#39;</span><span class="p">,</span> <span class="s1">&#39;Coat&#39;</span><span class="p">,</span>
               <span class="s1">&#39;Sandal&#39;</span><span class="p">,</span> <span class="s1">&#39;Shirt&#39;</span><span class="p">,</span> <span class="s1">&#39;Sneaker&#39;</span><span class="p">,</span> <span class="s1">&#39;Bag&#39;</span><span class="p">,</span> <span class="s1">&#39;Ankle boot&#39;</span><span class="p">]</span>

<span class="n">train_images</span> <span class="o">=</span> <span class="n">train_images</span> <span class="o">/</span> <span class="mf">255.0</span>

<span class="n">test_images</span> <span class="o">=</span> <span class="n">test_images</span> <span class="o">/</span> <span class="mf">255.0</span> 

<span class="n">activation</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">keras</span><span class="o">.</span><span class="n">activations</span><span class="o">.</span><span class="n">relu</span>

<span class="n">model</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">keras</span><span class="o">.</span><span class="n">Sequential</span><span class="p">([</span>
<span class="n">tf</span><span class="o">.</span><span class="n">keras</span><span class="o">.</span><span class="n">layers</span><span class="o">.</span><span class="n">Flatten</span><span class="p">(</span><span class="n">input_shape</span><span class="o">=</span><span class="p">(</span><span class="mi">28</span><span class="p">,</span> <span class="mi">28</span><span class="p">)),</span>
<span class="n">tf</span><span class="o">.</span><span class="n">keras</span><span class="o">.</span><span class="n">layers</span><span class="o">.</span><span class="n">Dense</span><span class="p">(</span><span class="mi">128</span><span class="p">,</span> <span class="n">activation</span><span class="o">=</span><span class="n">activation</span><span class="p">),</span>
<span class="n">tf</span><span class="o">.</span><span class="n">keras</span><span class="o">.</span><span class="n">layers</span><span class="o">.</span><span class="n">Dense</span><span class="p">(</span><span class="mi">10</span><span class="p">)</span>
<span class="p">])</span>

<span class="n">model</span><span class="o">.</span><span class="n">compile</span><span class="p">(</span><span class="n">optimizer</span><span class="o">=</span><span class="s1">&#39;adam&#39;</span><span class="p">,</span><span class="n">loss</span><span class="o">=</span><span class="n">tf</span><span class="o">.</span><span class="n">keras</span><span class="o">.</span><span class="n">losses</span><span class="o">.</span><span class="n">SparseCategoricalCrossentropy</span><span class="p">(</span><span class="n">from_logits</span><span class="o">=</span><span class="kc">True</span><span class="p">),</span><span class="n">metrics</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;accuracy&#39;</span><span class="p">])</span>

<span class="c1"># model summary</span>
<span class="n">model</span><span class="o">.</span><span class="n">summary</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stderr output_text">
<pre>c:\users\sonu.ramkumar.jha\desktop\experiments\env\lib\site-packages\numpy\_distributor_init.py:30: UserWarning: loaded more than 1 DLL from .libs:
c:\users\sonu.ramkumar.jha\desktop\experiments\env\lib\site-packages\numpy\.libs\libopenblas.GK7GX5KEQ4F6UYO3P26ULGBQYHGQO7J4.gfortran-win_amd64.dll
c:\users\sonu.ramkumar.jha\desktop\experiments\env\lib\site-packages\numpy\.libs\libopenblas.WCDJNK7YVMPZQ2ME2ZZHJJRJ3JIKNDB7.gfortran-win_amd64.dll
  warnings.warn(&#34;loaded more than 1 DLL from .libs:&#34;
</pre>
</div>
</div>

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>2.5.0
Model: &#34;sequential&#34;
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
flatten (Flatten)            (None, 784)               0         
_________________________________________________________________
dense (Dense)                (None, 128)               100480    
_________________________________________________________________
dense_1 (Dense)              (None, 10)                1290      
=================================================================
Total params: 101,770
Trainable params: 101,770
Non-trainable params: 0
_________________________________________________________________
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">model</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">train_images</span><span class="p">,</span> <span class="n">train_labels</span><span class="p">,</span> <span class="n">epochs</span><span class="o">=</span><span class="mi">10</span><span class="p">)</span>

<span class="n">test_loss</span><span class="p">,</span> <span class="n">test_acc</span> <span class="o">=</span> <span class="n">model</span><span class="o">.</span><span class="n">evaluate</span><span class="p">(</span><span class="n">test_images</span><span class="p">,</span>  <span class="n">test_labels</span><span class="p">,</span> <span class="n">verbose</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;test_loss&#39;</span><span class="p">,</span> <span class="n">test_loss</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;test_accuracy&#39;</span><span class="p">,</span> <span class="n">test_acc</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>Epoch 1/10
1875/1875 [==============================] - 4s 2ms/step - loss: 0.5000 - accuracy: 0.8255
Epoch 2/10
1875/1875 [==============================] - 3s 1ms/step - loss: 0.3751 - accuracy: 0.8645
Epoch 3/10
1875/1875 [==============================] - 3s 2ms/step - loss: 0.3388 - accuracy: 0.8773
Epoch 4/10
1875/1875 [==============================] - 3s 2ms/step - loss: 0.3142 - accuracy: 0.8843
Epoch 5/10
1875/1875 [==============================] - 3s 2ms/step - loss: 0.2957 - accuracy: 0.8922
Epoch 6/10
1875/1875 [==============================] - 3s 2ms/step - loss: 0.2797 - accuracy: 0.8971
Epoch 7/10
1875/1875 [==============================] - 3s 2ms/step - loss: 0.2685 - accuracy: 0.8991
Epoch 8/10
1875/1875 [==============================] - 3s 1ms/step - loss: 0.2577 - accuracy: 0.9028
Epoch 9/10
1875/1875 [==============================] - 3s 1ms/step - loss: 0.2476 - accuracy: 0.9076
Epoch 10/10
1875/1875 [==============================] - 3s 1ms/step - loss: 0.2388 - accuracy: 0.9105
313/313 - 0s - loss: 0.3403 - accuracy: 0.8798
test_loss 0.34025073051452637
test_accuracy 0.879800021648407
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

</div>
 
