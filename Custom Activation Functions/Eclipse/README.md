## Eclipse: Ghost ReLU's Evil Twin born during Eclipse

Eclipse: f(x) = x*sigmoid(a*gammoid(x)) , where a is a trainable parameter initialized to 1.735 just like in Ghost ReLU, gammoid is a squisher function replacing
tanh, gammoid(x) = x/(1+|x|)

Just like tanh, gammoid also squishes input to range (-1,1) but much more computationally efficient.

![image](https://github.com/user-attachments/assets/fd66874f-7a9c-41b1-9062-a48555fc68f7)

![image](https://github.com/user-attachments/assets/cf68c9f0-ff61-4b73-aafe-1b1ca47b38bc)

Though I plotted it today, I had theorized it on 31 May 2025. Today is 7 June 2025 1.51 PM IST. I also plotted some other gammoid variants which you can see in the
jupyter notebook provided

![image](https://github.com/user-attachments/assets/7b80de2f-a5c7-43fe-bda6-5a1efb945ac7)
