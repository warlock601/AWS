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
