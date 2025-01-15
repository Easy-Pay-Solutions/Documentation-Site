---
description: How to authenticate with the Number backend
coverY: 0
layout:
  cover:
    visible: false
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# API Authentication (v1)

<figure><img src="../../../.gitbook/assets/Authentication Flow.png" alt=""><figcaption></figcaption></figure>

## Authentication

Both the REST and SOAP APIs provide their own methods for authenticating with Number. You will need to use them to receive the `Session Key`. To authenticate, you need to provide your `Account Code` and `Token`.



***



{% include "../../../.gitbook/includes/param-account-code.md" %}

***



{% include "../../../.gitbook/includes/param-token.md" %}

***



As a result of authentication, you will obtain a `Session Key`. This key is required to prove your identity when using any of the other methods provided by our backend.

**You will need to reauthenticate when one of the following two errors occurs:**&#x20;

{% hint style="danger" %}
**5030:** Expired Session Key (session key has expired after 25 hours)&#x20;
{% endhint %}

{% hint style="danger" %}
**5050:** Unauthorized Session Key (your IP has changed since you last authenticated)
{% endhint %}

The system will lock your IP out if you send 6 unsuccessful authentication attempts in a row. Always abort unsuccessful authentication attempts instead of retrying and notify the user. Only the Number support team can remove the lock from a merchant.

We recommend that you obtain and use the same `Session Key` until you receive one of those errors.



***



{% include "../../../.gitbook/includes/param-sess-key.md" %}



***



## Lockouts

When you authenticate, you will receive `FunctionOK` and `AuthSuccess` flags in the response. You should handle the response as follows:

1. Check the FunctionOK flag.
   1. If false, read the `ErrMsg` and `ErrCode`, and abort.
   2. If true, read the `AuthSuccess` flag.
      1. If `AuthSuccess` is false, read `RspMsg` and abort.
      2. If `AuthSuccess` is true, save the `SessKey` value.

Once again, it's important to abort unsuccessful authentication attempts and notify the user that new credentials need to be applied to the product.&#x20;

The system will lock your IP after 6 unsuccessful attempts in a row. When a lockout occurs, our support department will need to manually audit it to determine if it's safe to remove the lock.&#x20;



***



## Token Renewal

The Client Admin Portal will allow you to create and manage all of your tokens.  There is no limit to the number of tokens you can create. We recommend creating a separate token for each individual processing location (IP address).

Each token has a lifespan of 6 months since it was generated and will need to be replaced afterwards. This can only be done by physically logging into The Client Admin Portal. To make the process faster, The Client Admin Portal provides a way to POST new tokens to your web server to help automate a part of the renewal process.





