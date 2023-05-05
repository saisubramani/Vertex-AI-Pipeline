# Now lets Create pipeline and Compile  

We completed 2 step, lets create the pipeline and compile the pipeline

Now what i need ? <br>
yeah same just need to import **buddy** !

```
import kfp.dsl as dsl
```

Define your **pipeline**. This example uses the  *load_data_op* factory function  from an earlier example. <br>
**PIPELINE** is a template for a multi-step workflow.

```
import kfp.dsl as dsl
from created_components_file import load_data_op

@dsl.pipeline(
   name='my-first-pipeline',
   pipeline_root = " gs://gcs location"
   description='An example pipeline that performs loading the data from google cloud storage.'
)

def load_data_from_gcs_pipeline():
  gcs_url_path = "gs://gcs-location-project/gcs-bucket/file-name.csv"
  load_data_from_gcs_op = load_data_op(
    gcs_url = gcs_url_path
  )

```

# Now lets Compile

Link gives a detail information about compile object : <https://www.kubeflow.org/docs/components/pipelines/v2/compile-a-pipeline/>

lets import compiler from **kfp**

```
from kfp.v2 import compiler

compiler.Compiler().compile(pipeline_func=load_data_from_gcs_pipeline,package_path="laod-data-from-gcs-pipeline.json")

```
pipeline_func : your pipeline function in our case **load_data_from_gcs_pipeline** <br>
package_path :  Json file which has pipeline information, this json file can be resued to trigger the pipeline job

# Now its final step let start the job:

We need *aiplatform* package 

```
from google.cloud import aiplatform
from datetime import datetime

SERVICE_ACCOUNT="Service-account-iam.gserviceaccount.com"
TIMESTAMP =datetime.now().strftime("%Y%m%d%H%M%S")
DISPLAY_NAME = 'laod_data_example-job{}'.format(TIMESTAMP)


job = aiplatform.PipelineJob(display_name = DISPLAY_NAME,
                             template_path = "laod-data-from-gcs-pipeline.json",
                             enable_caching = True,
                             project = "gcp-project",
                             location = "us-central1")

job.run(service_account=SERVICE_ACCOUNT)
```

1. We need SERVICE AACOUNT to start the job.
2. A Display Name for the job to see in vertex-ai pipeline console.
3. *enable_caching* will make use of successfully completed cache data, which executed previously.
4. project-id and location we can get using **gcloud config list**  command
# Important points

1. Pipeline name should not have "_",  Please specify a pipeline name that matches the regular expression "^[a-z0-9][a-z0-9-]{0,127}$" using `dsl.pipeline(name=...)` decorator.



<b> WoW we achieved ! Lets celebrate ! <b><br>

![](https://github.com/saisubramani/Vertex-AI-Pipeline/blob/main/IMAGE/sucessfull-1.jpg)