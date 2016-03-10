# Find the Levenshtein distance between two Strings

Sometimes when comparing Strings you want a certain degree of flexibility when looking for matches due to typos, different spellings etc, you can easily achieve this by using Apache Commons and its handy `StringUtils.getLevenshteinDistance`.  This method returns the distance between two Strings as to how much they differ, examples below:

```java

import java.util.Arrays;

import org.apache.commons.lang3.StringUtils;

public enum NAMES {

	OWEN("Owen"), //
	HOLLIE("Hollie");

	private String name;

	private NAMES(String name) {
		this.name = name;
	}

	public static NAMES find(String name,int threshold) {
		return Arrays.stream(values())
				.filter(n -> StringUtils.getLevenshteinDistance(n.name, name) < threshold)
				.findFirst()
				.orElseThrow(() -> new IllegalArgumentException("NAME: " + name + " not found"));
	}

}
```

Then the subsequent tests of the above, by increasing the threshold we can make matching less rigid:

```java

	@Test
	public void shouldFindNameWithExactMatch() {
		val name = "Owen";
		val threshold = 1;
		assertThat(NAMES.find(name,threshold)).isEqualTo(NAMES.OWEN);
	}
	
	@Test(expected = IllegalArgumentException.class) 
	public void shouldNotFindNameViaLevenshteinMatch() {
		val name = "Holly";
		val threshold = 1;
		NAMES.find(name, threshold);
	}
	
	@Test() 
	public void shouldFindNameViaLevenshteinMatch() {
		val name = "Holly";
		val threshold = 3;
		assertThat(NAMES.find(name, threshold)).isEqualTo(NAMES.HOLLIE);
	}
```