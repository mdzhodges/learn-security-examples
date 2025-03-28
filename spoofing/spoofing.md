# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross
site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

   `$ npx install`

2. Start the **insecure.ts** server

   `npx ts-node insecure.ts`

3. Start the malicious server **mal.ts**

   `npx ts-node mal.ts`

4. Open __http://localhost:8000__ in a browser, type a name and Submit.

5. Open the __Application__ tab in the Browser's inspect pane. Find the __Cookies__ under __Storage
   __. You should see a __connect.sid__ cookie being set.

6. Open the HTML file __mal-steal-cookie.html__ file in the same browser (different tab). Open
   inspect and view the console.

7. Click the link in the HTML file. Do you see the cookie being stolen in the console?

8. Open the HTML file __mal-csrf.html__ file in the same browser (different tab). What do you see if
   the user has not logged out of **insecure.ts**? What do you see if the user has logged out?

## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.

The spoofing vulnerability in this file is due to the hardcoded string as the secret.
In addition to this, another vulnerability is the misconfiguration of the cookie. This
misconfiguration of the cookie cause the cookie to be seen from different domains.

2. Briefly explain different ways in which vulnerability can be exploited.

Due to the cookie configuration, a malicious attacker has the ability to steal the cookie for the
website from a different domain. This allows the attack to potentially
gain admin access if the cookie they steal happens to the be the admin's cookie.

3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.

It does not have a spoofing vulnerability because the secret is not hardcode.
In addition to this, the cookie is no longer visible from a different URL do to the
configuration of the cookie being stricter and correct.