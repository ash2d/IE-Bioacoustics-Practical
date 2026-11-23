# Ideas for improving the models

## 01_supervised.ipynb

**Data augmentation**. Apply random transformations to each spectrogram during training, such as shifting it in time, masking out a few frequency bands or time frames (as in SpecAugment), or adding background noise. Because the model sees a slightly different version of each clip every epoch, it is encouraged to learn features of the bird call that are invariant to these changes, rather than overfitting to the small set of training clips.

**Batch normalisation, max pooling and dropout**. Batch normalisation normalises the activations of each layer over the mini-batch, which tends to stabilise and speed up training. Max pooling downsamples each feature map by keeping the strongest response in each local patch, making the model less sensitive to small shifts of a call in time or frequency. Dropout randomly zeroes a fraction of the inputs to the final layer during training, which discourages the model from relying on a small number of features and acts as a regulariser. All three can (but won't necessarily) improve generalisation to unseen clips.

## 02_autoencoder.ipynb

**Unfreeze the encoder**. Currently the encoder is frozen after being trained for reconstruction, and only the classifier head is trained on the labels. Fine-tuning the encoder and head jointly on the labelled clips, with a lower learning rate for the encoder, allows the supervised signal to adapt the representation towards discriminating between species, while retaining what was learned from the unlabelled data.

**Class-weighted loss**. The labelled set is imbalanced, with many more wrens than robins, so a model trained with a standard cross-entropy loss is biased towards predicting the majority class. Weighting the loss for each class, for example by inverse class frequency, increases the penalty for errors on under-represented species and counteracts this bias. The same approach can be applied in the supervised notebook.
