# Converting the function to component

What i need to convert function to component?<br>
Just you need to import *kubeflow* buddy , as simple as! 

```
import kfp
from kfp.components import create_component_from_func_v2
```

# I need to give some Notes on this !
```
create_component_from_func_v2
```
1. Call **kfp.components.create_component_from_func(func)** to convert your function into a pipeline component.

        a. func: The Python function to convert.
        b. base_image: (Optional.) Specify the Docker container image to run this function in.
          Currently, if you do not specify a container image, your Python-function based component uses the python:3.7 container image. 
          If your function has complex dependencies, you may benefit from using a container image that has your dependencies preinstalled, or building a custom container image
          Link : https://www.kubeflow.org/docs/components/pipelines/v1/sdk/python-function-components/#containers
        c. output_component_file: (Optional.) Writes your component definition to a file. You can use this file to share the component with colleagues or reuse it in different pipelines.
        d. packages_to_install: (Optional.) A list of versioned Python packages to install before running your function

Lets come to our use case:

```
from my_python_file import load_data_from_gcs

load_data_op = create_component_from_func_v2(
    func=load_data_from_gcs,
    base_image=docker_image,
)
```

A Good overall example Link : <https://www.kubeflow.org/docs/components/pipelines/v1/sdk/python-function-components/#example-python-function-based-component> 

Now we created a Kubeflow component lets celebrate !

![](https://github.com/saisubramani/Vertex-AI-Pipeline/blob/main/IMAGE/successful.jpg)

We have Kubeflow component now lets create Pipeline and compile , see you in next Document part-3 <link>
