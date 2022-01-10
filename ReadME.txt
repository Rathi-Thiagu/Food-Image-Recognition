All the files listed in here need to be run using GPU to reduce training time.

Resouces Needed  : Google Colab Pro 
RunTime settings : GPU and High RAM  

Dataset will be automatically downloaded from URLs.FOOD. 
Commands are added for installing the correct version of pyTorch and torchvision needed.

All the files will need a google drive mount to store the model after training. If you dont want to mount google drive , kindly comment the below lines in cell No 2 and change the path from '/content/drive/MyDrive/' to '/content/model/' in the code while saving the model.
	from google.colab import drive
	drive.mount('/content/drive')
	
Food_101_EffNetB4.ipynb: 
	This is the Best model file that trains the EfficientNetB4 and saves two trained models
	1. learneffb4.save('/content/drive/MyDrive/food-effNetb4101-train-e3')
	2. learn_effb4.save('/content/drive/MyDrive/food-effNetb4101-train-ev3')
	
Food_101_EffNetB5.ipynb: 
	This file will load the pretrained EfficientNetB5 and train the model on Food 101 after performing augmentation on Training set.
	Running this file will save the trained model in this path "/content/drive/MyDrive/food101-effNetb5-train-e3".
	Incase of you are mounting the google drive kindly change the path to "/content/model/food101-effNetb5-train-e3"

Fastai Widget_Demo.ipynb:
	This file gives a demo of the fastai widget used to remove the top k losses after training the model. It stored the cleaned dataset as cleaned.csv in the specified path.

Food101_EffNetB3.ipynb:
	This file will load the pretrained EfficientNetB3 and train the model on Food 101 after performing augmentation on training set.
	Running this file will save two models.
		1. Model trained with original data - learneffb3.save('/content/drive/MyDrive/food101-effNetb3-train-e3') - Acc 0.85
		2. Model trained with cleaned data  - learneffb3.save('/content/drive/MyDrive/food101-effNetb3-train-ev4') - Acc 0.89

Food101_EffNetB0.ipynb:
	This is the first baseline model trained without manual cleaning ,learning rate optimizer ,TTA and got low accuracy. 
	Running this file will create a directory '/content/models' and saves the trained model in learn.save('/content/models/food-101-train-epoch-v1').
	
	
Food_101_ResNet152.ipynb:
    This file will train the ResNET152 model and save in learn.save('/content/drive/MyDrive/food-ResNET101-train-e4').
	The accuracy is very low so it is not consideed for predicting the test accuracy and ensemble of models.

Food_101_Ensemble.ipynb
	This file is dependent on the following files.
		Food101_EffNetB3.ipynb
		Food101_EffNetB4.ipynb
		Food_101_EffNetB5.ipynb
	So first the mentioned files need to be run and models has to saved.
	In this ensemble file, we load the saved models and then predict the test images using all the models and guess the label based on majority or weighted average of the probabilities of each class.
	
	Model 1 = EfficientNetB3 = Acc 0.85
	Model 2 = EfficientNetB4 = Acc 0.85
	Model 3 = EfficientNetB3 = Acc 0.89
	Model 4 = EfficientNetB5 = Acc 0.88
	Ensemble of Model 1 + 2 + 3 = Acc 0.86 (Ensemble using majority vote)
	Ensemble of Model 1 + 2 + 3 +4 = Acc 0.88 (Ensemble using class probability averaging)
	Ensemble of Model 1 + 2 + 3 + 3 + 4 = Acc 0.87 (Ensemble using weighted average)
	
Error_ResNET152_Training.ipynb
	Kindly do not try this file . This is kept only for recursive Exception reference.
	
The class categories in the dataset.

apple_pie,baby_back_ribs,baklava,beef_carpaccio,beef_tartare,beet_salad,beignets,bibimbap,bread_pudding,breakfast_burrito,bruschetta,caesar_salad,cannoli,caprese_salad,carrot_cake,ceviche,cheese_plate,cheesecake,chicken_curry,chicken_quesadilla,chicken_wings,chocolate_cake,chocolate_mousse,churros,clam_chowder,club_sandwich,crab_cakes,creme_brulee,croque_madame,cup_cakes,deviled_eggs,donuts,dumplings,edamame,eggs_benedict,escargots,falafel,filet_mignon,fish_and_chips,foie_gras,french_fries,french_onion_soup,french_toast,fried_calamari,fried_rice,frozen_yogurt,garlic_bread,gnocchi,greek_salad,grilled_cheese_sandwich,grilled_salmon,guacamole,gyoza,hamburger,hot_and_sour_soup,hot_dog,huevos_rancheros,hummus,ice_cream,lasagna,lobster_bisque,lobster_roll_sandwich,macaroni_and_cheese,macarons,miso_soup,mussels,nachos,omelette,onion_rings,oysters,pad_thai,paella,pancakes,panna_cotta,peking_duck,pho,pizza,pork_chop,poutine,prime_rib,pulled_pork_sandwich,ramen,ravioli,red_velvet_cake,risotto,samosa,sashimi,scallops,seaweed_salad,shrimp_and_grits,spaghetti_bolognese,spaghetti_carbonara,spring_rolls,steak,strawberry_shortcake,sushi,tacos,takoyaki,tiramisu,tuna_tartare,waffles