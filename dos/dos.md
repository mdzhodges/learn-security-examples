# Denial-of-Service (DoS)

This example demonstrates DoS vulnerabilities and how they can be exploited.

## Steps to reproduce

1. Install all dependencies

   `$ npm install`

2. Ignore if you have already done this once. Insert test data in the MongoDB database. Make sure
   the mongod is up and running by typing the `mongosh` command in the termainal. If mongod process
   is up then you will see that the connection was successful. Command to insert test data:

   `$ npx ts-node insert-test-users.ts`

This will create a database in MongoDB called __infodisclosure__. Verify its presence by connecting
with mongosh and running the command `show dbs;`.

2. Start the **insecure.ts** server

   `$ npx ts-node insecure.ts`

3. In the browser, pretend to be a hacker and type a malicious request

    ```
        http://localhost:3000/userinfo?id[$ne]=
    ```

4. Do you see the server crashing?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts** that can lead to a DoS attack.

There are 2 potential vulnerability in insecure.ts. The first vulnerability is the ability for a
single use to send many requests, possibility causing a server crash.
In addition to this, there is also a potential for a NOSQL attack which could crash the server do to
a type error.

2. Briefly explain how a malicious attacker can exploit them.

A malicious attack can exploit the server by sending an invalid ID to the end point would crash the
server. In addition to this, sending many requests could also crash the server.

3. Briefly explain the defensive techniques used in **secure.ts** to prevent the DoS vulnerability?

Secure.ts sanitizes the ID to make the format acceptable for the mongo query. In addition to this,
add error handling to the server to prevent the server from crashing. Lastly, there is a rate limit
set to prevent too many requests from being set.
