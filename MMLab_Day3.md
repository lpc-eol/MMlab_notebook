## OpenMMLab 实战营打卡 - 第 3 课 - Note

* Pytorch training overviews
    
    * Define loss function and optimizer 
    
    * Inner loop for training
      
      * compute prediction error  (loss)
      * Backpropagation 
  
        * `optimizer.zero_grad() `
        
        * `loss.backward()`
        
        * `optimizer.step()`   
        
      * Output logs 
    * Inner loop for testing
    
    * training loops 
      
      * `for t in range (epochs):` 
    
    * Saving models
  
    * loading models (inference)
    
      * `model = NeuralNetwork()` (Create instance)
      
      * `model = load_state_dict (torch.load("model.pth"))`

    * predict new images
    

    ```python
     model.eval ()  (**important**)
     x,y = test_data[0][0],test_data [0][1]
     with torch.no_grad():
        pred=model(x)
        predicted,actual = classes [pred[0].argmax(0)],classes[y]
        print(f'Predicted: "{predicted}",Actual:"{actual}")
    ```

* MMlab config
  
  * model structure (layers, channels) 
  
  * Dataset (dataset path, dataset augmentation, dataset partition) 
  
  * Training strategy (gradient decent algorithm, learning rate, batch size, total training epoch, learning rate scheduler ) 
  
  * GPU, distributed training
  
  * logs, checkpoints  
    
* Config code explain

    * mobilenet-v2
    
      *  `type = MobileNet-v2` (model name)
      
      * `num_classes =1000 ` (classify 1000 class) 
       
       * `data=`  (pipeline for forward pass)
     
       * inference single image
        
           * `result = inference_model (model,'xxx.jpg')`  
        * visualization of the result
          
          ``` python
          from mmcls.apis import show_result_pylot

          show_result_pyplot(model,'xxx.jpg',result)
    
      * config file variable location is not important
      
      * `load_from =` (use for finetune), path to achieve pre-trained weight 
      
      * `data_prefix=` (path to achieve training dataset ), e.g `data/fruit30_split/train` 
      
      *   `ann_file`, annotation class names
      
      * **MMLab default 8 GPUs training, therefore learning rate has to divide by 8 if you are using a single GPU.**
    
    * Launch training command
    
      * `mim train mmcls mobilenet-v2_fruit.py`  
    
* Q&A
  * Q : Does the input size of an image to a model be fixed? (AlexNet, GoogLeNet)
  
    A : For early deep learning models, they use a full-connected layer, the output size is fixed, and then the input size should also be fixed. For modern deep learning networks, they use the global average pooling layer instead of the full-connected layer. Therefore, the input size no longer needs to be fixed.


