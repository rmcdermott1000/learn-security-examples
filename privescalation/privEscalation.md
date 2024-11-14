# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

    ```
        http://localhost:3000/send-form
    ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
    - The main vulnerability in insecure.ts is its lack of secure authentication and authorization controls. It relies on user input (userId) within the request body to identify and authorize the user, allowing non-admin users to escalate their privileges by simply setting their userId to that of an admin.
2. Briefly explain how a malicious attacker can exploit them.
    - An attacker could exploit this vulnerability by crafting a request to the /update-role route, setting their userId to the ID of an admin in the request body.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
    - Session-Based Authentication: The session middleware is used to store the authenticated user’s ID in the session (req.session.userId). This ensures the server can identify the actual logged-in user without relying on user-provided userId in requests.
    - Role-Based Authorization: Once authenticated, the server checks the user’s role based on session data, ensuring only users with an admin role can update roles.