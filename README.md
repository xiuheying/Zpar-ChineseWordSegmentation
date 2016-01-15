# Zpar-ChineseWordSegmentation

This is an example script to implement chinese word segmentation by running the code of zpar

Please follow the below steps:
(1)Download the Source code of ZPar to the directory zpar.
(2)Compile:
   make zpar.zh for the Chinese zpar
   make segmentor for the word segmentation system.
   After compiling,a directory zpar/dist/segmentor will be created,in which there are two files:train and segmentor. The file train is used to train a segmentation model,and the file segmentor is used to segment new texts using a trained segmentation model.
(3)To train a model,type:
   zpar/dist/segmentor/train <train-file> <model-file> <number of iterations>
(4)To apply an existing model to segment new texts,type:
   zpar/dist/segmentor/segmentor <model> [<input-file>] [<output-file>]
(5)Suppose a maunally specified segmentation of the input file has been given in a reference file,you can evaluate the quality of the outputs by typing:python evaluate.py output.txt reference.txt to get the precision,recall,and f-score.(The file evaluate.py can be find in the directory zpar/doc/doc/seg_files )

The performance of the system after one training iteration may not be optimal. You can choose the model that gives the highest f-score on your development test data by running "./test.sh" in the directory zpar/doc/doc/seg_files,which automatically trains the segmentor for 30 iterations, and after the ith iteration, stores the model file to model.i. You can compare the f-score of all 30 iterations and choose model.k, which gives the best f-score, as the final model.In this file, there is a variable called segmentor. You need to set this variable to the relative directory of zpar/dist/segmentor.
