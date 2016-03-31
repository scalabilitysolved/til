# Play Framework XSS gotchas

One thing to note when using Play Framework and specifically Twirl templates is that using `@Html()` in your templates will implicility trust the content and *not* escape any of the HTML.