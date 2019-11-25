# 如何在建好TF图后修改图

网上大部分教程都说tensorflow的图建好后是不能修改的，但是实际上是可以的。

## Operation._update_input()函数
```python
op._update_input(i, new_tensor)
```
此函数的作用是将op的第i个输入变成new_tensor。

下面的例子是用该函数将mul op的输入从b变成c。
```python
import tensorflow as tf
import os

def SaveGraph(tb_dir, sess):
    if not os.path.exists(tb_dir):
    os.makedirs(tb_dir)
    g = sess.graph
    writer = tf.summary.FileWriter(tb_dir)
    writer.add_graph(g)
  
    
a = tf.placeholder(shape=[], dtype=tf.float32, name='a')
b = tf.placeholder(shape=[], dtype=tf.float32, name='b')
c = tf.placeholder(shape=[], dtype=tf.float32, name='c')
  
d = a*b

# save graph
sess = tf.Session()
SaveGraph('tensorboard/before/', sess)

# reroute operation mul
op = b.consumers()[0]#<op here is the mul operation of d>
op._update_input(1, c)#<update the first input of op with c>

# save new graph
SaveGraph('tensorboard/after/', sess)
```

在28行图建好后，tensorboard中的图如下所示：
