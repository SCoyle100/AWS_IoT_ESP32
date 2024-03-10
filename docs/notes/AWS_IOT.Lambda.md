---
id: 9lbbwpngkuf55uyrygn58ek
title: Lambda
desc: ''
updated: 1682882656715
created: 1682880574904
---


```Python

import json
import boto3
import uuid

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('DHTSensorData1')

def lambda_handler(event, context):
    data = json.loads(event['message'])
    humidity = data.get('humidity')
    temperature = data.get('temperature')
    
    response = table.put_item(
        Item={
            'id': str(uuid.uuid4()),
            'humidity': humidity,
            'temperature': temperature
        }
    )
    
    return {
        'statusCode': 200,
        'body': json.dumps('Data stored successfully!')
    }

```


![](/assets/images/lambda_test.PNG)




