Tests for data races among your code and the tests themselves.

A race is flagged when 2+ goroutines access the same memory location concurrently and at least one is writing to it, with no happens-before relationship between them (other code which ensures the access is in a specific order).

It's not a static analysis - it only reports races that *actually happened* during that run