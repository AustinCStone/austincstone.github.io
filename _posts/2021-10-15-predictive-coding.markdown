---
layout: post
title:  "Is predictive coding more biologically plausible than gradient descent?"
date:   2021-09-21 14:10:01 -0700
categories: jekyll update
published: false
---

[Predictive Coding][predictive-coding-main] is presented as a "biologically plausible" learning algorithm for neural nets. Several papers have come out showing that predictive coding can be applied to increasingly less toy-like problems (such as CIFAR100), and that it produces results equivalent to gradient descent. Recent papers have also proven that predictive coding will update the weights in exactly the same way as gradient descent in the limit of infinite "inference steps."

After looking at some of these works, it wasn't immediately clear to me how predictive coding differs from backpropagation and exactly what the advantages of predictive coding are in terms of biological plausibility. In order to better understand this, I wrote as simple as possible implementation of a feed-forward, fully connected net using predictive coding and using gradient descent, side by side. You can find my [colab implementation here][colab].

Currently I'm actually not convinced the proposed implementations of predictive coding offer much in terms of biological plausibility over backpropagation. If you look at my implementation and the original paper, you will see both require computing (TODO: insert equation) the derivative of activations of a layer with respect to that layer's input, and passing that gradient information along to the parent. This is what is done in the implementation from "Predictive coding approximates backprop along arbitrary computation graphs" here, and what is described in "An Approximation of the Error Backpropagation Algorithm in a Predictive Coding Network with Local Hebbian Synaptic Plasticity."

I think predictive coding does give the advantage of being "asynchronous" and is perhaps more robust to inter neuron communication noise than gradient descent. Predictive coding involves iteratively updating each neuron's local "error" to gradually minimize the a global "free energy" function. Each neuron can run "error propagation" at different times and different rates, whereas SGD assumes that each node backpropagates an error synchronously. If you add gaussian noise to the signals sent back and forth between the neurons, predictive coding is still able to learn in the presence of large channel noise (you can see this in my colab). That being said, the mechanism which allows for this is pretty obvious: predictive coding performs an inner loop where each neuron repeatedly and gradually updates its internal "error" until it has converged. Gradient descent could be also be very robust to channel noise too if you did one hundred backward passes and set the gradient on each layer to the average across all the passes.


# Why Backprop is Biologically Implausible

There are several proposed reasons why backprop can't be implemented by biologically neurons, as least as neurons are currently understood. These three problems are:

* Backprop requires symmetric weights.
During a forward pass, the weights used to send an activation forward are the same as the weights needed to send a signal backward. Some believe that this is implausible, since biological neurons communicate with one-way channels (TODO) and we can observe that neurons generally don't have symmetric forward and backward connections.

* Backprop requires computing derivatives
The argument is there isn't a clear biological mechanism for how this could happen. As mentioned above, derivatives are still computed in predictive coding. In the (TODO insert link) original paper, they propose activation-derivative nodes whose sole purpose is to compute (TODO:) d/activation / d pre-activation. Of course, one could introduce these to backprop as well.

* Biological Neurons use discrete spikes
This is again equivalentally a problem for both PC and SGD. Some evidence indicates that neurons simply rate encode information in their spikes; maybe modeling activations as floating point numbers is similar to looking at the rate activations across a fixed chunk of time, making this a non-problem.

* SGD requires batch-training
I've sometimes heard this raised as a problem; in the real world we seem to get one example at a time instead of a diverse batch of examples all at once. This is equivalently a problem for the proposed implementation of SGD and Predictive coding. There is some evidence that the brain (TODO) replays experiences after a while in order to learn from them, maybe presenting a solution to this problem. Another possible objection to this problem is that neural nets can actually learn from individual examples, it just takes much longer and requires a much lower learning rate.

* Timing problem
SGD requires explicit timing coordination between all the neurons during the backward pass and weight update. This seems like one problem which predictive coding really does address. The weight updates and error propagation could all happen asynrhonously in predictive coding. While I haven't explicitly worked it out, I do think that one could implement a similar version of "asynchronous SGD" by simply having each neuron store a moving average of the gradient's it receives, and asynchronously updating its weights in the direction of its gradient every so often. 


\\( a^2 = b^2 \\)


Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[predictive-coding-backprop-1]: [https://www.mrcbndu.ox.ac.uk/sites/default/files/pdf_files/Whittington%20Bogacz%202017_Neural%20Comput.pdf]
[predictive-coding-backprop-2]: [https://arxiv.org/abs/2006.04182]
[predictive-coding-main]: https://en.wikipedia.org/wiki/Predictive_coding
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[colab]: https://colab.research.google.com/drive/1YgXwC36PCrVR0jmZvmTictHBLLNIcCjp?usp=sharing
