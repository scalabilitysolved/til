# Apache commons bag structure for occurrences

Sometimes when working with collections we want to know how many times a particular elements exists in the collection, we can achieve this via the TIL [here](check-frequency-of-occurrences-in-a-list.md) or we can use the Apache Commons Bag that has some additional powerful methods baked in.

For example to find the occurrences of an elements in a collection we can do the following:

```java

	@Test
	public void shouldReportFrequency_UsingDataBag() {
		val integers = Lists.newArrayList(1,2,2,3);
		val bag = new HashBag<Integer>(integers);
		
		assertThat(bag.getCount(2)).isEqualTo(2);
	}
```

But also handily if we only want to work with those elements that are unique then we can access an immutable set from the databag too like so:

```java

	@Test
	public void shouldReportSet_OfUniqueInstances() {
		val integers = Lists.newArrayList(1,2,2,3);
		val bag = new HashBag<Integer>(integers);
		
		assertThat(bag.uniqueSet().size()).isEqualTo(3);
	}
```
