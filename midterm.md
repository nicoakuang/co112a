# **Study Journal**
## ***Topic: GPU/CUDA and other graphics processor related technologies***
#### By 鄭石光 111110534 資工二 | Teacher 陳鍾誠

## Chapter one, Overview of GPU Architecture
### Introduction to Graphics Processing Units (GPUs).
Graphics Processing Units, commonly known as GPUs, have become integral components in modern computing systems, playing a pivotal role in various applications beyond their original purpose of rendering graphics. In this introduction, we will explore the fundamental concepts of GPUs, their architecture, and the diverse range of tasks they perform.

What is a GPU?
A GPU is a specialized processor designed to accelerate rendering and manipulation of images and videos. Unlike Central Processing Units (CPUs), which are general-purpose processors, GPUs are optimized for parallel processing, making them highly efficient for tasks that involve handling multiple data streams simultaneously.

Evolution of GPUs
Initially developed for rendering graphics in video games, GPUs have evolved significantly. Modern GPUs are versatile and widely used in scientific simulations, artificial intelligence (AI), machine learning (ML), cryptocurrency mining, and other compute-intensive applications.

#### Key components and architecture of modern GPUs.
1. Stream Processors:
GPUs consist of multiple stream processors, each capable of executing its set of instructions concurrently. This parallel architecture enables GPUs to process a large volume of data simultaneously, leading to enhanced performance.

2. Memory Hierarchy:
GPUs have a hierarchical memory structure, including registers, shared memory, and global memory. This hierarchy is optimized for efficiently handling the vast datasets associated with graphics rendering and computation.

3. Parallelism:
Parallelism is a key feature of GPU architecture. Tasks are divided into smaller parallel threads, and each thread is processed independently. This approach allows GPUs to perform complex calculations faster than traditional CPUs.

#### GPU Applications
1. Graphics Rendering:
GPUs excel in rendering high-quality graphics for video games, simulations, and multimedia applications. They handle complex rendering tasks, such as shading, lighting, and texture mapping, with remarkable speed.

2. Scientific Computing:
Scientists and researchers leverage GPUs for complex simulations and scientific computations. The parallel processing capabilities of GPUs significantly accelerate simulations in fields like physics, chemistry, and biology.

3. Machine Learning and AI:
GPUs play a crucial role in training and running machine learning and AI models. Their parallel architecture is well-suited for processing large datasets and performing the matrix operations involved in neural network training.

4. Cryptocurrency Mining:
GPUs are used in cryptocurrency mining due to their parallel processing capabilities. They can efficiently perform the complex mathematical calculations required for mining various cryptocurrencies.

~ In-school area implementation ~

5. Video Processing:

Video processing using GPUs involves leveraging the parallel computing capabilities of Graphics Processing Units to perform various tasks on video data. GPUs excel in parallelizing tasks, making them well-suited for video processing, where multiple operations need to be performed simultaneously on different pixels or frames.

6. Image Processing:

Image processing involves manipulating or altering images to enhance or extract information from them. This field covers a broad range of techniques and methods aimed at improving the quality of images, extracting useful features, or preparing images for analysis.

## Chapter two, CUDA Programming Fundamentals
#### Basic CUDA syntax and concepts.

Understanding CUDA Kernels:

1.Kernel Definition:
```
__global__ void myKernel(int *array) {
    // Code to be executed on the GPU
}
```
The __global__ specifier indicates that this function will be called from the host but executed on the device (GPU).

2.Thread Hierarchy:
```
dim3 blockDim(16, 16); // 16x16 threads per block
dim3 gridDim(64, 64);  // 64x64 blocks in the grid
myKernel<<<gridDim, blockDim>>>(dev_array);
```
CUDA organizes parallel threads in a grid and each grid is divided into blocks. Threads inside a block can communicate and synchronize with each other.

3.Thread Indexing:
```
int threadIDx = threadIdx.x + blockIdx.x * blockDim.x;
int threadIDy = threadIdx.y +
```
CUDA provides built-in variables for thread indices.

#### GPU Memory Management

GPU memory management is a crucial aspect of leveraging the power of Graphics Processing Units (GPUs). Understanding how to efficiently allocate, transfer, and deallocate memory on the GPU is essential for optimizing performance.

**Memory Types:**

1. Global Memory:

Description: Largest memory space on the GPU.
Scope: Accessible by all threads.
Usage: Main storage for data shared across the GPU.

2. Shared Memory:

Description: Shared among threads within a block.
Scope: Limited to threads within a block.
Usage: Faster than global memory; used for communication within a block.

3. Constant Memory:

Description: Read-only memory cached for fast access.
Scope: Accessible by all threads.
Usage: Ideal for constants shared across threads.


**Memory Operations:**

1. Memory Allocation:

Usage: Allocate memory on the GPU using cudaMalloc.

2. Memory Copy:

Usage: Transfer data between CPU and GPU using cudaMemcpy.


3. Memory Deallocation:

Usage: Release allocated GPU memory using cudaFree.



## Chapter three, Parallel Programming with GPUs

Parallel programming with GPUs unlocks the immense processing power of graphics cards, enabling the execution of complex tasks concurrently. NVIDIA's CUDA platform is a prominent tool for harnessing this parallelism, allowing developers to implement and optimize parallel algorithms for GPUs. This chapter explores the principles of parallelism in GPU computing and guides you through the process of implementing parallel algorithms using CUDA.

#### Understanding Parallelism in GPU Computing:

1. SIMD Architecture:

GPUs are built on Single Instruction, Multiple Data (SIMD) architecture.
Multiple cores execute the same instruction on different data simultaneously.

2. Thread Hierarchy:

Execution occurs in threads organized into blocks and grids.
A block is a group of threads that can communicate and synchronize.
A grid is a collection of blocks.

3. Memory Hierarchy:

Efficient memory access is crucial for GPU performance.
Different memory types (global, shared, and local) serve different purposes.

#### Implementing Parallel Algorithms using CUDA:

1. Kernel Definition:

In CUDA programming, a kernel is a function that runs on the GPU. It is designed to be executed in parallel by multiple threads. The kernel function is identified with the __global__ qualifier.
Here, blockIdx.x and threadIdx.x are used to calculate a unique thread identifier tid.
For example:
```
__global__ void myKernel(int *input, int *output, int size) {
    int tid = blockIdx.x * blockDim.x + threadIdx.x;
    if (tid < size) {
        output[tid] = input[tid] * input[tid];
    }
}
```

2. Kernel Invocation:

Launching a CUDA kernel involves specifying the grid and block dimensions. The grid is a collection of blocks, and each block is a collection of threads. For example:
This launches the myKernel with gridSize blocks and blockSize threads per block.
```
int blockSize = 256;
int gridSize = (size + blockSize - 1) / blockSize;

myKernel<<<gridSize, blockSize>>>(d_input, d_output, size);

```

3. Optimizations:

Shared Memory Usage:
- hared memory is a fast, on-chip memory that can be shared among threads within a block.
- Efficient use of shared memory can enhance inter-thread communication and reduce global memory access.
```
__global__ void optimizedKernel(int *input, int *output, int size) {
    extern __shared__ int sharedData[];

    int tid = blockIdx.x * blockDim.x + threadIdx.x;
    if (tid < size) {
        sharedData[threadIdx.x] = input[tid];
        __syncthreads();

        output[tid] = sharedData[threadIdx.x] * sharedData[threadIdx.x];
    }
}

```

### Reading Materials Overview of GPU Architecture
- [Understanding GPU Architecture](https://www.intel.com/content/www/us/en/products/docs/processors/what-is-a-gpu.html)
- [Evolution of GPU](https://shadow.tech/en-GB/blog/history-of-gaming-gpus)
- [GPU Applications](https://openmetal.io/docs/product-guides/private-cloud/uses-for-gpus-other-than-gaming/)

### Reading Materials CUDA Programming Fundamentals
- [Basic CUDA syntax and concepts](https://medium.com/@rakeshrajpurohit/understanding-cuda-for-gpu-computing-330fa792ca1c#:~:text=Kernel%20Functions%3A%20In%20CUDA%2C%20you,computation%20based%20on%20its%20data.)
- [Memory Operations](https://example.com/cuda-guide)

### Reading Materials Parallel Programming with GPUs
- [Understanding Parallelism in GPU Computing](https://medium.com/@rakeshrajpurohit/understanding-cuda-for-gpu-computing-330fa792ca1c)
- [Implementing Parallel Algorithms using CUDA](https://www.sciencedirect.com/topics/computer-science/kernel-invocation)

