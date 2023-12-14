# [[Flexbox]]

The **main way to elements on a screen** and allows for full control over the positioning of an element

There are two types of boxes inside of flexbox:

1. Flex containers
2. Flex items

Every item that's a direct child of a *flex container* is a flex item

Flex containers are **responsible for** setting up the layout of the flex items

```
.menu-container {
	/* ... */
	display: flex;
}
```

Flex items are **responsible for** telling the container how many things it needs to position

```
.menu-item {
	/* ... */
	display: flex;
}
```
![[flex-container-and-flex-items-6234bb.7ffe361a.png]]
When you define flex containers you can mix and match flexbox with other layout tools such as [[floats]]

![[enabling-flexbox-dd3b59.cb39abcd.png]]

