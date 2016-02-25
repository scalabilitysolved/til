# Print out all requests that WireMock received

Sometimes when using WireMock it can be handy to know exactly which requests it received, you can easily do this via the following snippet (logging or Sysout the info needed):

```java
WireMock.findAll(RequestPatternBuilder.allRequests()).forEach(request -> System.out.println(request.getAbsoluteUrl()));
```