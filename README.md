# Face-Classification-and-Verification-using-CNNs
Face Classification &amp; Verification using Convolutional Neural Networks


In this homework we work on pattern recognition problems that require position invariance. Specifically we will work on the problem of recognizing or verifying faces in images.

In typical pictures of faces, the face is rarely perfectly centered. Different pictures of the same person may have the face shifted by varying amounts. The classifier must recognize the face regardless of this indeterminacy of position. This calls for position-invariant models,
specifically Convolutional Neural Networks, or CNNs.
 
A CNN is a neural network that derives representations (or embeddings) of input images that are expected to be invariant to the precise positions of the patterns in it. These embeddings are subsequently classified by downstream classifiers (which may just be an additional softmax layer, or even an MLP, appended after the convolutional layers), to achieve position-invariant pattern recognition.
We will consider two kinds of problems in this setting.

<ins>Classification</ins>: Here, we attempt to identify the person in a picture. This is a closed set problem, where the subjects in the test set have also been seen in the training set, although the precise pictures in the test set will not be in the training set. For this to achieve high accuracy it is only required that the embeddings for (all pictures of) the subjects in our “vocabulary” be linearly separable from each other.

![2_1](https://user-images.githubusercontent.com/92863991/212869944-8d836194-1049-430c-8b6a-f2979df14034.png)



<ins>Verification</ins>: Here, we attempt to only determine if the person in a given “query” picture is also present in a given gallery of images or not, with no reference to their identity. This is a open set problem, where the subjects in the test data may not have been seen during training at all. In order to solve this problem we will require that the embeddings of two pictures of the same person are always closer than those from pictures of two different people. With such embeddings, in order to solve the gallery problem we must only determine if the embedding of any of the pictures in the gallery is sufficiently close to that of the query.

![2_2](https://user-images.githubusercontent.com/92863991/212869989-73623f67-d404-42ad-afb6-98495e04ed96.png)



<ins> Dataset </ins>: Subset of the VGGFace2 dataset

This dataset is very widely known and used in research and industry. Images are downloaded from Google Image Search and have large variations in pose, age, illumination, ethnicity, and profession (e.g., actors, athletes, politicians).

The dataset was collected with three goals in mind:
1. To have a large number of both identities and images per identity.
2. To cover a large range of pose, age, and ethnicity.
3. To minimize the label noise.

The classification dataset consists of 7,000 identities. The verification dataset consists of 1000 identities. The dataset has been class-balanced, so each class has the equal number of training images, and all the images are resized to 224 x 224 pixels.

To summarize, this assignment contains 2 parts:

• For classification, you will be given an image of a human face. What you need to do is to learn to classify this image with the correct face identity from 7000 identities.

• For verification, you will have 1000 unknown identity images (split into dev and test) and they need to be mapped one of the 1000 known identities. For the dev-set, you will be given 200 unknown identities and you will be expected to find known identities (out of 1000 known identities) that these unknown identities map to. For these dev images you will also be given the identity label of the image that it maps to in the known images. Similarly, for the test set you will have 800 unknown identities that would need to be mappped to their corresponding known identities, except you will not know what identity it maps to. Note: It is not a one to one mapping, that is the unknown images don’t map to a unique image in the known folder.
