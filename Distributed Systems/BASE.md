BASE = Basically Available, Soft state, Eventually consistent.
This acronym was forced so that it could be the opposite of [[ACID]]

A BASE database prioritize availability over consistency. Sometimes the data can be wrong, but *eventually* it will be all ironed out. For this you get increase availability, a DB transaction can partially complete in the moment and be finished at a later time, meaning more availability (less erroring)

NoSQL databases use BASE architecture