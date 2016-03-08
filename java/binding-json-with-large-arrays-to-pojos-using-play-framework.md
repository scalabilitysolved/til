# Binding JSON with large arrays to POJOs using Play Framework

When using the Play Framework in Java you can bind Jackson ObjectNodes to a POJO via:

```java
		ObjectNode node = Json.newObject();
		//Assuming the node has additional data
		Form<User> bind = form(User.class).bind(node);
```

However assuming a class such as this:

```java
	@Data
	public class User{
		private List<String> followers;
	}
```

If your incoming JSON payload has more than 255 elements in the array (followers) then the form binding will blow up with a completely unrelated error, this is beacuse under the hood Play defaults to a maximum of 255 elements in an array for form binding.

To get around this limiation you can instead use the Play JSON class which will handle any sized array:

```java
	User user = Json.fromJson(node, User.class);
```