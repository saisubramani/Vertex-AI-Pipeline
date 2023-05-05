# Welcome to create your first component

I will not start with basic , like adding 2 numbers using a function and then telling you that how i converted function to component ! 

I will directly go with GCP stuff!

# Little bit inputs we need, before Coding !

Please go through this Link which give a good understanding of how to define fucntion and passing a parameter to it : <https://www.kubeflow.org/docs/components/pipelines/v1/sdk/python-function-components/>

## Some  **important** points to remember:

1. A Kubeflow Pipelines component is a self-contained set of code that performs one step in your ML workflow. 
2. The component code, which implements the logic needed to perform a step in your ML workflow.
3. A component specification defines  <br>
  a. The component’s metadata, its name and description. <br>
  b. Docker container image to run <br>


![](https://github.com/saisubramani/Vertex-AI-Pipeline/blob/main/IMAGE/KF1.jpg)
## How to write a function:

1. It should *not use any code declared outside of the function* definition.
2. Helper functions must be defined *inside this function*
3. If the fucntion need to return larger value , *we need to pass the data as a file*.
4. Function accept numerical value as a parameter, and the parameter must have type hints. supported type *int* and *float*.
5. **If your function has complex dependencies, choose or build a container image for your Python function to run in.**


### As you know i will give some key points , my key points are <br>

1. Parameters represent values. They are inputs or outputs of type str, int, float, bool, dict, or list that typically are used to change the behavior of a pipeline. 
2. Parameters are stored in metadata
3. **Artifacts represent references to objects–most commonly files–that are produced during pipeline executions.**
4. Example of Artifacts:
  a. Models
  b. Datasets
  c. Metrics



# Lets take a use case:
you need to pull the data from GCS and make use of it in your ML pipeline

GCS - Google Cloud Storage

Man make it simple..!, I am new to kubeflow !
Relax first we can create a function

## Python function:

1. Below python fucntion will help you to pull the data from gcs using Pandas dataframe.
2. As we know that data should be passed to next component! but we cant return larger value , so we need to pass as file !

How can i pass as file ? <br>
I will give some details , refer this link : <https://www.kubeflow.org/docs/components/pipelines/v1/sdk-v2/v2-component-io/#:~:text=The%20Kubeflow%20Pipelines%20SDK%20v2,the%20behavior%20of%20a%20pipeline.>



```

from kfp.dsl import Dataset, Output

def load_data_from_gcs(
  gcs_url:str,
  data_set:Output[Dataset]
):
  import pandas as pd

  pd_dataframe = pd.read_csv(gcs_url)
  # preprocessing code
  # processed_df 
  processed_df.to_pickle(data_set.path+".pkl")

  print(pd_dataframe.head(2))

```

The above function will read the data from GCS as pandas dataframe and we are dumping as pickle file to pass this data to next component.

Note: Here we are passing the fetched data as a pickle file to next component, we can pass as  csv file also. 

```
from kfp.dsl import Output

def load_data_from_gcs(
  gcs_url:str,
  data_set:Output[Dataset]
):
  import pandas as pd

  pd_dataframe = pd.read_csv(gcs_url)
  # preprocessing code
  # processed_df 
  processed_df.to_pickle(data_set.path+".csv")

  print(processed_df.head(2))

```

Yeah now we have python function, we can convert this function to kubeflow component in next readme <link>