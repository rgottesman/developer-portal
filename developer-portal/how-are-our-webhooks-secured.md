### How are our webhooks secured?

Webhooks are secured through anonymity - every user gets a unique,
random URL to send webhook data to.

For extra security, all webhook information sent by Surfsight to your
application contains an additional header attribute:
**X-Surfsight-Signature**. The signature is created using the
destination URL, the ssoSecret of your organization, and the content of
the request. The signature should appear similar to:
29c4198c5e3da799887deaf0b0450bac8880efc0769cb79b97138ce9888a4308c7211415879152fdc4a14933c77cd4d531e71a29008214360ce340ccf49b87c8.