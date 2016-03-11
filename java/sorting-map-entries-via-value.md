# Sorting Map entries via value

Sometimes you'll have a map and need to sort the keys so that they are ordered by the value of corresponding their  _value_, with Java 8 it is super simple to achieve:

```java

		Map<String, Integer> sortedMap = map.entrySet()
				.stream()
				.sorted(reverseOrder(comparingByValue()))
				.collect(toMap(Entry::getKey, Entry::getValue, (e1, e2) -> e1, LinkedHashMap::new));
```
