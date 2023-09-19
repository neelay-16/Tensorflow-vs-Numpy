# Tensorflow-vs-Numpy

So,starting from the very basic,right from the evolution of using lists,transforming into numpy arrays and finally we are in the world of tensorflow.
The evolution of transferring from lists to numpy arrays lies in the reason that,lists do not support column wise operations on a matrix,which generates the need of numpy array. 
Similarly,there is something that numpy won't support that is being resolved by tensorflow.
But,here is a twist.
Let me explain it:

By reading the above lines,it may seem that some feature was not available in numpy which made us to trasnform to using tensorflow. But,this is not completely true.
The twist lies in the fact that,internally in tensorflow,the data structure used to store the data is "numpy".
When we store a data using tensorflow,let's say as a constant or as a variable and when we try to retrieve the data using the constant name or the variable name,python tells us that though you are using tensorflow,the data which you want to store,internally it stores in the form of numpy only.
Have a look over here - 

![image](https://github.com/neelay-16/Tensorflow-vs-Numpy/assets/135517502/0549de5b-1aec-4b0c-999e-62c5a042a636)


This shows that though it may look that tensorflow and numpy may be rivals,but internally they are dependent on each other.
Now the question arises that if tensorflow using numpy internally,then what is the use of using this new python library again?
The answer lies in the purpose they serve.
Let me explain it:

To explain this we need to understand 2 more things i.e Eager Execution and Lazy Execution.
Eager Execution : Eager execution is a feature that allows operations to be evaluated immediately, enabling a more intuitive and interactive way of building and debugging our code by computing operations immediately as we run the code. Which is very normal as we mostly do in any coding:

![image](https://github.com/neelay-16/Tensorflow-vs-Numpy/assets/135517502/5a29c016-650a-4c13-b52e-d7f726ebd8fc)

Lazy Execution : Lazy execution, in any programming, refers the evaluation of code until it's explicitly needed. It optimizes resource usage by only computing results when required, enhancing efficiency in tasks like data processing and functional programming. Which is not very normal. Here we just store the expression in the form of a graph but we dont evaluate the expression until and unless we need it in the code.
Taking the same example as above:

![image](https://github.com/neelay-16/Tensorflow-vs-Numpy/assets/135517502/78c0cef9-bac5-47d7-ab8f-5c3f6e2bc98b)

You can see that using "@tf.function" we implement lazy execution.When we call the bm() function,python shows us that it has stored the expression as "mul_1:0" telling us that some multiplication expression is stored but is not evaluated. We did not get the answer of the expression.
In fact,lazy execution creates a graph internally to store the expression. A rough graph may be like:

![lazy execution](https://github.com/neelay-16/Tensorflow-vs-Numpy/assets/135517502/7dc00921-a326-4f49-9477-541c27bf5405)

This the reason why we need tensorflow.
There is a very popular misconception about numpy that it cannot handle n*n matrix,but its not true. We can store n*n matrix in numpy as well as tensorflow,just the difference is about the lazy execution. 

Note that the example screenshots placed above are very simple example. But the main purpose of these concepts play a major role when there are huge matrices of n*n matrix where we perform the operations on them. 

Another reason of using tensorflow is about the Distributed Computing:
Distributed computing is a paradigm in which multiple computers work together to solve a complex task, often by dividing it into smaller sub-tasks that are processed concurrently. This approach enhances performance, scalability, and fault tolerance in computing systems.
In this technique,when we have a very huge amount of data in complex form which can reduce the performance of a single system,so we distribute the functions performed by our code so that the huge amount of data is being distributed and these systems output when combined give us the perfect desired output. The systems to be used can be of any O.S,any RAM,any IP just the thing to focus on is that all these systems should work towards one specific goal. A rough figure of  Distributed Computing can be visualized as:

![Distributed Computing](https://github.com/neelay-16/Tensorflow-vs-Numpy/assets/135517502/7f5fe372-7067-48fb-aef4-101878d05e40)



