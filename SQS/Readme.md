# SQS

- Amazon SQS is a web service that gives you access to a message queue that can be used to store messaged while waiting for the computer a computer to process them.

- Amazon SQS is a distributed queue system that enables web services applications to quicky and reliablyqueue messages that one component in the application generates to be consumed by another component. A queue is a temporary repo for messages that are awaiting processing.

- Using Amazon SQS, you can decouple the components of an application so they run independently, easing message management between components. Any component of a distributed application can store messages in a fail-safe queue. Messages can contain up to 256 KB of text. Any component can later retrieve the message programmatically using the Amazon SQS API.

- The queue acts as a buffer between the component producing and saving data. This means that queue resolves issues that arise if the producer is producing  work faster than the consumer can process it, or if the producr or consumer are intermittently connected to the network.

## Two different Types of Queue

- Amazon SQS offers standard as the default queue type. A standard queue lets you have a nearly-unlimited number of transactions per second.
- Standard queues guarrantes that a message will be delivered at least once.
- However, occasionally (because of highly-distributed architecture that allows high throughput). more than one copy of the message might be delivered out of order. Standard queues provide best-effort ordering which ensures that messages are generally delivered in the same order as they are sent.

- FIFO Queue complements Standard Queue. The most important feature of this type are First In First Out delivery and exactly once processing. The order in which messages are sent and received is strictly preserved. And a mesasge is delivered once and remains available until a consumer processes and deletes it; duplicates are not introduced in the queue.

- FIFO queues also support message groups that allow multiple ordered message groups within a single queue. FIFO queues are limited to 300 transactions per second, but have all the capabilities of a standard queue.

# Exam Tips:

- SQS is pull pased, not push based.
- Messages are 256 KB in size.
- Messages can be kept in the queue from 1 min to 14 days; the default retention period is 4 days.
- Visbility timeout is the amount of time that the message is invisible in the SQS queue after a reader picks up that message. Provided the job is processed before th visbility timeout expires, the message will then be deleted from the queue.
- If the job is not processed within the time, the message will become visible available again and nother reader will process it. This could result in the same message being delievered twice.
- Visbility timeout maximum is 12 hours.
- SQS guarantees messages will be delivered at least once.
- Amazon SQS long polling is a way to retrieve messages from your Amazon SQS queues. While regular short polling returns immediately (even if the message queue being polled is empty), long polling doesn;t return a response until a message arrives in the message queue, or the long poll times out.
