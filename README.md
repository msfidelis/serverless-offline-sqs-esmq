# Serverless Offline SQS / ElasticMQ Plugin

This adapter works with ElasticMQ API. 

```bash
docker run -it -p 9324:9324 s12v/elasticmq:latest
```

## Install

```bash
npm install serverless-offline-sqs-esmq
```

## Starting a Queue


```yml

custom:
  serverless-offline-sqs-esmq:
    apiVersion: '2012-11-05'
    endpoint: http://0.0.0.0:9324
    region: sa-east-1
    accessKeyId: root
    secretAccessKey: root
    
```

```yml
resources:
  Resources:
    BooksQueue:
      Type: AWS::SQS::Queue
      Properties:
        QueueName: BooksQueueExample
```

## Using SQS API 

```javascript
const options = {
    apiVersion: '2012-11-05', 
    region: 'localhost',
    endpoint: "http://0.0.0.0:9324",
    sslEnabled: false,
};

const sqs = new AWS.SQS(options);
```

## Output Log: 

```bash
serverless offline start 
...
Serverless: Creating Queue BooksQueueExample
...
```


Credits: This is a custom fork from [Godu Project](https://www.npmjs.com/package/serverless-offline-sqs.)
