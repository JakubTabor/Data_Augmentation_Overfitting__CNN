 **Data_Augmentation_Overfitting__CNN**
# First I need to download dataset from tensorflow
# So i save "url", then I use method "get_file" on "flower_photos" from my saved url "dataset_url"
* I save it in directory and unzip, using "untar"

# Then I need to convert my data into "pathlib"
* Thats because it will be more proper to use (Path of my data_dir), it looks like this **(pathlib.Path(data_dir))**
* Now i convert my data_dir into list, i want five samples, so i make them global **(list(data_dir.glob('*/*.jpg'))[:5])**
* I want to get length of my dataset, so i take len of my global images and save it as variable (image_count)
* Then I check roses images in my dataset, so I use **(PIL.Image)** to open first image and save my roses images as variable **(roses)**

# Next I gonna create one list for my images to sort "every type" of them and secound list for my images labels

![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/flower_images_dictionary.png)

# Then I convert my images into numerical 3D numpy arrays, next i resize then to the same dimension for training purpose
* First i create two empty lists **(X, y = [], [])**, then i make for loop **(for flower_name, images in flowers_images_dict.items())** and with acces to items
* Then in that loop i create another loop **(for image in images)** i create **img** variable which is **(cv2.imread and str on my image)** 
* It will convert into **(3D np.array)** then i resize img using **cv2.resize** img variable and set size which is **(180,180)**
* Then I fill my **(X and y variables, X with resized_img as 3D array and y with flowers_labels_dict)** so numbers of my **labels of flower_name**

![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/convertion_of_all_images.png)

# And i convert my (X and y into numpy arrays) i have (X and y) prepared
* Next i import (train_test_split) and get **(train and test sets)**
* I check length of my sets and scaled them in range **(from 0 to 1 for training in my CNN)**

# Now i gonna build CNN, i create variable to keep all visually good (num_classes = 5), then i start building (Sequential model)
![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/CNN_model.png)

* First layer have 16 filter detectors **(filter size is 3)** padding means adding **one layer of zeros** to my image while processing
* And **(padding = same)** return **same output shape as my input shape** 

# Then i add (pool layer after every conv. layer), and i also add two (hidden conv. layers) with 32 and 64 neurons
* Purpose of adding (pool layer) is to reduce the dimensions the layers

![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/maxpool.gif)

# Next i add "Flatten layer" to convert it into (1D array) 
* And also one **(Dense layer with 128 neurons)** **(My output layer have 5 classes)**
* Then i compile my model with **optimizer as adam** and loss as **SparseCategoricalCrossentropy**, because my output is **exact value**
* **metrics is accuracy**

![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/Flatten_layer.png)

# Next training of my model, so i use (X_train_scaled, y_train and set number of epochs at 30)
* During the training appears **(accuracy close to 1.00)** it means that my model is overtrained
* When I evaluate my model with **(X_test Scaler, y_test)** so brand new data it return me pretty low accuracy in comparison to accuracy during trainning 
![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/Model_before_augmentation.png)

* I also check predictions, but i need to return index of my prediction (np.argmax(score))

# Now i gonna (augment) my data with new samples by (rotating and zooming) my original data, i can also (flip it)  

![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/data_augmentation_process.png)

# I show how my data is changing after (augmentation), it is zoomed and rotated
* I also need to convert it into **(numpy and int type)**  **plt.imshow(data_augmentation(X)[0].numpy().astype("uint8"))**

# Once again I create my "Sequential model" but first i add (data_augmentation function) 

![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/CNN_augmented.png)

* Then **thre convolutial layers** after every layer i put also **pool layer** 
* And i add also **dropout layer** which will **drop 0.2 of neurons** for better **accuracy score**
* After that Flatten layer to fit all **conv layers** into my **neural net**
* Then additional **Dense layer with 128 neurons** and output **Dense layer with five classes** 

# I compile my model with this same parameters, because there is no need to change anything in there
* And next training my model with **X_train_scaled and y_train and 20 epochs**
* Now accuracy of my model during the training reaches **88**
* After evaluation of my model with my **test sets accuracy is 70**
![](https://github.com/JakubTabor/Data_augmentation_imbalance_data/blob/main/Images/Model_after_augmentation.png)
* in my previous model **it was 63**
* So we can notice the difference, by adding new samples to our data and drop some neurons we can achieve better accuracy
* Its because our model is trained on more possible variants of images
