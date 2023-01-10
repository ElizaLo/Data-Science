<img src="https://raw.githubusercontent.com/ElizaLo/Data-Science/master/img/MLOps.png" width="1050" height="150">

## Courses

- ["Deployment of Machine Learning Models"](https://www.udemy.com/course/deployment-of-machine-learning-models/?referralCode=D4FE5EA129FFD203CFF4) by Udemy

## Articles, Blogs

- [A Brief Guide to Running ML Systems in Production](https://www.oreilly.com/content/a-brief-guide-to-running-ml-systems-in-production/) by O'Reilly 
  > Best Practices for Site Reliability Engineers  
- [Efficient Machine Learning Inference](https://www.oreilly.com/content/efficient-machine-learning-inference/) by O'Reilly
  > The benefits of multi-model serving where latency matters
- [Site Reliability Engineering (SRE)](https://sre.google) by Google

## Machine Learning Lifecycle Platforms

| Title | Description|
| :---: | :--- |
|[MLflow](https://mlflow.org)|<ul><p>MLflow is a platform to streamline machine learning development, including tracking experiments, packaging code into reproducible runs, and sharing and deploying models. MLflow offers a set of lightweight APIs that can be used with any existing machine learning application or library (TensorFlow, PyTorch, XGBoost, etc), wherever you currently run ML code (e.g. in notebooks, standalone applications or the cloud).</p><li>[MLflow GitHub](https://github.com/mlflow/mlflow)</li></ul>|
|[Aporia](https://www.aporia.com)|<ul></p>The Monitoring Platform for Machine Learning<p><li>[Aporia GitHub](https://github.com/aporia-ai)</li><li>[ML Platform Workshop](https://github.com/aporia-ai/mlplatform-workshop)</li></ul>|
|[Comet.ml](https://www.comet.ml/site/data-scientists/)|<ul><p>Comet is doing for ML what Github did for code.</p><p>Track your datasets, code changes, experimentation history, and models. Comet provides insights and data to build better models, faster while improving productivity, collaboration and explainability.</p></ul>|
|[DVC](https://dvc.org)|<ul><p>Data Version Control, or DVC, is a data and ML experiment management tool that takes advantage of the existing engineering toolset that you're already familiar with (Git, CI/CD, etc.).</p></ul>|

## Tools

| Title | Description|
| :---: | :--- |
|[Synapse Machine Learning](https://github.com/microsoft/SynapseML)|<ul><p>Simple and Distributed Machine Learning</p><p>SynapseML (previously MMLSpark) is an open source library to simplify the creation of scalable machine learning pipelines. SynapseML builds on Apache Spark and SparkML to enable new kinds of machine learning, analytics, and model deployment workflows. SynapseML adds many deep learning and data science tools to the Spark ecosystem, including seamless integration of Spark Machine Learning pipelines with the Open Neural Network Exchange (ONNX), LightGBM, The Cognitive Services, Vowpal Wabbit, and OpenCV. These tools enable powerful and highly-scalable predictive and analytical models for a variety of datasources.</p></ul>|


## :octocat: GitHub Repositories

| Title | Description|
| :---: | :--- |
|[MLOps-Basics](https://github.com/graviraja/MLOps-Basics)|The goal of the series is to understand the basics of MLOps like model building, monitoring, configurations, testing, packaging, deployment, cicd, etc.|
|[MLOps Zoomcamp](https://github.com/DataTalksClub/mlops-zoomcamp)|Free MLOps course from DataTalks.Club|
|[Deployment of Machine Learning Models](https://github.com/trainindata/deploying-machine-learning-models)|Code for the online course ["Deployment of Machine Learning Models"](https://www.udemy.com/course/deployment-of-machine-learning-models/?referralCode=D4FE5EA129FFD203CFF4)|


## AWS 

| Title | Description|
| :---: | :--- |
|[Amazon SageMaker Safe Deployment Pipeline](https://github.com/aws-samples/amazon-sagemaker-safe-deployment-pipeline)|Safe blue/green deployment of Amazon SageMaker endpoints using AWS CodePipeline, CodeBuild and CodeDeploy.|

### Workshops

:octocat:

| Title | Description|
| :---: | :--- |
|[Amazon Sagemaker MLops (with classic CI/CD tools) Workshop](https://github.com/awslabs/amazon-sagemaker-mlops-workshop)| Machine Learning Ops Workshop with SageMaker: lab guides and materials.|
|[ML Platform Workshop](https://github.com/aporia-ai/mlplatform-workshop)|This repo contains example code for a (very basic) ML platform.|
| | |

### Articles

- [Deploying A Pre-Trained Sklearn Model on Amazon SageMaker](https://towardsdatascience.com/deploying-a-pre-trained-sklearn-model-on-amazon-sagemaker-826a2b5ac0b6)

## Azure 

| Title | Description|
| :---: | :--- |
|[MLOps with Azure ML](https://github.com/microsoft/MLOpsPython)|MLOps using Azure ML Services and Azure DevOps|

## 🐳 Docker

<img src="https://raw.githubusercontent.com/ElizaLo/Data-Science/master/img/docker_1.png" width="1050" height="150">

- [Docker Hub](https://hub.docker.com)
- [Docker Cheat Sheet](https://www.docker.com/sites/default/files/d8/2019-09/docker-cheat-sheet.pdf)
- [Docker Documentation](https://docs.docker.com)
- [List of TCP and UDP port numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

### Docker Documentation

- [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)
- [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [Container networking](https://docs.docker.com/config/containers/container-networking/)
- 

### Articles 

**Security:**
- [Hardening Docker containers, images, and host - security toolkit](https://cloud.redhat.com/blog/hardening-docker-containers-images-and-host-security-toolkit) by Red Hat
- [Docker Container Security 101: Risks and 33 Best Practices](https://www.stackrox.io/blog/docker-security-101/)
- 

### Docker Commands

- Build **image**

      docker build -t [testimage (name of image)] .

- Build **container**

      docker run --name [name of container] -p [ports] [name of image]
      docker run --name testcontainer -p 8080:80 testimage

- Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

      docker scan
      
- Show all images

      docker images --all

- Show all containers

      docker ps

- Exec

      docker exec --help
      
- Logs

      docker logs 
      docker logs --help
      
- Remove container

      docker rm

- Remove image

      docker rmi
      
- Login to DockerHub

      docker login
      
- Push a new image to this repository using the CLI

      docker tag local-image:tagname new-repo:tagname
      docker push new-repo:tagname
      
Make sure to change tagname with your desired image repository tag.

- Add tag 

      docker tag [image name] [user name]/[repo name]:[tag name]

- To push a new tag to this repository

      docker push user_name/repo_name:tagname
      
- Docker Pull Command

      docker pull user_name/repo_name
      
- Create Volume

      docker volume create volume_name
      
- Volume list

      docker volume list
    
- Inspect volume

      docker inspect volume

### :octocat: GitHub Repositories 

| Title | Description, Information |
| :---:         |          :--- |
|[Awesome Docker](https://github.com/veggiemonk/awesome-docker)|🐳 A curated list of Docker resources and projects|
|[Awesome Compose](https://github.com/docker/awesome-compose)|Awesome Docker Compose samples|
|[❄️ 🐳 Awesome AI, ML and Data Science on Kubernetes](https://github.com/CognonicLabs/awesome-AI-kubernetes)|❄️ 🐳 Awesome tools and libs for AI, Deep Learning, Machine Learning, Computer Vision, Data Science, Data Analytics and Cognitive Computing that are baked in the oven to be Native on Kubernetes and Docker with Python, R, Scala, Java, C#, Go, Julia, C++ etc|
|[CIS Docker Benchmark support](https://github.com/aquasecurity/docker-bench)|Checks whether Docker is deployed according to security best practices as defined in the CIS Docker Benchmark|

## Kubernetes

<img src="https://raw.githubusercontent.com/ElizaLo/Data-Science/master/img/kubernetes.png" width="1050" height="150">

### Communities

| Title | Description, Information |
| :---:         |          :--- |
|[The StackRox Community](https://www.stackrox.io)|Security continues to be a critical need for the broader cloud-native ecosystem building and running Kubernetes applications. The StackRox community will work toward providing an open source Kubernetes-native security solution to protect Kubernetes environments.|

# Machine Learning in Production

<img src="https://raw.githubusercontent.com/ElizaLo/Data-Science/master/img/Production.png" width="1050" height="150">

## :octocat: GitHub Repositories

| Title | Description, Information|
| :---:         |          :--- |
|[applied-ml](https://github.com/eugeneyan/applied-ml#forecasting)|Papers & tech blogs by companies sharing their work on data science & machine learning in production.|
|[awesome-production-machine-learning](https://github.com/EthicalML/awesome-production-machine-learning)|A curated list of awesome open source libraries to deploy, monitor, version and scale your machine learning.|
