# Type inference using Lombok

Outside of a pretty sketchy looking site [Lombok](https://projectlombok.org/index.html) adds loads of great features to Java, who said Java couldn't have type inference?

```java

package com.scalesolved.lombok;

import static org.fest.assertions.Assertions.assertThat;
import lombok.val;

import org.junit.Test;

public class LombokPlayground {

	@Test
	public void shouldUseLombokTypeInference() {
		val admin = new Admin();
		assertThat(admin).isInstanceOf(Admin.class);
	}

	public class Admin {}
}

```