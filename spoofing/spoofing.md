# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

    `$ npx install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. Start the malicious server **mal.ts**

    `npx ts-node mal.ts`

4. Open __http://localhost:8000__ in a browser, type a name and Submit.

5. Open the __Application__ tab in the Browser's inspect pane. Find the __Cookies__ under __Storage__. You should see a __connect.sid__ cookie being set.

6. Open the HTML file __mal-steal-cookie.html__ file in the same browser (different tab). Open inspect and view the console.

7. Click the link in the HTML file. Do you see the cookie being stolen in the console?

8. Open the HTML file __mal-csrf.html__ file in the same browser (different tab). What do you see if the user has not logged out of **insecure.ts**? What do you see if the user has logged out? 


## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.
    - The insecure.ts application uses a session configuration with httpOnly set to false, which allows JavaScript access to session cookies. This increases the risk of session hijacking, enabling attackers to spoof or impersonate users by stealing their session cookies.
2. Briefly explain different ways in which vulnerability can be exploited.
    - Attackers could exploit this by injecting malicious JavaScript that reads session cookies, especially on cross-site pages or if there’s an XSS vulnerability. 
3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.
    - In secure.ts, httpOnly is set to true, which prevents JavaScript from accessing session cookies, and sameSite is enabled to mitigate cross-site request forgery (CSRF) risks. 