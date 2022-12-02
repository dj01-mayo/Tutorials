# Accessing Cloud DICOM

Project Name: <walkthrough-project-name/>

Project ID: <walkthrough-project-id/>

## Cloud DICOM Overview

Cloud DICOM holds extensive Mayo Clinic imagery data assets. This tutorial provides you the fundamentals of retrieving batches of that DICOM data for use in your AI/ML efforts.

This tutorial provides instructions for: 
1. Identifying a cohort of images hosted in the Advanced Data Lake and
1. Exporting those images to your project's local bucket.

## Setting up your project

You need to complete some access steps prior to following these instructions. 

If you have done so, skip ahead. 

If you have not completed these steps, please pause to complete them before continuing.

First, request the following entitlements in SailPoint.
- MCC Live - Midia Mdsa AIF Image Science Users
- MCC Live - ADL - FHIR BigQuery Views - Prod - Privacy Protected

Second (in parallel in okay), submit a [request](https://mcsm.service-now.com/serviceconnect?id=sc_cat_item&table=sc_cat_item&sys_id=967ba0921b1d1c506546b9541a4bcb4a) for Cloud DICOM to have access to write to your project's bucket. 

1. Choose Request type = Other,
1. Complete the required form fields,
1. Provide comments requesting that the Healthcare Service Agent needs Object Admin access to your project's buckets.

## Download the utility notebook

1. Navigate to Vertex AI.
1. Select Workbench to view the available notebooks.
1. Select your existing Notebook. (NOTE: Your DLVM must already be running)
1. Click OPEN JUPYTERLAB to open your Notebook.
1. Open a new Notebook, select Python 3 for the kernel.
1. Run the following command in a cell:

```
!gsutil -m cp -r gs://$AIF_COMMON_BUCKET/dsc-tutorial-resources /home/jupyter/welcome_demo
```

## Open and use the utility

Success! You have the Cloud DICOM utility notebook available. Follow the instructions below to utilize it.

You can also review the code involved to implement it in other scenarios.

1. Open the workbook in WelcomeDemo / dsc-tutorial-materials / DICOM-Batch.ipynb
1. Follow the instructions available in the workbook to query and download DICOM files from Cloud DICOM to your project's bucket.

To view, your DICOM images, navigate to Cloud Storage.
