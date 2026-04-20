A network partition is a failure scenario which occurs when some parts of a distributed system can't talk to eachother, even though each part is still running. It's often called a "split brain" scenario.

If you had 3 servers in London, New York, and Sydney, the network could suddenly drop such that eg London and Sydney cannot communicate, or maybe London is completely isolated from the other 2.

If this happens you hit the [[CAP theorem]] problem, do you start rejecting requests or do you start serving possibly conflicting data (as they can't communicate) from London vs Sydney?