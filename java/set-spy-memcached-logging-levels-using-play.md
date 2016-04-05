# Set Spy-Memcached logging levels using Play Framework

When using Play Framework and Spy-Memcached the following won't automatically work in your logger.xml file:

```xml
    <logger name="net.spy.memcached" level="WARN">
        <appender-ref ref="DAILY-ROLLING-ASYNC" />
    </logger>
```

For some reason Spy-Memcached doesn't automatically pick up the settings unlike other components (Hibernate/Spring etc). To work around this you need to call the following method and then Spy-Memcached will respect whatever logging levels you set:

```java
	private void configureLogger() {
		Properties systemProperties = System.getProperties();
		systemProperties.put("net.spy.log.LoggerImpl", "net.spy.memcached.compat.log.SLF4JLogger");
		System.setProperties(systemProperties);
	}
```