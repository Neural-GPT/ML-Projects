## Neutron Activation Function
Formula: f(x) = (x*a^x)/(1+a^x) , where a is any real number from (1,inf) but typically from [1.1,e] and controls the local maxima on the -ve side of the graph
which makes the function non-monotonic just like gelu, swish and mish. 

![image](https://github.com/user-attachments/assets/585a98ac-425c-42c5-a5f1-f075c74cda5e)

It's original formula was: f(x) = x*e^x * sigmoid(-x), I chose exponential due to it's non-monotonic left bump resembling that of gelu. Sigmoid(-x) controls the +ve
explosion due to exponential so it becomes linear at large x. I simplified it's formula and made it more flexible.

It's gradient graph: 

![image](https://github.com/user-attachments/assets/29a13fe7-b788-457c-b639-5d56ea2ddb77)

Notice the zero gradient around -10, it's the point of local maxima due to the non-monotonic bump, and the zero gradient there is evident in gelu, swish and mish 
as well. In neutron it can be placed flexibly by chamging value of "a" thus increasing or decreasing the effective learning zone for the neural network. Increasing
"a" reduces the learning zone and vice versa. The zero gradient at local maxima means learning can't be resumed beyond it, this is the price we pay for the 
beautiful non-monotonic activation functions. flexibibly changing "a" in Neutron offers a solution to this problem, another solution is Pulsar like push at zero 
gradient to push it into the negative gradient zone beyond the local maxima or placing a small non-zero +ve gradient instead of 0, althoguh this might lead to 
unstable effects as it's not tested.


### Update: after the [bitter truth](https://github.com/Neural-GPT/ML-Projects/tree/main/Custom%20Activation%20Functions/Bitter%20Truth) :
Neutron is changed to Atomic Swish: f(x) = k * X * Sigmoid_a(b * X) , where 'a' is the base in sigmoid. k, a & b are learnable parameters in fixed range, 
k -> [0.95, 1.05], b -> [0.5, 4], 4 because sigmoid significantly flattens around x = +-5, a -> [1.05, 4]. (29 June 2025)
