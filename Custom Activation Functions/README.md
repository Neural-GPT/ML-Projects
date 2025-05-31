## GhostReLU & Pulsar: Two Novel Activation Functions for Neural Networks

Ghost ReLU: A smooth, asymetric activation resembling leaky relu.
formula: f(x) = x * σ(a*tanh(k*x)) , where a and k are trainable parameters, for now the value of k is capped at 1 because I haven't experimented on it. a helps control the slope on both -ve and +ve side of the graph, at a = 1.735 (default), +ve slope max outs at 0.85 and -ve slope max outs at 0.15. Why this happens is because tanh outputs between -1 and 1 and it is inside sigmoid so this acts as domain restriction for sigmoid from (-inf, inf) to (-1.735, 1.735) so range of sigmoid on this  domain is from -0.15 to 0.85 which then scales down the x multiplied to it. At a = 4, it highly resembles leaky relu because +ve slope is nearly 0.97 (1 for leaky relu) and -ve slope is 0.03 (0.018 for leaky relu).

![image](https://github.com/user-attachments/assets/8e9c7e4a-f12e-4846-ae5f-11833b15d462)
![image](https://github.com/user-attachments/assets/1b5f58a3-0730-4c65-b690-684cb2503c8b)
![image](https://github.com/user-attachments/assets/578084c2-c471-4627-837c-6faa33c8913b)

Pulsar: Leaky ReLU with directional gradient push at 0.
formula: f(x): {x for +ve x,
                0.018*x for -ve x,
                +-ε at zero}, 	ε is a very small number (like 0.0001) to barely push the gradient flow towards -ve or +ve axis without introducing noise
 How this works is since at zero slope is kept zero by convention which causes dead neurons, to avoid this we use a very small slope here and assign it the sign 
 with accordance to which direction it was flowing towards. For example if it was converging from -ve values towards zero then we'll introduce gradient such that
 from zero it gets pushed towards the +ve direction and vice versa so that training keeps on going. If the optima is at 0 so it'll converge back to zero despite
 the direction we push it to, if this happens 3 times (or any threshold of your choice), we should keep it at zero for the time being. We have to use the
 gradient history for each neuron to achieve this. What it accomplishes is continued learning at zero along with the computational efficiency of leaky relu or
 prelu.

 ![image](https://github.com/user-attachments/assets/91f5326a-f4f4-4a61-aa91-4f90fc286991)

 ![image](https://github.com/user-attachments/assets/f819bdb0-ee0a-43e0-891e-8a1b9374239c)


Currently I used them both on MNIST data using PyTorch but they couldn't outperform ReLU, which is because the data is very simple and relu's simplicity is more
than enough. They should work well with suitable initializations on more complex tasks like deeper cnn's, transformers and autoencoders which I have yet to learn.
So I'll post updates when I'm done with learning and detailed experimentation. This post was to mark my name as the creator of these activation functions.

My name is Arjun Gupta, you can contact me via email: titanxarestren@gmail.com
Today's date is 31 May 2025, 2.03 PM IST
