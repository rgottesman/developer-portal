## Organization authentication

Partners can create an admin token that is valid for twenty-four hours
to authenticate any requests sent during that time for a specific
organization.

**To generate an admin token for an organization:**

1.  Create an organization using the **POST /organizations** call.

-   curl --request POST https://api-prod.surfsight.net/v2/organizations
        --header 'Content-Type: application/json'
        --header 'Authorization: {token}'
        --data-raw '{

          "name": "organization 1"
        }'

    > **Note**
    >
    > This API call must be made by a user who is defined as a partner
    > in the system. If you do not have partner permission credentials
    > please reach out to your technical account manager to receive
    > partner API credentials.

    The API request returns two keys: **ssoSecret** and
    **organizationld**.

    > **Caution**
    >
    > Securely store these key values on your backend database. These
    > keys are not stored on the Surfsight system.

2.  Create a JWT token. You can use the following site:
    <https://jwt.io/>.

-   ![](media/image1.png){width="4.7573797025371825in"
    height="3.044722222222222in"}

    The following parameters must be set:

    -   current timestamp

    -   ssoSecret

    -   organizationId

    > **Note**
    >
    > The JWT token is valid for fifteen minutes. It is encrypted with
    > HS256 and sends private claims.

3.  Request an admin token with the **GET /organizations/sso** call.

-   Provide your JWT token in the authorization header.

        curl --request GET https://api-prod.surfsight.net/v2/organizations/sso
        --header 'Content-Type: application/json'
        --header 'Authorization: {JWT token}'

    > **Note**
    >
    > The admin token that is returned is valid for twenty-four hours.