  in NetworkVisualization-TensorFlow, it introduces **SqueezeNet**. it uses squeezenet1_0 which has some difference from squeezenet1_1
  
  when i have downloaded the weights about the model, there comes three files: 
  
  * squeezenet.ckpt.data-00000-of-00001, 
	
  * squeezenet.ckpt.index, 
	
  * squeezenet.ckpt.meta. 


  i don't know their relationship and not sure which one should be feed to the save_path in the initial step.
Since it is written by tensorflow, there are some introductions in  
http://cv-tricks.com/tensorflow-tutorial/save-restore-tensorflow-models-quick-complete-tutorial/

  according to the tutorial, meta graph is a protocol buffer which saves the complete Tensorflow graph; i.e. all variables, 
operations, collections etc. This file has **.meta** extension. Checkpoint file is a binary file which contains all the values of the weights, biases, gradients and all the other variables saved. This file has an extension .ckpt. 
However, Tensorflow has changed this from version 0.11. Now, instead of single **.ckpt** file, we have two files: data file is the file that contains our training variables

when run step "Pretrained Model", the error occurs:


	INFO:tensorflow:Restoring parameters from cs231n/datasets/squeezenet.ckpt/
	INFO:tensorflow:Restoring parameters from cs231n/datasets/squeezenet.ckpt/
	---------------------------------------------------------------------------
	NotFoundError                             Traceback (most recent call last)
	/home/yoyo/cs231/cs231_environments/assignment2/.env/lib/python3.5/site-packages/
	tensorflow/python/client/session.py 	in _do_call(self, fn, *args)
  
	......
	NotFoundError: Unsuccessful TensorSliceReader constructor: Failed to find any matching files for 	cs231n/datasets/squeezenet.ckpt/
	 [[Node: save/RestoreV2_51 = RestoreV2[dtypes=[DT_FLOAT], _device="/job:localhost/replica:0/task:0/cpu:0"](_arg_save/Const_0_0, save/RestoreV2_51/tensor_names, save/RestoreV2_51/shape_and_slices)]]

	During handling of the above exception, another exception occurred:

	......

**REASON:**
	the path is wrong. in assignment3, i have reused the virtulenv in assignment2, so the current root is in assignment2. 
	if changed to absolute path, everything comes normal.
