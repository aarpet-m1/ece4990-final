General Instructions for the using the YOLO / RF-DETR notebooks.
First, make sure to run all steps starting from the top first to install all prerequsities toolboxes that are required to run the model. 

YOLOv11/12
Initial setup must be run so that a compatable Nvidia GPU can be found in the system. Next, run the next notbook prompt to install ultralytics as it contains the YOLOv11 or YOLOv12 models.
The YOLO sample image notebook can be skipped as it provides a example of a sample image runtime.
Follow the next subsections, each is named after its respective dataset. Run the 1st block always so that the directory can be set and moved to the
Google Colab main directory. The next block will install roboflow so that the respective dataset can be downloaded through the roboflow website. This might take a short while.
The next block contains the code to start the training process using Google Colab with modifyable hyperparameters.
The next two blocks allow for the user to mount to Google Drive so that the training results and weights can be stored and not deleted by the Google Colab runtime.
Skipping the next blocks that contain other datasets are to be skipped to generate data from the training results. The subsection "Display Data from Dataset" contains the first step to start the setup for display. Running the next blocks until the end of the page will generate the confusion matrix, best results, Loss/mAP graphs, and the test grid.

If needed to generate different train results, keep in mind the name of the new trained weights file. For example, the 2nd run of a different dataset will be named "train2" and "val2" to be used to display the new data from a different dataset training result.

RF-DETR
This notebook relies on having a ROBOFLOW account so that the user can fork datasets from the Roboflow library of datasets.
{ Instructions from Roboflow
To fine-tune RF-DETR, you need to provide your Roboflow API key. Follow these steps:

Open your HuggingFace Settings page. Click Access Tokens then New Token to generate new token.
Go to your Roboflow Settings page. Click Copy. This will place your private key in the clipboard.
In Colab, go to the left pane and click on Secrets (🔑).
Store HuggingFace Access Token under the name HF_TOKEN.
Store Roboflow API Key under the name ROBOFLOW_API_KEY.
}


Now that your API key is found, you can run the next block to add huggingface or roboflow api key to access your account.
Next, run the Nvidia-smi block to confirm there is a running GPU in the notebook.
Install the dependencies so the RF-detr model is ready to be used.
Example data and inference can be skipped as they are sample runtimes.
Next, make sure to get your URL from roboflow so that it can be fetched to the notebook environment. The next block concerns actually running the model.
With the high GPU VRAM requirement, our suggestions is to use these settings: model.train(dataset_dir=dataset.location, epochs=100, batch_size=1 , grad_accum_steps=1, lr=1e-4) 
If this did not work with the free T4 GPU, a google colab subscription plan may be required to access the L4 High Ram GPU. 
Once successfully trained, the next blocks allow for the inference and evaluation data to be generated with the trained dataset. 
In order to download your weights and images, click on the folder on the left of the side bar and find "/content/output". The weights will be named output. Generated images will be in the same directory. Keep in mind that the runtime session must NOT be terminated by any means to keep the weights to be accessable through Google Colab's temporary file storage. It is possible to mount the user's Google Drive to the Google Colab notebook so the weights and data can be saved there instead. 

Known Issue: Free T4 GPU in Google Colab will not run the RF-DETR model as it requires more VRAM.

