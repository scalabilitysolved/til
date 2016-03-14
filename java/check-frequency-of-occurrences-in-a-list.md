# Check frequency of occurrences in a List 

If you have a list and you want to know how many times a paticular object is contained within the list then the `Collections` class offers a handy `frequency` method that works like so:

```java

	@Test
	public void shouldReportFrequencyOfTwo() {
		val integers = Lists.newArrayList(1,2,2,3);
		assertThat(Collections.frequency(integers, 2)).isEqualTo(2);
	}
```