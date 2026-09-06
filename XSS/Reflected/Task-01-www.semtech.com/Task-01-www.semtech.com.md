# A reflected Cross-Site Scripting (XSS) vulnerability was identified on `https://www.sierrawireless.com`

The search functionality on the affected page reflects user-controlled input into the application's response without adequate output encoding. By supplying a crafted XSS payload through the search input, an attacker can cause arbitrary JavaScript to execute in the context of `https://www.sierrawireless.com/resources/ebook/`.

The vulnerability was verified in Google Chrome using the browser's Developer Tools, and successful JavaScript execution was observed.

## Steps To Reproduce:

1. Navigate to the vulnerable page:

   `https://www.sierrawireless.com/resources/ebook/`

2. Locate the search box on the page.

3. Enter the following proof-of-concept payload into the search box:

   `<img src=x onerror=alert(1)>`

4. Submit the search.

5. Observe that the payload is reflected and the JavaScript executes, resulting in an `alert(1)` dialog.

6. The issue can be reproduced consistently using the affected search functionality.

## Impact

An attacker can craft a malicious URL or input containing JavaScript and potentially persuade a victim to interact with the affected search functionality.

When successfully triggered, attacker-controlled JavaScript executes in the security context of `www.sierrawireless.com`. Depending on the affected page, victim privileges, and available application functionality, this may allow an attacker to manipulate page content, perform actions available to the victim, or access information exposed to scripts running within the affected origin.

The attached proof-of-concept video demonstrates successful JavaScript execution.

## Author

Roshan Jeffrin R
