1. DLQ is a queue that hold messages that could not be delivered to their intended recipients. Basically other queues can target DLQ for messages that can't be processed successfully, they're useful for debuggiing applications or messaging systems.<br/>
2. Messages can't be processed because of a variety of possible issues, such as erroneous conditions within the producer or consumer application or an unexpected state change that causes an issue with your application code. For example, if a user places a web order with a particular product ID, but the product ID is deleted, the web store's code fails and displays an error, and the message with the order request is sent to a dead-letter queue.
3. Benifits:
   - Configure an alarm for any messages moved to a dead-letter queue.

   - Examine logs for exceptions that might have caused messages to be moved to a dead-letter queue.

   - Analyze the contents of messages moved to a dead-letter queue to diagnose software or the producer's or consumer's hardware issues.

   - Determine whether you have given your consumer sufficient time to process messages.
  
Note: The dead-letter queue of a FIFO queue must also be a FIFO queue. Similarly, the dead-letter queue of a standard queue must also be a standard queue.
