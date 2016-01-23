# Zpar-ChineseWordSegmentation

This is an example script to implement chinese word segmentation by running the code of **ZPar**<br><br>
Please follow the below steps:<br>
(1) Download the Source code of [ZPar](https://github.com/SUTDNLP/ZPar) to the directory `ZPar`.<br>
(2) Run command `cmake .` in the directory `CMake` to generate Makefile<br>
(3) Compile using `make segmentor` in the directory `Make` <br>
&#160; &#160; &#160; &#160;After compiling,a directory `ZPar/dist/segmentor` will be created,in which there are two files:`train` and `segmentor`. The file `train` is used to train a segmentation model,and the file `segmentor` is used to segment new texts using a trained segmentation model.<br>
(4) To train a model,type:<br>
&#160; &#160; &#160; &#160;`ZPar/dist/segmentor/train <train-file> <model-file> <number of iterations>`<br>
&#160; &#160; &#160; &#160;For example,`ZPar/dist/segmentor/train pku.train model 1`<br>
(5) To apply an existing model to segment new texts,type:<br>
&#160; &#160; &#160; &#160;`ZPar/dist/segmentor/segmentor <model> <input-file> <output-file>`<br>
&#160; &#160; &#160; &#160;For example,`ZPar/dist/segmentor/segmentor model pku.test pku.test.output`<br>
(6) Suppose a maunally specified segmentation of the input file has been given in a reference file,you can evaluate the quality of the outputs by typing:<br>
&#160; &#160; &#160; &#160;`python ZPar/doc/doc/seg_files/evaluate.py <output-file> <reference-file>` <br>
&#160; &#160; &#160; &#160;For example,`python ZPar/doc/doc/seg_files/evaluate.py pku.test.output pku.test.reference` <br>
&#160; &#160; &#160; &#160;The file `evaluate.py` performs automatic evaluation .You can find the precision,recall,and f-score here<br>
***
&#160; &#160; &#160; &#160;The performance of the system after one training iteration may not be optimal. You can choose the model that gives the highest f-score on your development test data by running `./test.sh` in the directory `ZPar/doc/doc/seg_files`,which can automatically train the segmentor for 30 iterations, and after the ith iteration, stores the model file to model.i. You can compare the f-score of all 30 iterations and choose model.k, which gives the best f-score, as the final model.In this file, there is a variable called `segmentor`. You need to set this variable to the relative directory of `ZPar/dist/segmentor`.
