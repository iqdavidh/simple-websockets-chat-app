
sam package --template-file template.yaml     --output-template-file packaged.yaml     --s3-bucket iqdavidh.demochat


sam deploy --template-file packaged.yaml  --stack-name simple-websocket-chat-app  --capabilities CAPABILITY_IAM     --parameter-overrides MyParameterSample=MySampleValue

aws cloudformation describe-stacks     --stack-name simple-websocket-chat-app --query 'Stacks[].Outputs'


--Probando *********************************************************

On the console, connect to your published API
$ wscat -c wss://agplpgfagi.execute-api.us-west-2.amazonaws.com/prod
```
4. To test the sendMessage function, send a JSON message like the following example. The Lambda function sends it back using the callback URL: 
``` bash
$ wscat -c wss://agplpgfagi.execute-api.us-west-2.amazonaws.com/prod
connected (press CTRL+C to quit)
> {"message":"sendmessage", "data":"hello world"}
< hello world
```
