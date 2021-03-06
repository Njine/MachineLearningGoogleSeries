################
# Instructions #

This is where we train a neural network from an image database for the first time. It is inspired by the codelab called "TensorFlow for Poets" (https://codelabs.developers.google.com/codelabs/tensorflow-for-poets/)

We use Google's Inception pre-trained model in order to train just the second to last "column" of our neural network so it can recognize between 5 types of flowers (daisy, dandelion, roses, sunflower and tulips).


Step 1 - Download and extract the flower training images

1) Download the flower training data: http://download.tensorflow.org/example_images/flower_photos.tgz
2) Extract the .tgz file. A folder called "flower_photos", containing the training images will be created.
3) Put that folder under recipe_6 (recipe_6/flower_photos)


Step 2 - Download TensorFlow's pre-trained models

1) cd ml_google/recipe_6
2) git clone https://github.com/tensorflow/models.git
3) python3 models/tutorials/image/imagenet/classify_image.py (this will download the inception model)


Step 3 - Run retrain.py which will perform the training and return the output_graph and the output_labels

python3 image_retraining/retrain.py \
--bottleneck_dir=bottlenecks \
--how_many_training_steps 500 \
--model_dir=models/inception \
--output_graph=trained_images_outputs/retrained_graph.pb \
--output_labels=trained_images_outputs/retrained_labels.txt \
--image_dir flower_photos


Step 4 - Run recipe_6.1.py in order to predict the test flowers contained in the flower_test_set folder.

I tried to vary the test dataset by including, for each type of flower:
1) A picture of a single flower (suffix _1)
2) A picture of a bunch of flowers (suffix _2)
3) A cartoon-like (or drawing) image (suffix _3)
4) A random picture which I figured would be hard for the classifier to get it right. (suffix _4)
