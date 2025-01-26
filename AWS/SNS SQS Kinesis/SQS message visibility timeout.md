- When a message is polled by a consumer it becomes invisible to other consumers for **by default** 30 seconds, in order to prevent duplicate processing.
	- Remember that a consumer must delete the message after processing as a separate action
- This can mean that a message could be processed twice if processing takes too long.
- However a consumer can extend the deadline by calling the ChangeMessageVisiblity API.
- You can't just make the timeout hours, because if a consumer were to crash, the message wouldn't be available for reprocessing for hours!
- Setting it too low will cause duplication of efforts by message consumers.
- 
![[SQS message visibility timeout.png]]

