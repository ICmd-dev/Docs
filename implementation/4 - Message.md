# Message
When inputs are too frequently, outputs can hardly "catch" up and cause latency. Among all factors, rendering is the predominant one slowing down the program. If another signal or update comes in when the renderer is busy, the update, which may be a crucial one, will be blocked behind or dropped. 

By intuition, we think of concurrency. We can spawn a daemon with a message queue in which every renderer-related signal is stored as _messages_.