# Training models in Vertex AI AutoML

Project Name: <walkthrough-project-name/>

Project ID: <walkthrough-project-id/>

## AutoML Image Data Overview

[AutoML](https://cloud.google.com/vertex-ai/docs/beginner/beginners-guide) is an ideal tool for researchers with limited machine learning experience as much of the model building process is automated. Recently, AutoML has been integrated into Google Cloud's latest AI service - Vertex AI. With this new platform, Vertex AI integrates many features of model building into one location - including the use of [AutoML's pre-trained models](https://cloud.google.com/vertex-ai/docs/training-overview). This document will provide an overview of training an image model with AutoML Image, offered through Vertex AI.

You can use the [Google Cloud Console](https://console.cloud.google.com) to train an AutoML image mode. The following use cases are supported:

- Image classification (single label)
- Image classification (multi-label)
- Image object detection

Refer to this [Google documentation](https://cloud.google.com/vertex-ai/docs/tutorials/image-recognition-automl/training) for more information and tutorials for using AutoML to build image models.

This document will cover building a single label image classification model using a [COVID chest x-ray dataset](https://www.kaggle.com/datasets/pranavraikokte/covid19-image-dataset) from Kaggle.

## Data Requirements

To use AutoML to build an image model, you will need images (minimum of 10 per label) in one of the following formats:

- JPEG
- GIF
- PNG
- BMP
- ICO

You can use pre-labeled images or label the images in the Google Cloud Console. For more information and best practices on preparing image data for AutoML, please visit [this page](https://cloud.google.com/vertex-ai/docs/training-overview#image_data).

### Building an AutoML Image Classification Model

AutoML Image automatically builds state-of-the-art machine learning models on image data. The first step in building a model is to create a Vertex Image dataset.

## Creating an Image Dataset

You can access AutoML Image by navigating to **Vertex AI > Datasets** in the panel or search bar:

**1.** Navigate to Vertex AI Datasets:

[![Vertex AI Datasets](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image1.png "Vertex AI Datasets")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image1.png "Vertex AI Datasets")

---
**2.** Choose an existing dataset or [create a new dataset](https://cloud.google.com/vertex-ai/docs/training-overview) by clicking <walkthrough-spotlight-pointer spotlightId="dataset-list-create-dataset-button">Create</walkthrough-spotlight-pointer>:



[![Create New Dataset](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image2.png "Create New Dataset")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image2.png "Create New Dataset")

---
**3.** Give a name for your dataset, choose the data type, region, and select the objective. For this example, we will be building a single label image classification model:

[![Name New Dataset](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image3.png "Name New Dataset")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image3.png "Name New Dataset")

---
**4.** Next, import or upload your images. If your images are available in your [shared GCS bucket](https://cloud.google.com/vertex-ai/docs/training-overview#select-an-import-file-from-cloud-storage), you can provide the path to the bucket. Alternatively, you can [upload images](https://cloud.google.com/vertex-ai/docs/training-overview#upload-data-from-your-computer) (recommended if you don’t have labels) or [input files](https://cloud.google.com/vertex-ai/docs/training-overview#upload-an-import-file-from-your-computer) (recommended if you do have labels) from your computer.

[![Import or Upload Images](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image4.png "Import or Upload Images")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image4.png "Import or Upload Images")

---
**5.** You will be asked to specify a destination for the images you are uploading. Creating a folder within your shared GCS bucket is recommended.

[![Upload Destination](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image5.png "Upload Destination")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image5.png "Upload Destination")

---
**6.** When you are ready, click **Continue:**

[![Upload Destination](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image6.png "Upload Destination")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image6.png "Upload Destination")

---
**7.**  The import process may take several minutes or longer depending on the size of your data. You will receive an email notification like the one below when your upload is complete:

[![Import Notification](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image7.png "Import Notification")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image7.png "Import Notification")

---
**8.** When your data has uploaded, the next step is to create labels (if uploading unlabeled images). You must create at least two labels and have at least 10 samples of each to continue with the modeling process. Reference [this guide](https://cloud.google.com/vertex-ai/docs/datasets/label-using-console) for more information.

[![Label Creation](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image8.png "Label Creation")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image8.png "Label Creation")

---
**9.** When you have finished the labeling process, click **Train New Model** to build an image classification model:

[![Traing Model](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image9.png "Traing Model")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/automl-image9.png "Traing Model")


## Training the Classification Model

Now that your dataset has been created, imported, and labeled, you can use the Cloud Console to review training images and begin model building. Please reference [this documentation](https://cloud.google.com/vertex-ai/docs/tutorials/image-recognition-automl/training) for more information.

**1.** The first step is to specify your training method. Make sure you select **AutoML** and then choose **Continue:**

[![Traing Method](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image1.png "Traing Method")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image1.png "Traing Method")

---
**2.** Next, you will be asked to specify the details of your model. Click on **Advanced Options** to see every detail available. When you are satisfied, choose **Continue:**

[![Model Training Details](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image2.png "Model Training Details")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image2.png "Model Training Details")

---
**3.** You can choose to enable model explainability (optional) in the next window. Click [here](https://cloud.google.com/vertex-ai/docs/explainable-ai/overview?_ga=2.230388308.-973502620.1605036207) to learn more about Vertex Explainable AI.

[![Model Explainability](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image3.png "Model Explainability")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image3.png "Model Explainability")

---
**4.** In the final section, “Compute & Pricing” you must specify the node hour budget. The minimum node hour budget is **8**.

[![Compute Pricing](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image4.png "Compute Pricing")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image4.png "Compute Pricing")

---
**5.** When you are satisfied with the selections you have made for your new model, choose Start Training to begin the model training process.

---
**6.** You will see your model training as shown below:

[![Model Training](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image6.png "Model Training")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image6.png "Model Training")

---
**7.** When your model training has finished, you will receive an email notification like the one below:

[![Training Notification](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image7.png "Training Notification")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/training-image7.png "Training Notification")

## Evaluating the Classification Model

**1.** You can evaluate your model’s performance in the Cloud Console by navigating to **Vertex AI > Models** and selecting your model:

[![Evaludate Model](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/evaluate-image1.png "Evaludate Model")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/evaluate-image1.png "Evaludate Model")

---
**2.** Next, click on the **Evaluate** tab to see the performance of your model:

[![Evaludate Model Preformance](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/evaluate-image2.png "Evaludate Model Preformance")](https://storage.googleapis.com/test.mkwalter.com/vertex-automl/evaluate-image2.png "Evaludate Model Preformance")

---
The model building processes for the other available image objectives (multi-label classification and object detection) follow similar steps as shown above for single label classification. Please reference the [Google documentation](https://cloud.google.com/vertex-ai/docs/training-overview#image_data) for more information.
