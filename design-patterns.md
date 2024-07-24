# Design Patterns

## Saga Design Pattern

https://medium.com/@dmosyan/how-did-uber-solve-data-consistency-problem-dcdd39bd3ed6

The Saga design pattern is a way to manage data consistency across microservices in distributed transaction scenarios. A saga is a sequence of transactions that updates each service and publishes a message or event to trigger the next transaction step. If a step fails, the saga executes compensating transactions that counteract the preceding transactions.

In simple words, if something goes wrong during a transaction (A transaction is a single unit of logic or work, sometimes made up of multiple operations), the previous changes should be reverted.
