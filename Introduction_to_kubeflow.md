# What is Kubeflow in genral ?

Kubeflow is a platform for data scientists who want to build and experiment with ML pipelines. <br>
Kubeflow is also for ML engineers and operational teams who want to deploy ML systems to various environments for development, testing, and production-level serving.

Hey stop ! what is pipeline first? <br>

In my understand a pipeline is a description of a machine learning (ML) workflow, including all of the components in the workflow and how the components relate to each other in the form of a graph. <br>
The pipeline configuration includes the definition of the inputs (parameters) required to run the pipeline and the inputs and outputs of each component.

# Show me the pipeline first !

![Pipeline](https://github.com/saisubramani/Vertex-AI-Pipeline/blob/main/IMAGE/pipeline.jpeg)

# Now what is pipeline componenets?

Components are composed of a set of inputs, a set of outputs, and the location of a container image. <br  >
A component's container image is a package that includes the component's executable code and a definition of the environment that the code runs in.

Example : In our *pipeline image* you can see there is a preprocess-data which is known as *components* <br>

From the above image we can say that we have 4 components totally !

I hope you got some understandig about component!

# Now i need to create a component ?

I will say yes and No,  I came to know there are prebuilt components ! 

You can use prebuilt-components use this link to know what are available already : <https://google-cloud-pipeline-components.readthedocs.io/en/google-cloud-pipeline-components-1.0.26/google_cloud_pipeline_components.aiplatform.html>

These are prebuilt available components where you can use in your pipeline! which makes you effort less !

Stop ... ! I have special requirements i need to create my own components ! what can i do ?

I have answer, if you know how to write a python function means then you can build your own component as simple as !

# What i need to create a component?
 **You need Kubeflow first !** <br>

![Kubeflow](https://github.com/saisubramani/Vertex-AI-Pipeline/blob/main/IMAGE/kubeflow.png)

Link to install Kubeflow : <https://www.kubeflow.org/docs/components/pipelines/sdk/install-sdk/>

Link to install Vertex AI Python client : <https://github.com/googleapis/python-aiplatform>

Vertex AI services Link : <https://github.com/kubeflow/pipelines/tree/master/components/google-cloud#installation>

Once you are done with all installation we can start to build our own kubeflow components !

See you in Next document <>







