# [[Lecture 5.3 - Normalization and Third Normal Form]]

**KEY POINT**: Transitive dependency

https://www.youtube.com/watch?v=aAx_JoEDXQA&list=PLLGlmW7jT-nTr1ory9o2MgsOmmx2w8FB3&index=4

Database must already be in first and second form

No transitive dependencies - All fields must be only determinable by the primary/composite keys, not by other keys

**A transitive dependency is when there is a dependency between two non primary key attributes** trans = across or in the middle of

3rd form violation:

![[Pasted image 20240211115354.png]]

You can fix this by separating the exam_name and total_marks attributes into a separate table called EXAM and setting exam_name as the primary key that can be linked in the SCORE table

![[Pasted image 20240211115604.png]]
![[Pasted image 20240206103839.png]]

Here, the winner's DOB is dependant on the winner attribute, which is a non primary key attribute. Because of this, it is a **transitive dependancy**

You can fix this by separating the winner and winner's dob attributes into a separate table and set winner as a primary key in a new table and then as a secondary key linked in the initial table


![[Screenshot 2024-02-06 at 10.38.53 AM.png]]