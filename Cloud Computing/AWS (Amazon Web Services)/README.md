# AWS (Amazon Web Services)

- [AWS Machine Learning Blog](https://aws.amazon.com/ru/blogs/machine-learning/)
- [Изучите возможности для Python на AWS](https://aws.amazon.com/ru/developer/language/python/)
- [AWS Documentation](https://docs.aws.amazon.com/index.html) - Find user guides, developer guides, API references, tutorials, and more
  - [Amazon SageMaker](https://docs.aws.amazon.com/sagemaker/index.html) - Documentation
    - [How Genworth built a serverless ML pipeline on AWS using Amazon SageMaker and AWS Glue](https://aws.amazon.com/ru/blogs/machine-learning/how-genworth-built-a-serverless-ml-pipeline-on-aws-using-amazon-sagemaker-and-aws-glue/)
    - [Creating a machine learning-powered REST API with Amazon API Gateway mapping templates and Amazon SageMaker](https://aws.amazon.com/ru/blogs/machine-learning/creating-a-machine-learning-powered-rest-api-with-amazon-api-gateway-mapping-templates-and-amazon-sagemaker/)
  - **AWS Lambda:**
    - [Lambda quotas](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html)
    - [Deploy Python Lambda functions with .zip file archives](https://docs.aws.amazon.com/lambda/latest/dg/python-package.html)
    - [AWS Lambda — теория](https://habr.com/ru/post/457100/)
  - [Amazon Simple Storage Service Documentation](https://docs.aws.amazon.com/s3/index.html):
    - [Creating a bucket](https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html)
    - [Bucket naming rules](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html)
    - [create-bucket](https://docs.aws.amazon.com/cli/latest/reference/s3api/create-bucket.html)
    - [Using high-level (s3) commands with the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-services-s3-commands.html)
    - [Uploading objects](https://docs.aws.amazon.com/AmazonS3/latest/userguide/upload-objects.html)
  - [AWS Elastic Beanstalk](https://aws.amazon.com/ru/elasticbeanstalk/)
    - [Complete Machine Learning solution(Part 3|3): Deploy Flask application on AWS Elastic Beanstalk](https://towardsdatascience.com/complete-machine-learning-solution-part-3-3-deploy-flask-application-on-aws-elastic-beanstalk-a86f127cef0a)
    - [Deploy Machine learning Flask app using ElasticBeanStalk service on AWS](https://medium.com/@skumarr53/deploy-machine-learning-app-using-elasticbeanstalk-service-on-aws-849c89745111)
    - [Deploy a machine learning model with AWS Elastic Beanstalk](https://medium.com/swlh/deploy-a-machine-learning-model-with-aws-elasticbeanstalk-dfcc47b6043e)
  - [Amazon Elastic File System](https://aws.amazon.com/ru/efs/):
    - [Shared File System for Your Lambda Functions](https://aws.amazon.com/ru/blogs/aws/new-a-shared-file-system-for-your-lambda-functions/)
  - [Amazon Elastic Container Service](https://aws.amazon.com/ru/ecs/?nc1=h_ls&whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc&ecs-blogs.sort-by=item.additionalFields.createdDate&ecs-blogs.sort-order=desc):
    - []()
- [Создание, обучение и развертывание моделей машинного обучения с помощью Amazon SageMaker](https://aws.amazon.com/ru/getting-started/hands-on/build-train-deploy-machine-learning-model-sagemaker/?trk=el_a134p000003yWILAA2&trkCampaign=DS_SageMaker_Tutorial&sc_channel=el&sc_campaign=Data_Scientist_Hands-on_Tutorial&sc_outcome=Product_Marketing&sc_geo=mult)
- [Hands-on Tutorials](https://aws.amazon.com/ru/getting-started/hands-on/?awsf.getting-started-category=category%23machine-learning&awsf.getting-started-content-type=content-type%23hands-on&trk=el_a134p000003yWJxAAM&trkCampaign=HandsOn_Tutorials_DS&sc_channel=el&sc_campaign=Hands-On_Tutorials&sc_outcome=Product_Marketing&sc_geo=mult) - Explore more tutorials from integrating intelligence to your apps to optimizing your models
  > Ознакомьтесь с практическими учебными пособиями и обучающими видеоматериалами по работе с сервисом AWS Начните работу и запустите первую рабочую нагрузку с помощью простых пошаговых учебных пособий 
- Coursera
  - [Getting Started with AWS Machine Learning](https://www.coursera.org/learn/aws-machine-learning)
- Edx
  - [AWS, Free online courses from Amazon Web Services](https://www.edx.org/school/aws)
- []()

## SageMaker Studio

### Write `.csv` file into S3 bucket

### Using AWS Data Wrangler

> _Pandas on AWS_

- [AWS Data Wrangler](https://aws-data-wrangler.readthedocs.io/en/stable/index.html) Documentation
- [AWS Data Wrangler](https://github.com/awslabs/aws-data-wrangler) on :octocat: GitHub

```python
!pip install awswrangler
```

> ❗**Note** : to make it work, the `awswrangler` has to be imported first

```python
import awswrangler as wr

wr.s3.to_csv(
    df=df_new,
    path='s3://'
)
```

## AWS Lambda

- **Building Scikit-Learn For AWS Lambda**
  - **Error:** `No module named 'sklearn.__check_build._check_build'`
  - Search: 
    - Using Scikit-Learn In AWS Lambda
    - Error with scikit-learn module in AWS Lambda
  - [Building Scikit-Learn For AWS Lambda](https://serverlesscode.com/post/scikitlearn-with-amazon-linux-container/)
  - [sklearn and pandas in AWS Lambda](https://datascience.stackexchange.com/questions/47955/sklearn-and-pandas-in-aws-lambda)
  - [Установка sklearn на AWS deeplearning AMI](https://coderoad.ru/49868348/Установка-sklearn-на-AWS-deeplearning-AMI)
  - [sklearn not working in aws lambda function. Deployment package issue](https://stackoverflow.com/questions/43872989/sklearn-not-working-in-aws-lambda-function-deployment-package-issue)
- 

### Articles

- [Возможности AWS Lambda](https://aws.amazon.com/ru/lambda/features/)
- [**AWS Machine Learning Blog**](https://aws.amazon.com/ru/blogs/machine-learning/)
  - [Deploying machine learning models as serverless APIs](https://aws.amazon.com/ru/blogs/machine-learning/deploying-machine-learning-models-as-serverless-apis/)
  - [How to Deploy Deep Learning Models with AWS Lambda and Tensorflow](https://aws.amazon.com/ru/blogs/machine-learning/how-to-deploy-deep-learning-models-with-aws-lambda-and-tensorflow/)
  - [Code-free machine learning: AutoML with AutoGluon, Amazon SageMaker, and AWS Lambda](https://aws.amazon.com/ru/blogs/machine-learning/code-free-machine-learning-automl-with-autogluon-amazon-sagemaker-and-aws-lambda/)
- [AWS Documentation](https://docs.aws.amazon.com/index.html)
  - [Create a Lambda Function and Deploy a Custom Trained Model to AWS DeepLens](https://docs.aws.amazon.com/deeplens/latest/dg/deeplens-getting-started-create-lambda.html)
  - [Using container images to run TensorFlow models in AWS Lambda](https://aws.amazon.com/ru/blogs/machine-learning/using-container-images-to-run-tensorflow-models-in-aws-lambda/)
  - [Tutorial: Configuring a Lambda function to access Amazon RDS in an Amazon VPC](https://docs.aws.amazon.com/lambda/latest/dg/services-rds-tutorial.html)
- Towards Data Science / Medium
  - [How to deploy a Machine Learning model on AWS Lambda](https://towardsdatascience.com/how-to-deploy-a-machine-learning-model-on-aws-lambda-24c36dcaed20)
  - [Deploy Machine Learning Models On AWS Lambda](https://medium.com/analytics-vidhya/deploy-machine-learning-models-on-aws-lambda-5969b11616bf)
  - [Serverless Machine Learning Engineering Project On AWS Lambda](https://medium.com/swlh/how-to-deploy-your-scikit-learn-model-to-aws-44aabb0efcb4)
  - [Deploying Machine Learning Model to AWS Lambda using Serverless](https://blog.francium.tech/deploying-machine-learning-model-to-aws-lambda-with-serverless-a121a8253901)
  - [Containerized ML deployment with AWS Lambda](https://sejalv.medium.com/containerized-ml-deployment-with-aws-lambda-680540fb92f4)
  - [How to Deploy ML models with AWS Lambda](https://blog.verta.ai/blog/how-to-deploy-ml-models-with-aws-lambda)
  - [How to Build an AWS Lambda for Data Science](https://towardsdatascience.com/how-to-build-an-aws-lambda-for-data-science-cec62deaf0e9)
- 

## AWS

- [SERVERLESS DATA PROCESSING ON AWS](https://data-processing.serverlessworkshops.io)
- [Deploy your Machine Learning model as a REST API on AWS](https://levelup.gitconnected.com/deploy-your-machine-learning-model-as-a-rest-api-on-aws-english-dcb1a0db3110)
