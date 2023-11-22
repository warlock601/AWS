# Fan-out Architecture
The development team at an startup E-commerce company has raised an issue.
They want to migrate from a custom solution that they are using to publish
messages to multiple endpoints. This custom solution occasionally goes down,
which impacts the production workflow. The development team needs a
managed solution that can send a published message to multiple set of
endpoints so that they don't have to worry about high-availability and the
configuration of the custom solution. To achieve this use-case, I want you to
design a fanout architecture using SNS and test the overall capabilities.
As part of the POC, use two different SQS queue as endpoint for SNS. Any
message published to SNS must be sent to both the SQS queues. This will
demonstrate the SNS capability of sending a published message to multiple set
of endpoints.
<br/>
Fan-out is a messaging pattern where messages are broadcasted in a one-to-many arrangement. Pub/Sub implies the ability to route messages from a single sender to multiple receivers.

1. Create a Standard-type SNS topic.
2. Create two SQS Queues with names "queue-1" & "queue-2" as standard type. These queues will receive messages from SNS as part of fan-out architecture.
3. Click on queue-1, SNS subscriptions > Subscribe to Amazon SNS topic > select the topic that was created and do similarly for queue-2
4. Go to Amazon SNS > select the created topic > Publish message > Enter message subject and body, then publish
<br/>
Before :<br/> <br/>

![Screenshot 2023-11-22 080053](https://github.com/warlock601/AWS-Projects/assets/32487715/a7489965-1d21-44f9-92c9-80f869434b06)

After :

![Screenshot 2023-11-22 080631](https://github.com/warlock601/AWS-Projects/assets/32487715/6c89712a-2412-40c0-94f7-f24c0c75d6a0)

5. To View message body: Amazon SQS > Queues > queue_name > Send And Receive Messages > Poll for messages. Messages will be available. Click on any message to see its body.

![Screenshot 2023-11-22 084138](https://github.com/warlock601/AWS-Projects/assets/32487715/479d96db-be79-4ea0-b249-6f591025006d)

