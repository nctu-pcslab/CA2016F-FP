<h1> NCTU IEE 2016 Fall </br> Computer Architecture Final Project </h1>

Part-I: Use CUDA to accelerate the operations of a typical convolutional layer in often-used large-scale neural networks. (You can find the description slides [here](https://docs.google.com/presentation/d/1uYAh4sU3ZA39zQfRGr596CdbRKgjEh4FnfDEz4eQwuU/edit?usp=sharing)) </br>
Part-II: Accelerate a sparse convolutional layer with CUDA. (You can find the description slides [here](https://docs.google.com/presentation/d/1XkgoowAUo4Ml5EyLstSpO9aO6wPK9HeHQ5VjkjblwiI/edit#slide=id.p))
## Three sub-directory
### ./data
This directory contains the input data for the base program
* /data/filt.txt - Store the values of filters
* /data/filt.coo - Store the values of filters in COO format
* /data/inNeu.txt - Store the values of input neurons
* /data/inNeu.coo - Store the values of input neurons in COO format

### ./innerProduct
This is the example to show you how to use CUDA to accelerate Inner Product
#### Usage
    
    cd ./innerProduct
    make
    make run
    
### ./device
The program under this directory can show the device information
#### Usage
    
    cd ./device
    make
    make run
    
## Usage of the base program
### Get the code and data for part-II into a new branch

    git checkout -t origin/part2

### Compile the code

    make
    
### Run the code

    make run
## Task
* Put the input data in sparse format and reimplement your CUDA kernels
* Use NVIDIA Visual Profiler to analyze and improve your code
* Optimize your CUDA kernels for the sparse format
* Improve the input data format (like using other sparse format rather than COO)

## Evaluation
* convLayerCPU() will do the computation with C++ and store the output in the outCPU
* checker() will check whether the values stored in outCPU and outGPU are the same
    * Store your result in the outGPU in dense format
    * You must pass the checking to ensure your result is correct!
* Use nvvp (or nvprof) to measure the kernel execution time and data transfer time 
* TA will use TotalExecTime to evaluate your preformance

        DataTransTime = DataHostToDeviceTime + DataDeviceToHostTime
        TotalExecTime = GPUKernelsExecTime + DataTransTime
        
## Grading Policy
* Completeness (30%)
    * Your result is correct (Pass the check) - 5%
    * You get speedup compared to convLayerCPU() - 5%
    * You use NVIDIA Visual Profiler (NVVP) to help you - 5%
    * You utilize the sparsity in either Neurons or Filters - 5%
    * Improve the input data format (like using other sparse format rather than COO) - 10%
* Performance Ranking (30%)
    * TA will rank your TotalExecTime on the provided server
    * The fastest one will get 30% and the last one will get 1%
* Report (40%)
    * Description of your implementation and results - 5%
    * Show how NVVP help you find and solve perf. issues - 5%
    * Discussion on your optimizations and innovations - 20%
    * Comparison between part-I - 5%
    * Feedback of this project - 5%

## Other Rules
* It’s team work, 1 ~ 3 people in one team
    * Same team members as [part-I](https://docs.google.com/spreadsheets/d/1o-Tpq2UEE8jDqwkoMaVHfYQvgkfbu5n_KWtzuctjJ7c/edit?usp=sharing)
* Compress your code and report into one zip file and upload to E3
    * Name your package as: LeaderID_FP2.zip
    * One team only need to upload one package to E3
    * Please name your report as: LeaderID_Report_FP2.pdf
    * Make sure TA can compile and run your code on the provided server
* Any CUDA library is forbidden to use in this project
* Delay is NOT acceptable
* Any plagiarism will make you get zero point


## Useful Reference
### Part-I
* LeNet: [Gradient Based Learning Applied to Document Recognition](http://vision.stanford.edu/cs598_spring07/papers/Lecun98.pdf)
* AlexNet: [ImageNet Classification with Deep Convolutional Neural Networks](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)
* CNN: [Standford CS231n Convolutional Neural Networks for Visual Recognition](http://cs231n.github.io/convolutional-networks/)
* CUDA Tutorial: [CUDA C/C++ Basics](http://www.nvidia.com/docs/io/116711/sc11-cuda-c-basics.pdf)
* CNN with CUDA: [Optimizing Convolution Operations in CUDA with Adaptive Tiling convolution on gpu](http://www.few.vu.nl/~bwn200/papers/werkhoven-a4mmc2011.pdf)
* GPU Profiling: [GPU Performance Analysis and Optimisation](http://people.maths.ox.ac.uk/gilesm/cuda/lecs/NV_Profiling_lowres.pdf)
* GPU Profiling: [CUDA Profiling Documentation](http://docs.nvidia.com/cuda/profiler-users-guide/index.html#axzz4PPDcxdt6)

### Part-II
* Network pruning: [Learning both Weights and Connections for Efficient Neural Networks](https://arxiv.org/pdf/1506.02626.pdf)
* Sparsity in Neurons: [Cnvlutin: Ineffectual-neuron-free Deep Neural Network Computing](http://www.ece.ubc.ca/~aamodt/papers/Cnvlutin.ISCA2016.pdf)
* Sparse data GPU: [Implementing Sparse Matrix-Vector Multiplication on Throughput-Oriented Processors](https://pdfs.semanticscholar.org/9abb/086fabdcd2853ed8303c0f9a62cf4b917a62.pdf)
* Sparse data with CUDA: [Efficient Sparse Matrix-Vector Multiplication on CUDA](http://wnbell.com/media/2008-12-NVR-SpMV/nvr-2008-004.pdf)

TA: Chien-Yu Lin </br>
Email: myislin@gmail.com
