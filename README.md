# Detect-technologies-I2

## Follow below steps to run the demo

### 1. Install anaconda and create the virtual environment
> conda create -n demoEnv python=3.7.0

### 2. Install the dependencies from requirement.txt file
> pip install -r requirement.txt

### 3. Run the setup file setup.sh
> bash setup.sh

### 4. Initiate airflow webserver
> conda activate demoEnv

> airflow webserver -p 7070

### 5. Initiate sceduler
> conda activate demoEnv

> airflow scheduler

### Refresh the page and open taxi_solution DAG

## Follow below steps to create tensorflow serving
### 1. Install tensorflow-serving-server
> docker pull tensorflow/serving

### 2. Verify the image installation
> docker images

### 3. Containerize the model
> docker run --name myTFServing -it -v <-path to saved_model>:/DT_tfserving -p 9001:9001 --entrypoint /bin/bash tensorflow/serving

### 4. Run the tfserving
> tensorflow_model_server --rest_api_port=9001 --model_name=taxi_experiment --model_base_path=/DT_tfserving/saved_models

### 5. Verify the tf serving
> curl -X GET http:/localhost:9001/v1/models/taxi_experiment
