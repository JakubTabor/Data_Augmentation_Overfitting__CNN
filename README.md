# Data_Augmentation_Overfitting__CNN
data augmentation in CNN
# First I need download dataset from tensorflow, so I will save "url", then I use method "get_file" on "flower_photos" from my saved url "dataset_url"
# I gonna save it in directory and unzip it using "using untar"
# Then I need to convert my data into "pathlib", so it will be more easy to use, I use "Path of my data_dir" "pathlib.Path(data_dir)"
# Now i convert my data_dir into list, then i want five samples, so i make them global "list(data_dir.glob('*/*.jpg'))[:5]"
# I want to get length of my dataset, so i take len of my global images and save it as variable "image_count"
