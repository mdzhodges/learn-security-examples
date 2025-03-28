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

4. Try different UserIds and see which one gives you authorized access to change the role of that
   user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**

There is privileged escalation in insecure.ts because of how the role of the user is being
validated. This is because of this allows a user to downgrade the role of admin to user because it
uses attacker controller variables.

2. Briefly explain how a malicious attacker can exploit them.

If the attacker simply enters 1 into the userID, then enter user into the role field, the role is
admin will be updated to user.

3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege
   escalation vulnerability?

In secure.ts, it is reading the userID's from the session. It will also check if the userID is set
in the session. If the user has not been loggedIn before, then the update will not work, preventing
privilege escalation.