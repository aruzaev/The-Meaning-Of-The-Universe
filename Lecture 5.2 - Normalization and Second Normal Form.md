# [[Lecture 5.2 - Normalization and Second Normal Form]]

Database must already be in first normal form

Second Normal Form (2NF) requires that any attribute that isn't a UID must be dependent on the entire UID, and not just a part of it (partial dependency)

Prohibits the use of partial dependencies on the composite keys

ex.

![[Pasted image 20240206103026.png]]
![[Pasted image 20240206103115.png]]

