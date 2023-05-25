# Data_Augmentation_Overfitting__CNN
data augmentation in CNN
# First I need download dataset from tensorflow, so I will save "url", then I use method "get_file" on "flower_photos" from my saved url "dataset_url"
# I gonna save it in directory and unzip it using "using untar"
# Then I need to convert my data into "pathlib", so it will be more easy to use, I use "Path of my data_dir" "pathlib.Path(data_dir)"
# Now i convert my data_dir into list, then i want five samples, so i make them global "list(data_dir.glob('*/*.jpg'))[:5]"
# I want to get length of my dataset, so i take len of my global images and save it as variable "image_count"
# Then I check roses images in my dataset, so I use "PIL.Image" to open first image and save my roses images as variable "roses"
# Now I gonna create one list for my images to sort "every type" of them and ine list for my images labels to give them numbers
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
