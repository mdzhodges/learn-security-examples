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

   There is no sanitization of user inputs, allow for users to input malicious code in the form
   input. The vulnerability here is the potentially allowing an XSS attack.

2. Briefly explain how a malicious attacker can exploit them.

   A malicious attacker can inject a malicious input in the form to allow for the attack to occur.

3. Briefly explain why **secure.ts** does not have the same vulnerabilities?
   Secure.ts does not have the same vulnerabilities because the input from the form is being
   sanitized for HTML inputs. This is seen in the function  
   escapeHTML function. 