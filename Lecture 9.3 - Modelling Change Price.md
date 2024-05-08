# [[Lecture 9.3 - Modelling Change Price]]

Historical prices are important to model because they allow us to look for trends, determine if an item has appreciated or depreciated in price, and getting a refund for an item that has been purchased at a previous price

The prices of products change over time, some go up and some go down

## Modelling Historical Price

The start date is the id and the price would be the mandatory element

end price would be optional because sometimes periods of a price of an item don't have any gaps

You can usually derive the end date from the start date of the next item

![[Pasted image 20240409160145.png]]

However if the item is limited, like seasonal fruits, then they need to have an end date

## Tracking Price Changes

![[Pasted image 20240409160355.png]]

The price that was paid  can be found by matching the purchase date with the start and end date of PRICE

this cannot be modelled and must be documented and implemented with additional code in the system

## Journaling

Whenever the database allows us to modify information, we need to ask ourselves whether we need to log or journal the old values

i.e. keep old values in the record

This is mainly an issue of sensitive or financial things

![[Pasted image 20240409160719.png]]

Aside from the diagram, this needs to have added features implemented by programmimg

The information in the journal usually consists of the old value of the item and who it was modified by