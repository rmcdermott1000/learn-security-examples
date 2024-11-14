# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

    `npm install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

    ```
        <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
    ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
    - insecure.ts lacks XSS protection, allowing user input to be injected directly into responses without sanitization. This makes it vulnerable to cross-site scripting (XSS) attacks, where injected scripts could execute in users' browsers.
2. Briefly explain how a malicious attacker can exploit them.
    - An attacker could exploit this by submitting malicious HTML or JavaScript in the registration form. 
3. Briefly explain why **secure.ts** does not have the same vulnerabilties?
    - in secure.ts, the escapeHTML function sanitizes user input by encoding HTML special characters, preventing malicious HTML or JavaScript from being interpreted by the browser. 