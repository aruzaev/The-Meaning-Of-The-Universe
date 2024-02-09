# [[Lecture 5.1 - Normalization and First Normal Form]]

**Normalization** is the process of creating a structure for a database in a way that reduces the **redundancy** of the data (how many times it's being repeated in different places) and to improve the **efficiency** of retrieving the data

e.x. storing your friend's phone number in your phone, address book, and on the fridge door is redundant

When data is stored in many different places, it makes it much harder to change and if you do decide to change it it can cause a lot of inconsistencies

"Every non-UID attribute must be dependent on the UID, the whole UID, and nothing but the UID"

One major goal when designing databases is to store information in one place which is **the best possible place**

## First Normal Form (1NF)

The First Normal Form requires that there are **no attributes** in the table that have **more than one value**

A way to check if a table is in violation of 1NF is by checking if each attribute has a single value for each entity

ex.

![[Pasted image 20240206085943.png]]

There can only be one value of the address for the building but there can be many values for classroom numbers, meaning that the top table is not in first form

If you do find out that an attribute is multi-valued and in violation of INF, then you can
> create an additional entity and relate it to the original one with a **1:M** relationship


![[Pasted image 20240206090830.png]]

![[Pasted image 20240206090854.png]]

