# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Run the server __insecure.ts__.

3. Pretend to be a malicous user and interact with the services by sending requests from the browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.
    - The main vulnerability in insecure.ts is lack of authentication and logging. The application allows any user to retrieve messages without any form of verification or logging.
2. Briefly explain why the vulnerability is addressed in __secure.ts__.
    - Authentication: Before retrieving messages, an authentication check is performed to ensure only authorized users can access them. This prevents unauthorized users from retrieving or sending messages.
    - Logging: Each action, including message retrieval and errors, is logged with timestamps and user details, allowing administrators to monitor access, detect suspicious behavior, and respond to potential issues promptly.
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?
    - chaining, it first does one function, if that function has no errors or 'passes' then the next function is run.