# Mashroom-detection

1
Annotate the images using imgtool.
2
make a folder name custom dataset and put all the images and corresponding text file keep it and zip it.
3
make a folder name Yolov3_custom_model_training in google drive and upload the dataset folder inside it.
4:
make google colab notbook and change runtime to GPU.
5:
mount it into google drive.
6: 
go to the directory and unzip the dataset.
7:
clone the respority to the googlecolab in your project folder.

8: download make file and enable GPU, opencv and CUDNN and upload it.
9: go to cfg folder insider darknet folder, so all the yolo version file are in cfg folder, so choose one of then
   that you work on it. In my case I choose yolov3.
10: find and download the yolov3.


11: open the yolov3 file in an editor, and do some changes like, comment the testing section (batch and subdivesion),
     and enable the training section. and there is only one class in this case, so set your batch size and subdivison
    your own and it must be divisible by 2. then changes the maximum batches which is equal to the number of classes x 2000.
    then change the number of steps which is conventionaly maximum batches -200, maximum batches +200.

12: search the yolo in the editor so you face three layers. first go the first layer. and before the yolo you can see the
filters which is equal to the bounding box and number of class +5. so you have to change it.
so 18 for one class. also change the classes in yolo first.

13: repeat the 12 number steps for both the layers yolo, and yolo.( just change the filter and number of classes.)
     save and upload the file. this is your custom yolo model. because you set it for your own problem.

14: then go to colab and run the make commond.

15: after running the make commond you go to the main folder.

16: after compilation by using make commond then for training we have to split the data into training and testing section.
     for this go to this url and download the files. (https://github.com/jakkcoder/Training_Yolo_Custom_Object_Detection_files.git)
17. go to inside these file (creating-files-data-and-name, and other similar name)  and open it. after opening change the
    full path to your path ('Custom data') in creating files datat and name file. and similar steps do with the second file
     as well. after path changing pick the files and place it inside custom data.
18. after that download the clases.txt and change it with the extension of (.names) and upload this files as well but dont
    remove the clases files as well.

19: download the pre traind weights or custom weights for yolov3 i download darknet53.con.74 from this link
(https://pjreddie.com/darknet/yolo/)
20: make new folder inside the yolov3 main folder name custom weights and upload this pretraind weights.

21.then go to the colab and run this commond 
  !python Custom_data/creating-files-data-and-name.py
  !python Custom_data/creating-train-and-test-txt-files.py
these two files we have uploaded so now we run it and after running go to directory and check new file with name 
label_data and two train and test.txt  is generated.
so if you open the test and train so randomly they split the data.

after this we want to exceute this commond inorder to successfully excute all the things.
!darknet/darknet

make a folder with name backup because all the custom weights are here during training.

22. training commond.
 !darknet/darknet detector train Custom_data/labelled_data.data darknet/cfg/yolov3_custom.cfg custom_weight/darknet53.conv.74 -dont_show

23: if error comes just change the image type jpeg to jpg in the train-test-txt files.

24: test it using custom weights which are saving in the backup file.
 
25: use final weights and yolov3_custom.cfg. upload some images. understand the code. 
note that opencv2 take the images from gbr not rgb so convert it using cvt function.



 



