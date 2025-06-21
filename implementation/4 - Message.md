# 4 - Message
When inputs are too frequently, outputs can hardly "catch" up and cause latency. Among all factors, rendering is the predominant one slowing down the program. If another signal or update comes in when the renderer is busy, the update, which may be a crucial one, will be blocked behind or dropped. 

By intuition, we think of concurrency. We can spawn a daemon with a message queue with a fixed size in which every renderer-related signal is stored as _messages_. Then messages can be _trivial_ or _crucial_. Trivial messages can be dropped at any time when they are in the front of the queue and another one message wants to enqueue. Crucial messages can never be dropped even though there is another one message incoming, which, when in the front, simply rejects the incoming messages till it is popped out.

Rendering is a trivial message, which means it will be dropped when another message comes in, keeping latest updates prior to the old ones. With a refined queue size, display keeps in track of interaction smoothly with the message queue.
