Challenge: This Web Is Too Simple

Category: Web

> A very simple web challenge

So I started off by doing SQL Injection on the login page:

![One](./one.png)
![Two](./two.png)

Then you see this:

> {"message":"Login Successful, This is your key: E9bYhRnW9P5QRtEdwsv15pJX"}

I had no idea what this meant :)
So I went round doing weird stuff like trying to change the query to include this "key" + searching random stuff under "Applications"..

![Wat](./wat.png)

I found this auth_token string:

> eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoibm9uLWFkbWluIiwiaWF0IjoxNzEwMjYyOTA5LjMyNjkzNCwiZXhwIjoxNzEwMjYyOTY5LjMyNjkzNH0.DRDNrFlRKPAmFtXaQ_KQDtYW0oapkpSnSEnj7Ed7lz8

I googled it an eventually found this write up:

https://www.linkedin.com/pulse/solving-json-web-token-challenge-mendix-ctf-2022-niels-de-haas/

Which basically told me everything I needed to know - slap the auth_token string into the encoded section and tweak it.

![Waw](./waw.png)

- Changed non-admin to admin
- Changed the exp time (because im slow)
- Added the "key" into the verify signature

Copy the new token + replace the old auth_token:

![flag](./flag.png)
