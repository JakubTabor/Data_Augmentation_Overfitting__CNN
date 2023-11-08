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

# Then I convert my images into 3D number numpy arrays, next i resize then to the same dimension for training purpose
# First i create two empty lists "X, y = [], []", then i make for loop " for flower_name, images in flowers_images_dict.items() and get acces to items"
# Then in that loop i create another loop "for image in images", I create "img" variable which is "cv2.imread and str on my image", 
# It will convert into 3D np.array, then I "resize img" using "cv2.resize" img variable and set size which is (180,180)
# Then I fill my "X and y" variables X with "resized_img as 3D array" and y with "flowers_labels_dict, so numbers of my labels of flower_name"
# And I convert my X and y into numpy arrays, I have X and y prepared, so I import "train_test_split" and get "train" and "test" set
# I check length of my sets and scaled them in range from 0 to 1 for training in my CNN
# Now I gonna build CNN, I create variable "num_classes = 5", then I start building "Sequential model"
# My first layer have 16 filter detectors, filter size is 3, "padding gonna add one layer of zeros to my image while processing"
# And "same" gonna return same output shape as my input shape 
# Then I add "pool layer after every conv. layer", I also add two "hidden conv. layers" with 32 and 64 neurons
# Next I add "Flatten layer" to convert it into "1D array" and I add one "Dense layer with 128 neurons", My "output layer will have 5 classes"
# Then I compile my model with "optimizer as adam", loss as "SparseCategoricalCrossentropy", because my output is "exact value" and "metrics as accuracy"
# I train my model with my "X_train_scaled, y_train and set number of epochs at 30" and I get unusually accuracy it means that my model is overtrained
# When I evaluate my model with completely new "X_test Scaler, y_test" it return me pretty low accuracy
# I also check predictions returning index of my prediction "np.argmax(score)"
# I gonna "augment" my data with new samples by "rotating and zooming" my original data, I can also "flip it"  
# I show how my data is changing after "augmentation", I also need to it into "numpy and int" "data_augmentation(X)[0].numpy().astype("uint8")"
# Once again I create my "Sequential model" but first I add "data_augmentation", then "thre convolutial layers", after every layer I create also "pool layer" 
# And I add also "dropout layer" which will "drop 0.2 neurons" for better "accuracy score" and I Flatten my conv. layers
# Then additional "Dense layer with 128 neurons" and output "Dense layer with five classes" 
# I compile my model with this same parameters as earlier and train it with "X_train_scaled, y_train and 20 epochs
# Accuracy on my model is "88", but when I evaluate model with new data from my "test sets" accuracy is "70"  in my previous model was "63"
# So we can notice difference, by adding new samples to our data and drop some neurons we can achieve better accuracy
