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
