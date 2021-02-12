# AWS-Fargate-App

Sample Flask Application on AWS Fargate

AWS Cloud-Formation templetes will create aws vpc & application load balncer with Fargate,



##Builiding 

 AWS base network with 2 private & 2 public subnets & ECS roles

```
aws cloudformation create-stack --stack-name base-network --template-body file://private-vpc.yml --parameters ParameterKey=EnvironmentName,ParameterValue=production --capabilities CAPABILITY_NAMED_IAM
```

 Application load-balncer which is exposed to outside world with public URL

```
aws cloudformation create-stack --stack-name ecs-alb --template-body file://alb_external.yml --parameters ParameterKey=EnvironmentName,ParameterValue=production
```

AWS Fargate Cluster

```
aws cloudformation create-stack --stack-name sample-app --template-body file://fargate.yml --parameters file://parameters.json
```

