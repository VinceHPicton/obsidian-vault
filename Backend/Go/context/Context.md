Context is a **signalling mechanism**, it's used to send cancellation signals, timeouts and rarely values, to other goroutines.

# The core idea
A `Context` is an object passed down through function calls:

`func doWork(ctx context.Context) error`

That `ctx` can tell you things like:
- “the user disconnected”
- “this request timed out”
- “the server is shutting down”
- “cancel everything derived from this operation”

# Cancellation
cancellation is **always cooperative in Go**, this means that context cancelling, timeouts, etc, send a signal to other goroutines, but they must be listening to that signal in some way for that to matter.