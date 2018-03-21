- tmux - https://github.com/reshamas/fastai_deeplearn_part1/blob/master/tools/tmux.md
- Quick summary - https://medium.com/@apiltamang/case-study-a-world-class-image-classifier-for-dogs-and-cats-err-anything-9cf39ee4690e
- fastai on pytorch, keras on {tensorflow, cntk, ...}
- quick d vs c
- what are jeremy's tricks
  - lrfinder, 
  - SGD with restarts
  - TTA
  - learning groups for differential learning rates
- Submit tricks
- *Individual Prediction: 40:00
- Summarize whale/galaxy zoo/jeremy
- How does CNN prediction work: 43:00
  - convolution, relu - activation function, maxpool (non-overlapping), next layer (tensor filter), fully connected layer, softmax - activation function 
  - activation == calculated number
  - filter == kernel
  - scalar 0, vector 1, matrix 2, tensor 3+ 
- 1 hot encoded vector
- Single label classification vs multi label classification
- Personality of activation functions
  - relu - 0 or positive
  - softmax - it wants to pick a thing [single label classification]
  - sigmoid - can model probability [multi label classification]
- metrics != loss function
  - confusion matrix
  - custom metrics
  - f2
- differential learning rates - settings depend on how close the dataset is to imagenet/pre-trained weights.
- training cnn => learns filters + fully connected layer weights
- visualize model - learn.summary()


TODO:
- Planet dataset
  - Individual prediction
- Galaxy zoo
  - Individual prediction
- 5 kaggle papers
  - summary of tricks

