# SWF

- Amazon Simple WorkFlow Service

- Is a web service that makes it easy to coordinate work across distributed application components. SWF enables applications for a range of use cases, including media processing, web application backends, business process workflows, and analytics pipeline, to be designed as a coordination of task.

- Tasks represents invocation of various processing steps in an application which can be performed by executable code, web sevice calls, human actions, and scripts.

- Amazon uses it in their warehouse.

- Human Element -  SWF service

## SWF vs SQS

- SQS has a retention period of 14 dys, SWF exctions can last up to 1 year.
- Amazon SWF presents a task-oriented API, where Amazon SQS offeres a message oriented API.
- Amazon SWF enusres that as task is assigned oly once and it is never duplicated. With Amazon SQS, you need to handle the duplicated messages and may also need to ensure that a mssage is processed inly once.
- Amazon SWF keeps track of all the tasks and events in an application. With Amazon SQS, you need to implement your own application-level tracking especially of your application uses multiple queues.

## SWF Actors

- Workflow starters: An application that can initiate (start) a workflow. Could be your e-commerce website following the placement order or mobile app searching for bus time.

- Deciders: Control the flow of activity tasks in a workflow execution. If something has finished (or failed) in a workflow, A decider decides what to do next.

- Activity workers: Carry out activity tasks.


# SNS

- Amazon Simple Notification Service is a web service, that makes it easy to set up, operate and send notifications from the cloud.

- It provides developers with a highly scalable, flexible and cost effective capabiity to publish messages from an application and immediately deliver them to subscribers or other applications.
