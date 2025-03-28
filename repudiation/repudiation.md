# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting
to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

   `$ npm install`

2. Run the server __insecure.ts__.

3. Pretend to be a malicous user and interact with the services by sending requests from the
   browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.

The vulnerability is here due to there is no logging. Therefore there is no repudiation, which means
if the server was attacked, there would be no way to investigate the attack.

2. Briefly explain why the vulnerability is addressed in __secure.ts__.

The vulnerability is addressed because there are logs to see what requests are being received and
what responses are being sent. There is also an error log.

3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain
   how it works?

Single chain of responsibility. This is because each middleware function that is logging
information, it logs one piece of information we need, instead of one middleware recording all the
information. 