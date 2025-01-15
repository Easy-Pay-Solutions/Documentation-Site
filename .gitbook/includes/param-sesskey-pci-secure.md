---
title: param - sesskey pci secure
---

`SessKey` string

A unique session key used for authentication in API calls with requests that directly pass the cardholder data. To create this key, use the value generated upon successful authentication, a 16-byte HMAC secret, a RSA certificate, and must be included in subsequent requests.

The format for the key is as follows: [`SessKey`](#user-content-fn-1)[^1]\_[`Epoch`](#user-content-fn-2)[^2]\_[`DeviceID`](#user-content-fn-3)[^3]\_[`Hash`](#user-content-fn-4)[^4].

Example: 9B9175EF556E4DDA93303132323141303035383339\_1702565789\_123\_1BD0C45A1DCBC7F9D0730FDD6222A45E10FCC7D9E84557499B812B138D0B7149

[^1]: &#x20;This key is generated upon successful authentication.

[^2]: Seconds since 1970 UTC

[^3]: UserID or DeviceID

[^4]: The HMAC hash created using the secret value which we will provide.
