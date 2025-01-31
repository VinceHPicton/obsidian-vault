This is a free optimization that can be used on Java, Python and .NET Lambdas.

How it works:
- on publishing a new version of the lambda it is immediately initialized
- a snapshot is taken of the disk state to be used later
- This snapshot can be used to very quickly pre-initialise to make calling the lambda much faster

![[Lambda SnapStart.png]]