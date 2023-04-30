Download Link: https://assignmentchef.com/product/solved-iannwtf-homework-4
<br>



<h1>1      Data set</h1>

We will work with the Tensorflow Malaria dataset <a href="https://www.tensorflow.org/datasets/catalog/malaria">https://www.tensorflow.org/datase</a>ts/ <a href="https://www.tensorflow.org/datasets/catalog/malaria">catalog/malaria</a><a href="https://www.tensorflow.org/datasets/catalog/malaria">.</a> It contains 27.558 coloured images of cells with equal shares of malaria-infected cells and uninfected cells. <sup>1</sup>

Print out some of the images together with their shapes. Do you see a problem here?

Do you have an idea how to solve it?<sup>2</sup>

Perform other necessary or beneficial preprocessing steps.<sup>3</sup>

<h1>2      Model</h1>

Implement a Convolutional Neural Network to classify the cells. Just try to combine some layers and see what happens. If you can’t make anything work, look at the hints.

4 5 6 7 8

<h1>3      Training</h1>

Then train your network. We would like you to just get started and try it yourself. In the hints we put some training hyperparameters for your orientation in case you’re stuck. <sup>9</sup>

For this task, you should reach a test accuracy of 90 – 95%. In the outstanding homeworks we would like to see at least 95% accuracy.

4 Visualization

Visualize accuracy and loss for training and test data using matplotlib.

<h1>Notes</h1>

1

Make sure to load the dataset from tensorflow datasets and not keras. We recommend splitting around 80% for training and taking the rest as test data, but there is not just one right solution here.

2

Problem: the images don’t have the same size, but that would be necessary to feed it into our network. Check the Courseware part on Image Representation in the bottom and choose one of the options provided there. Test afterwards if it worked, by printing some pictures and their shapes.

3 Relevant reprocessing steps:

<ul>

 <li>Shuffling</li>

 <li>Batching, an orientation would be minibatches of size 64. Feel free to also try other batchsizes and see what happens.</li>

 <li>Normalize the images so your network can work with them better. Check Courseware/Image</li>

</ul>

Representation for inspiration.

<ul>

 <li>One-hot-encode the labels. What should be the depth of the resulting labels?</li>

</ul>

4

You probably want to use convolutional layers: tf.keras.layers.Conv2D, kernels of size 3 are always a good choice. The number of filters can vary from something like 20 to over a 100. See what works for you. For activations functions check out ’tf.keras.activations’.

5

For the first layer, you will need to specify the shape of the input to your CNN. use the flag input shape for that.

6

It might be a good idea to alternate convolutional and Max Pooling Layers. Check out: tf.keras.layers.MaxPool2D(pool size=)

7

Use a readout layer. You can decide to reshape your inputs before this read out layer (check out tf.keras.layers.Flatten()) or use global average pooling: tf.keras.layers.GlobalAveragePooling2D()

8

4 convolutional layers should be enough to reach around 90% accuracy. Feel free to build deeper networks but they need longer to train and are more prone to overfitting.

9 Training Hyperparameters for orientation:

<ul>

 <li>epochs: 10 – 25, depending on your architecture you can train even longer as long as the model is not overfitting</li>

 <li>learning rate: should be very small! Try something between 0.00001 and 0.0001.</li>

 <li>optimizer: Adam</li>

 <li>loss: BinaryCrossEntropy. Check keras.losses.BinaryCrossentropy()</li>

 <li>accuracy: how many items in prediction and target are the same (in the batched vectors)? → take the mean of it</li>

</ul>