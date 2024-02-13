# [[Lecture 5.2 - Normalization and Second Normal Form]]

**KEY POINT**: Partial dependency 

https://www.youtube.com/watch?v=mUtAPbb1ECM&list=PLLGlmW7jT-nTr1ory9o2MgsOmmx2w8FB3&index=2

Database must already be in first normal form

Recall that one or more attributes can be linked together to form more **meaningful unique identifiers called COMPOSITE KEYS**

Second Normal Form (2NF) requires that any attribute that isn't a UID must be dependent on the entire UID, and not just a part of it (partial dependency)

Partial dependency is also when there is an attribute that is **dependent on one half on the composite key but not on the other**

![[Pasted image 20240211113820.png]]

Prohibits the use of partial dependencies on the composite keys

ex.

![[Pasted image 20240206103026.png]]
![[Pasted image 20240206103115.png]]

