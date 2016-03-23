# Extract links from a String

Yesterday I needed to extract all links from a String, ideally I wanted a solution where I didn't have to write any Regexes, I stumbled across the handy little library [Autolink-Java](https://github.com/robinst/autolink-java).

Using it like so the following method will produce a List of all links contained within the String

```java
	public List<String> extractLinks(String body) {
		LinkExtractor linkExtractor = LinkExtractor.builder()
				.linkTypes(Sets.newHashSet(LinkType.URL))
				.build();

		return Lists.newArrayList(linkExtractor.extractLinks(body))
				.stream()
				.map(link -> body.substring(link.getBeginIndex(), link.getEndIndex()))
				.collect(toList());
	}
```