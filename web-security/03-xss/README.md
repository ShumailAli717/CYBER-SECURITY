# Cross-Site Scripting (XSS)

## Platform: OWASP Juice Shop

## Challenge: DOM XSS
**Difficulty:** 1 star
**Location:** Search bar

**Payload used:**
<iframe src="javascript:alert(`xss`)">

**What happened:**
The search bar's input was being rendered directly into the DOM without
sanitization. When the iframe payload was entered into the search field,
the browser executed it and triggered a JavaScript alert box. This is
classified as DOM-based XSS because the vulnerability exists in the
client-side JavaScript code, not on the server.

**Why it worked:**
The application inserted the search term directly into the page without
properly encoding or sanitizing it first.

**Mitigation:**
User input should be sanitized/encoded before being inserted into the DOM
(e.g., using a library like DOMPurify), and unsafe methods like
`innerHTML` should be avoided for untrusted input.
