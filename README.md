# MessagingCentre

A small, fast communication layer allowing message-based communication between publisher and subscriber object without any references needed.

# Subscribing

```c#

// Subscribe to a message using an existing method
MessagingCentre.Subscribe<TPublisher>(this, "messageToSubTo", callbackDelegate);

// Subscribe to a message using an anonymous delegate
MessagingCentre.Subscribe<TPublisher>(this, "messageToSubTo", (sender) =>
{
    // messageToSubTo has been published
});

// Subscribe to a message that contains data
MessagingCentre.Subscribe<TPublisher, TArgs>(subscriberObject, "messageToSubTo", (sender, args) =>
{
    // messageToSubTo has been published with args
});

```

# Publishing

```c#

// Publish a simple message
MessagingCentre.Publish<TPublisher>(this, message);

// Publish a message with payload data
MessagingCentre.Publish<TPublisher, int>(this, message, 12);
MessagingCentre.Publish<TPublisher, string>(this, message, "Data to go with message");
MessagingCentre.Publish<TPublisher, MessageData>(this, message, new MessageData{ Id = 12, Date = DateTime.Now });

```

# Unsubscribing

```c#

// Unsubscribe from messsages with and without data
MessagingCentre.Unsubscribe<TPublisher>(this, "messageToUnsubFrom");
MessagingCentre.Unsubscribe<TPublisher, string>(this, "messageToUnsubFrom")

```
