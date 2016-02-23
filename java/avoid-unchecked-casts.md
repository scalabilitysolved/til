# Avoid unchecked casts

Often when dealing with different libraries you'll come across a wildcard return type like `List<?>`, usually people handle this like so (which generates an unchecked cast operation warning):

```java

	public void uncheckedCast() {
		List<User> users = (List<User>) getList();

		users.forEach(u -> System.out.println(u));
	}

	private List<?> getList() {
		return Arrays.asList(new User("Owen"), new User("Michael"));
	}

	@Data
	private class User {
		private final String name;
	}

```

With the streams API there is an elegant way to avoid these unchecked casts (assuming the same class and `getList` method as above):

```java

	
	public void withoutCastWarning() {
		List<User> users = getList().stream()
				.map(u -> (User) u)
				.collect(toList());

		users.forEach(u -> System.out.println(u));
	}
```








