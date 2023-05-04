# I Don't know where to Start Vertex AI 
Hi readers this Document is created to share my experience and findings which i gone through during my learning  ! <br>
Feel free to make changes and let me know if my statements is false during your reading ! <br>
Reach me : <saisubramani68@gmail.com> <br>




# Why Vertex AI ?
**Below are keypoints to understand why we need vertexAI**

1.  Create a dataset and upload data.

2.  Train an ML model on your data:

    Train the model
    Evaluate model accuracy
    Tune hyperparameters (custom training only)
    Upload and store your model in Vertex AI.

3.  Deploy your trained model to an endpoint for serving predictions.

4.  Send prediction requests to your endpoint.

5.  Specify a prediction traffic split in your endpoint.

6.  Manage your models and endpoints.

# What i need is to implement custom-trained ML models on Vertex AI.

This *link* gives you a detail understanding of custom-trained ML Model in vertexAI : <https://cloud.google.com/architecture/ml-on-gcp-best-practices>

I can give you an example: <br>

Client : Hi guys i have built a model i need to host it on GCP so that user can make use of the model !

MLOps Team : Yeah we can do it, just need answers for below listed Questions
1. Where your inference data comes from ? whether is it Streaming or realtime data ?
2. Where is your Model? is in local or in GCP ?
3. What frame work did you used for creating the model?
4. Do you need to retrain the model on any specify duration? or you need a traning pipeline ?
5. Is there any pre/post processing work in data before sending to the model for inference?
6. Do you need to monitior your model performance ?

Once you get answer for all the question now you need to go in deep !

![](https://github.com/saisubramani/Vertex-AI-Pipeline/blob/main/IMAGE/deeper.jpg)


**Vertex AI Pipelines lets you orchestrate your machine learning (ML) workflows in a serverless manner. Before Vertex AI Pipelines can orchestrate your ML workflow, you must describe your workflow as a pipeline. ML pipelines are portable and scalable ML workflows that are based on containers and Google Cloud services.**

# Building Pipelines !

Detail information on this link : <https://cloud.google.com/vertex-ai/docs/pipelines/build-pipeline#sdk>

Which pipelines SDK should I use? <br>
Vertex AI Pipelines can run pipelines built using the Kubeflow Pipelines SDK v1.8.9 <br>

Build your pipeline using the **Kubeflow Pipelines SDK**. By building a pipeline with the Kubeflow Pipelines SDK, you can implement your workflow by building custom components or reusing prebuilt components, such as the Google Cloud Pipeline Components. Google Cloud Pipeline Components make it easier to use Vertex AI services like AutoML in your pipeline.

I hope you got some understanding on why vertex ai, especially why custom model training/ Deployment !

see you on next Document <>