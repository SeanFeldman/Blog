I always found it interesting that most of us start counting earlier than we can read or spell out our own names.
Almost as if we are predispositioned to count first. Yet number can become very difficult to some later in the game.

Azure Service Bus client seems to be no exception to that either. With the "old school" client [(`WindowsAzure.ServiceBus`)][old-client] reading message counts was a trivial exercise.

While it looked simple and innocent, this operation is quite expensive and challenging on the broker side. Imagine a partitioned entity with 16 sections. To get message count, it would require to perform a query on all 16 brokers and aggregate the result to be served back to the client. Now imagine a "clueless" and "stubborn" client that just keeps pondering server side to get the counts every few seconds. You guessed it right, it's not ideal. Message counts were not designed to be queried frequently, and such an action is an abuse.

And that's why it's going to be deprecated from the new [client][new-client]. Full stop. What do you mean it will be gone?! How will it be possible to get message counts? Fear not. There's a way. Eventually.

But first, let's look at a bigger picture.



Microsoft.Azure.ServiceBus<p/>
Microsoft.Azure.Management.Monitor


[old-client]: https://www.nuget.org/packages/windowsazure.servicebus "WindowsAzure.ServiceBus"