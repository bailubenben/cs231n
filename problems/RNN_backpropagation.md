in the file rnn_layers.py, when implement the function rnn_step_backward, it involves to 
compute **np.tanh's derivative**. 

originally, i tried to use

        tan(x)' = 1 / cos(x) ** 2
when run Vanilla RNN: step backward, the output was as following:

        dx error:  4.68073056857e-10
        dprev_h error:  2.46403461944e-10
        dWx error:  7.09199180589e-10
        dWh error:  5.03429305235e-10
        db error:  7.30192291439e-11
however when going down to run Overfit small data, the warnings came up:

        (Iteration 1 / 100) loss: 76.913487
        (Iteration 11 / 100) loss: 21.063424
        (Iteration 21 / 100) loss: 4.016050
        (Iteration 31 / 100) loss: 0.566892
        (Iteration 41 / 100) loss: 0.239450
        (Iteration 51 / 100) loss: 0.162021
        (Iteration 61 / 100) loss: 0.111553
        (Iteration 71 / 100) loss: 0.097595
        (Iteration 81 / 100) loss: 0.099114
        (Iteration 91 / 100) loss: 0.073982
        /home/yoyo/cs231/cs231_environments/assignment3/cs231n/rnn_layers.py:70: RuntimeWarning: overflow encountered in             square dtanh = 1 / (np.cosh(prev_h.dot(Wh) + x.dot(Wx) + b) ** 2)
  
firstly, i thought the problem existed because denominator was possible to be close to zeros. i considered to add some small 
constant, eps, for numeric stability. but i don't know when to add. So i chose to ignore the problem. 

when i finished RNN_Captioning and tried to read the blog  http://karpathy.github.io/2015/05/21/rnn-effectiveness/, i found 
in the code https://gist.github.com/karpathy/d4dee566867f8291f086 that the computation about tan's derivative was different 
from mine. so i changed to use dtanh = 1 - np.tanh(prev_h.dot(Wh) + x.dot(Wx) + b) ** 2

everying is normal:
when run Vanilla RNN: step backward, the output was as following:

    dx error:  4.68073970133e-10
    dprev_h error:  2.46403217135e-10
    dWx error:  7.0920202156e-10
    dWh error:  5.03426517319e-10
    db error:  7.30162216654e-11
when run Overfit small data, the output was:

    (Iteration 1 / 100) loss: 76.913487
    (Iteration 11 / 100) loss: 21.063403
    (Iteration 21 / 100) loss: 4.016044
    (Iteration 31 / 100) loss: 0.566888
    (Iteration 41 / 100) loss: 0.239451
    (Iteration 51 / 100) loss: 0.162019
    (Iteration 61 / 100) loss: 0.111553
    (Iteration 71 / 100) loss: 0.097594
    (Iteration 81 / 100) loss: 0.099114
    (Iteration 91 / 100) loss: 0.073982
  
from the derivative of sine：
  （http://math2.org/math/derivatives/more/trig.htm#cos）
  
From the derivative of ex：
  （http://math2.org/math/derivatives/more/hyperbolics.htm）

in machine learning, tan's derivative uses the latter
