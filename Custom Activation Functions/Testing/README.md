### Testing and comparison of Ghost ReLU and Eclipse:

1. RESNET20 CIFAR10: Ghost ReLU gets to 92.03% max test accuracy, Eclipse maxes out at 92.12%. Eclipse surprisingly takes longer (3011) to train than Ghost (2828).
2. ReLU is already a very efficient activation function that serves the purpose of non linearity very good, it wins in practicality so theoretical disadvantages are
   just noise. ReLU family (ReLU, leaky ReLU, PReLU) is still the king of computer vision and mlp tasks.
   
3. I have 3 ideas:
  I.   test ghost and eclipse on complex cnn's where swish family outperforms relu family by a bit: my activations outperform relu and swish and perfrom just before
       gelu and mish, its a win because my activations are expensive then swish but cheaper then gelu and mish
  II.  same with nlp and other complex  tasks
  III. i go to attempt best run possible for resnet20 cifar10 or any other setup and then compare ghost, eclipse, relu, gelu best performance
