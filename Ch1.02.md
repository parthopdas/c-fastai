- Learning rate finder
  - plot the loss vs lr -> find lowest, pick 1 order less
  - The point of steepest descent would have resulted in learning quicker, however the selection generalizes better
  - How many times: [a] at least once, [b] post un-freezing for sure [c] changing what/how is being trained

- Data augmentation
  - provide more data to prevent overfit

- PreCompute = true
  - load the weights of the pre-trained network
  - data-augmentation wont work
  - Weights for 1.5M imagenet db works well with similar images. But may need to:
    - Fine tune for the specific case at hand
    - Relearn layer 1 features for dissimilar images

- CycleLength = 1 for SGD w/ restarts
  - LR Annealing => decrease the LR as we get closer to the loss minima
    - Step-wise annealing
    - Cosine annealing
    - Normally
      - it will hit one of the local minima, but won't generalize well i.e. if loss function is slightly different its not the minima anymore
      - if we hit a wider valley, it generalizes better [different data set may have a slightly offset loss vs lr function]
    - w/ restarts
      - cosine annealing, jump up => do enough number of times it hits a valley => eventuall with restart it just stays in the wide valley
      - hence not the steepest point in lr.find - it may be too low and may not jump out when restarted
    - cycle_len = 1 => number of restarts

- Save/Load weights => good idea to do it from time to time

- Differential LR
  - The early layer(s) need little if any learning (e.g. edges are same for icebergs or cats)
  - Later layer probably do
  - Unfreeze & pass LR array - earlier layers have lesser LR
  - Can unfreeze from layer n onwards, not specific layers
  - For images similar to precomputed weights, use 10x lesser for earlier layers, last layer LR from lr.find, for dissimilar images go down by 3x

- cycle_mult => stretches the restart cycle x axis
  - = 2 => doubling length of cycle

- 3 parameters
  - number of cycles
  - number of epochs per cycle
  - cycle_mult

- Test-time Data Augmentation
  - Issue: All inputs to a model have to be a square [GPU needs same dimension for images], e.g. face may not have been seen during validation
  - Make avg predictions for original image + transformations => hopefully in one of images, face is seen

- Confusion matrix for classification problems
  - Useful to see which group you are having most trouble with

- Steps:
  - Initial exploration
  - Build model
    - Enable data augmentation, and precompute=True
    - Use lr_find() to find highest learning rate where loss is still clearly improving
    - Train last layer from precomputed activations for 1-2 epochs
    - Train last layer with data augmentation (i.e. precompute=False) for 2-3 epochs with cycle_len=1
    - Unfreeze all layers
    - Set earlier layers to 3x-10x lower learning rate than next higher layer
    - Use lr_find() again
    - Train full network with cycle_mult=2 until over-fitting
  - Visualize results
  
- To get better results 
  - rerun the training with validation set as well
  -   
  
