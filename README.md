# Finding-Similarity-between-Vector-Models-of-Images-using-Similarity-Scores

Author: Ashwin Karthik Ambalavanan
Contributors: 1. Ajay Gunasekaran
       	      2. Aditya Vikram Sharma

Download the folder into the C:/ Drive so that all file paths are supported. Download the devset from: http://skuld.cs.umass.edu/traces/mmsys/2015/paper-5.

The codebase is used for finding similarity between users, images and locations from features extracted from a set of images in flickr as given in the link: http://skuld.cs.umass.edu/traces/mmsys/2015/paper-5

Check the detailed description of tasks in the pdf file attached with the project. The task code SHOULD be run in the order described for correct execution. For detailed explanation of the logic used in each of the 5 tasks, check "Code/README_Tasks.txt". 	

The dataset describes features describing Images taken in Locations that are annotated manually by Users.
There are two types of features: 
1. Textual Descriptors which consist of TF, DF and IDF values for each annotation grouped under user, image or location category.
2. Visual Descriptors which consists of 10 Color Models, namely, CM, CM3x3, CN, CN3x3,CSD,GLRLM,GLRLM3x3, HOG,LBP, LBP3x3 which give different sets of values for each image.

There are a total of 30 Locations. Each location has around 298 - 300 images. There are 10 Color models for each location which give different values for the images of that location.

We use Cosine similarity because Cosine similarity is calculated using only the dot product and magnitude of each vector, and is therefore affected only by the terms the two vectors have in common. Cosine thus has some meaningful semantics for ranking similar documents, based on mutual term frequency.

The schema for the first 3 tasks (content of corresponding CSV Files) are stored as below:
[Annotations UserID1 UserID2 UserID3]
["wicked"      Value   Value   Value]
[......   	....    ....    ....]

Check http://skuld.cs.umass.edu/traces/mmsys/2015/paper-5/Div150Cred_readme.txt for information about the dataset.

The "Code" folder contains the entire project
The "devset" folder contains the text descriptor and the visual descriptor features.
The "Outputs" folder contains document outputs for each individual task.
The "Report" describes in detail what has been done in the project.

Description of items in devset Folder:
	1. devset/desctxt- Has Textual Descriptors (TF, DF, TF-IDF) for grouped for Image, Location and Users.
	2. devset/descvis- Has Visual Descriptors for images in locations which is the output of 10 different color models(CM, CM3x3, CN, CN3x3,CSD,GLRLM,GLRLM3x3, HOG,LBP, LBP3x3)
	3. devset_topics.xml- XML File containing mapping of number to location name. 

Description of items in Code Folder:
	1. Code/CSV- Contains required csv files for each task
	2. Code/Tasks- Contains the Task code for each task.
	3. Sample_Inputs_*- Has the inputs required for each task.
	
Code/CSV/img_edit- Contains all edited images after clustering which is the output of K_Means_Clustering.py clustering with cluster size 10. These 	
					files are used in Task 4.
Code/CSV/img_edit_task5- Contains all edited images after clustering which is the output of K_Means_Clustering_Task_5.py with cluster size 7. These 
					files are used in Task 5.
Code/CSV/Task_1- Contains 3 CSV files with User Data categorized together based on TF, DF and IDF values.
Code/CSV/Task_2- Contains 3 CSV files with Image Data categorized together based on TF, DF and IDF values.
Code/CSV/Task_3- Contains 3 CSV files with Location Data categorized together based on TF, DF and IDF values. It also contains the "devset_textTermsPerPOIEdited.csv" which is the same as "devset_textTermsPerPOI.csv" but with the first couple of word names of locations joined with an "underscore".

The task code described below SHOULD be run in the order described for correct execution.

Code/Tasks/CSV_Writer_DB_User.py- The code is used to extract required data from the file devset_textTermsPerUser.txt and write the required 		
information in a database type format into a csv file. The column header in the written file would signify the user id's of the various users and the row headers would be annotations.

Code/Tasks/Task_1.py- The code is used to extract 'k' similar users for a given user based on the tf, df or idf values as specified in the sample inputs file.

Code/Tasks/CSV_Writer_DB_Images.py- The code is used to extract required data from the file devset_textTermsPerImage.txt and write the required information in a database type format into a csv file. The column header in the written file would signify the user id's of the various users and the row headers would be annotations.

Code/Tasks/Task_2.py- The code below is used to extract 'k' similar images for a given image based on the tf, df or idf values as specified in the sample inputs file.

Code/Tasks/CSV_Writer_DB_Locations.py- The code below is used to extract required data from the file devset_textTermsPerPOI.txt and write the required information in a database type format into a csv file. The column header in the written file would signify the user id's of the various users and the row headers would be annotations.

Code/Tasks/Task_3.py- The code below is used to extract 'k' similar location for a given location based on the tf, df or idf values as specified in the sample inputs file.

Code/Tasks/K_Means_Clustering.py- The code below performs K-Means Clustering with a cluster size of 10 with 10 image samples taken from each cluster and written into the edited images folder. These images are used for Task_4.

Code/Tasks/Task_4.py- The code below is used to extract 'k' similar locations given a location id and a model (CM, CM3x3, CN, CN3x3, CSD, GLRLM, etc). For each match, the code also lists the overall matching score as well as the 3 image pairs that have the highest similarity contribution.

Code/Tasks/K_Means_Clustering_Task_5.py- The code below performs K-Means Clustering with a cluster size of 7 with 10 image samples taken from each cluster and written into the edited images folder. These images are used for Task_5.

Code/Tasks/Task_5.py- The code below is used to extract 'k' similar locations given a location id and a model (CM, CM3x3, CN, CN3x3, CSD, GLRLM) based on visual descriptors. For each match, the code also lists the overall matching score and the individual contributions of the 10 visual models.
