## OpenMMLab 实战营打卡 - 第 2 课 - Note

* Image classification Task

  * Limitation of ordinary classification algorithm
  
  * handcrafted design features
    
    * image ->  handcrafted design features -> classification 
    
      * example for handcrafted design algorithm:
      
        * step1: calculate gradient for neighbour pixels     
         * step2: performing statistics on gradients
      
   * Supervised learning
   
   * Self-Supervised Learning
     
     * Learning based on unlabeled data
     
   * Classification Network development
  
     * VGG(2014)
     
       * split **5x5** kernel  into **3x3** kernels in multiple layers
       
     * ResNet (2015)
        
        * why ResNet works?
        
          * 1.1  ResNet have $O(2^n)$ hidden path to connect input and output 
          
          * 1.2 Loss surface is smooth after adopting residual module, easily converging to a global minimum or local minimum.
          
        * ResNet B, C, and D improvements:
          
          * improve the partial structure of the residual modules
        
        * ResNeXt
        
          * Use group convolution to reduce the number of parameters
        
        * SEResNet
        
          * Introduce attention mechanism to channel dimension
      
      * Neural architecture search (2016+) 

        * Using reinforcement learning and some algorithm to search networks for the best performance
        
          * Example
            
            * NASNet (2017), MnasNet (2018) , EfficientNet(2019), RegNet (2020)
            
      * Vision Transformers (ViT)
      

        * Use a transformer instead of a convolution network to classify by a larger dataset. It can perform better than convolution-based networks.
          
          * Visional Transformer (2020)
          
          * Swin-Transformer (2021 ICCV best paper) 
          
          * ConvNeXt (2022)
        
            * Swin transformer's model elements migrate to the convolutional network (I should read this paper later)
            
    * Convolution
    
      * Convolution parameter calculation
      
      *  GoogLeNet use different size of a kernel
      
      * ResNet Bootleneck block to compress channel, reduce computation cost (to build the deeper network)
      
      *  Depthwise Separable Convolution
      
         *  decompose regular convolution into layer-by-layer and point-by-point convolution (MobileNet V1/V2/V3)
  
    * Vision Transformer
      
      * Difference 
      
        * Global reception field
        
        * Swin Transformer 
        
          * Vision Transformer  (2020) feature map is obtained from 16 times downsampling, indifferent to ViT, Swin Transformer applied Hierarchical Transformer structure 
          
          * Shifted Windows Multi-head Self-attention to achieve global reception field.
  
    * Model Learning
      
      * Self-supervised learning 
        
      * Cross-Entropy loss

      * Stochastic gradient descent (SGD)
      
    * Training skills
    
      *  Random initialisation weights
      
      * annealing learning rate 
      
        * Apply a relatively higher learning rate at the beginning of training until the learning rate becomes stable. And then apply a lower learning rate
      
      * Warmup
      
        *   Gradual increase in learning rate in the first few rounds of training up to a preset learning rate to stabilise the initial phase of training
     
        *   For the same training task, when a factor of k expands the batch size, the learning rate should also be multiplied by a factor of k.
        
      * Adaptive gradient algorithm
        
        * Different parameters require different learning rates, which are automatically adjusted according to the historical magnitude of the gradient

      * Weight Decay
      
      * EMA
      
      *Early stopping

    * Dataset augmentation
    
      * Label Smoothing
      
    *  Self-supervised learning
    