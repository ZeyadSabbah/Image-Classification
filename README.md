# Image-Classification
##Introduction
In this repo, the loaded images are for Skates, Shoes, Soccer_Shoes and Rollerblades.
They were uploaded from Google Images by downloading the URLs of each image in each search(category).

The purpose is to build a model using fastai.vision that can distinguish between those four objects.

##Creating the dataset
To have a dataset of images created
1. Searching for the objects or categories in Google Images is needed.
2. Opening the Console by pressing Shift + Ctrl + j in Windows or Linux.
3. Copying and pasting a javascript code that downloads the URLs of the items on the page
'urls=Array.from(document.querySelectorAll('.rg_i')).map(el=> el.hasAttribute('data-src')?el.getAttribute('data-src'):el.getAttribute('data-iurl'));
window.open('data:text/csv;charset=utf-8,' + escape(urls.join('\n')));'
4. Downloading the urls of each object (category) in the local machine.
5. Creating different directories in the Colab machine for the different categories.
6. Uploading the urls' text files.
7. Downloading the urls in the directories created for them.
8. Deleting the files that won't open because Google might have given a corrupted url.

Now there is raw data.

##Viewing the dataset
To view the dataset, since images of an object are in one directory, ImageDataBunch.from_folder function can be used. The validation set has to be specified with a percentage.
After that, using data.show_batch function to check the images.

Some of the images don't have the right labels, that's why cleaning these images is required. Leaving it for now, and be back to that point later.

##Training model
- Choosing resnet34 to be applied on this dataset.
- Fitting the dataset to the model.
- Error rate is 0.156.
- Checking for the best range of learning rate.
- Fitting the model further with the best learning rate.
- Saving the weights.

##Interpreting model's output
- Having a confusion matrix of the objects predicted on the validation set.
- Getting the most confused by the model.
- Shoes are mispredicted by the Soccer_shoes the most.

##Cleaning up the dataset
- Colab does not support widgets library from fastai, that's why cleaning images will take place on the local machine.
- Using Jupyter Notebook, after installing fastai and PyTorch, and creating an environment to work in, will run all the previous steps in local machine till reaching learn step.
- In addition to that, downloading the weight that has been saved earlier.
- Importing fastai.widgets, getting the top losses of this model.
- Using the ImageCleaner function, delete not relative images, and changing wrong labels till the message 'No images to show :)' appears.
- cleaned.csv file is created, which is two columns; one of them is for the file name (image) and the other is the right label of it.
- Reading this file to be a dataframe
- Splitting the dataset into training and validation sets (could continue without doing this step)
- Creating directories for train and valid, and the four categories as well.
- Copying the correct images from the original directories to the clean directories.
- Tarring clean data to be able to be uploaded in Colab.

##Uploading Clean Data
- Making a new direction for clean data, and untarring the uploaded file.
- Viewing data and applying the same steps before cleaning images.
- Accuracy increased by 5%.

##Predicting example
- Picking an example to be tested.
