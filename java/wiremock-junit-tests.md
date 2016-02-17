# Wiremock for stubbing out external APIs

Set up WireMock in Junit Tests by first declaring a Rule, adding a notifier of type `ConsoleNotifier` will enable verbose logging and is very useful when your requests aren't matching your stubbed routes.

```java
import org.junit.Rule;
import static com.github.tomakehurst.wiremock.core.WireMockConfiguration.wireMockConfig;

import com.github.tomakehurst.wiremock.common.ConsoleNotifier;
import com.github.tomakehurst.wiremock.junit.WireMockRule;

	@Rule
	public WireMockRule wireMockRule = new WireMockRule(wireMockConfig().port(MOCK_SEVER_PORT).notifier(new ConsoleNotifier(true)));
```

A nice utility method for stubbing out GET requests is like so (has dependecy on Lombok library), make sure to have your JSON files on the classpath


```java

	public void stubGet(String url, String responseFile, int code) {
		stubFor(get(urlEqualTo(url)).willReturn(aResponse().withStatus(code).withBody(getResponse(responseFile))));
	}
	
	@SneakyThrows
	public String getResponse(String file) {
		URL systemResource = ClassLoader.getSystemResource("responses/" + file + ".json");
		Path responseFilePath = Paths.get(systemResource.toURI());
		return new String(Files.readAllBytes(responseFilePath));
	}
```

When needing to simulate delays in your stubbed service you can apend `withFixedDelay` to the response like so:

```java
	public void stubGetWithDelay(String url, String responseFile, int code,int delay) {
		stubFor(get(urlEqualTo(url)).willReturn(aResponse().withStatus(code).withFixedDelay(delay).withBody(getResponse(responseFile))));
	}
```