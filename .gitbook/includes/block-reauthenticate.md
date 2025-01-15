---
title: block - reauthenticate
---

You will need to reauthenticate when one of the following two errors occur:&#x20;

* 5030: Expired Session Key (session key has expired after 25 hours)&#x20;
* 5050: Unauthorized Session Key (your IP has changed since you last authenticated)

The system will lock your IP out if you send 6 unsuccessful authentication attempts in a row. Always abort unsuccessful authentication attempts instead of retrying and notify the user. Only the Number support team can remove the lock from a merchant.
