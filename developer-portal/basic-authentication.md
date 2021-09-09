## Basic authentication

Surfsight API uses Bearer authentication (also known as token
authentication). The server generates a bearer token in response to a
login request. The client provides this token in the **Authorization**
header when making further requests.

    --header 'Authorization: ImahFWLZWFdD8VVcUtIED2YuOjPFlZpldQTE5tUqKdv'

You need an email address and password to get a token. When beginning
your partnership with Surfsight, we send you an email containing this
information.

> **Note**
>
> Every company can request up to nineteen additional usernames.

**To receive an authentication token:**

Make the **POST /authentication** call. Enter the email address and
password you received in an email from a Surfsight agent in the request
body and an authentication token is returned.

    curl --request POST 'https://api-prod.surfsight.net/v2/authentication'
    --header 'Content-Type: application/json'
    --data-raw '{

      "email": "email@email.com",
      "password": "123Abcd!"
    }'

> **Note**
>
> The token that is returned is valid for twenty-four hours.