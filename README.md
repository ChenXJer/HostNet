# HostNet

**HostNet** is a virus host prediction tool that can make predictions on rabies lyssavirus and flaviviruses, and can provide prediction services on other more data sets.

## Install

Note that this implementation has only been tested on Python 3.8.5, we recommend to use linux and miniconda for the enviroment management.

1. [Download and install Conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html).

2. Clone the `HostNet` repository: `git clone https://github.com/ChenXJer/HostNet.git` and change directory `cd HostNet`

3. Install Python dependencies: `pip3 install -r requirements.txt`
4. (Optional) Download the original dataset : `cd origin_data` and refer to the README.md file
5. Change directory `cd train`and test the installation: `python3 train_model.py`

HostNet configuration file commands
---

HostNet uses configuration files to centrally configure the parameters of the model.

 All configuration files are stored in the `/HostNet/train/config/` folder (you can also adjust it as needed), and the training will automatically read the folder. 

All profiles are trained sequentially. There are two example files in the current folder, which are used to test the two given example models respectively.



Each command in the configuration file and its specific meaning are shown in the following table.

|   command    |                         what it does                         |
| :----------: | :----------------------------------------------------------: |
|  input_path  |        The load path of the input dataset [required]         |
| output_path  | The path to save the best model and model key indicators [required] |
|  file_name   |                   Model naming [required]                    |
| cut_sequence |         Subsequence segmentation method (1.RC 2.ASW)         |
|    epochs    | Maximum number of epochs used for training the model (default : 100) |
|  subseq_len  |              Subsequence length (default : 250)              |
| emb_word_len |        Gene sequence fragment length (range : 1, 3-9)        |
|   emb_type   |      Gene sequence vectorization type (1.One-hot 2.K2V)      |
|  need_train  |        Train or test the model（y : train, n : test)         |
|  batch_size  |         Mini-batch size of dataset loading per epoch         |
|     clw      |           Use clw to balance the dataset（y or n)            |
| hidden_node  |     Counts of HostNet hidden layer nodes (default : 150)     |



After creating your config file you can train or test your model

HostNet output files
---

Some key parameter values for model training and testing will be generated under the output_path path specified in your configuration file. 

The meanings of each file are as follows:

- **file_name**_best_val_acc.pth : The hidden layer parameters of the best model for testing performance under the vaildation dataset, used to load the model for testing.
- key_point.csv : Generate parameter values such as accuracy, AUC, and F1 in the test model
- standard(mean)_confusion_matrix : Generate a confusion matrix at the Standard and Aggregated levels
- key_point_per_class_table.csv : Generate F1 and ACC corresponding to each category
- training_kpi.csv : Generate Train ACC, Train LOSS and Val ACC during training

Contribute
---

I would love for you to fork and send me pull request for this project.
Please contribute.

License
---

This software is licensed under the [Apache License](
