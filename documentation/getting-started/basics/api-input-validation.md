---
description: Basic details about input validation in the APIs
---

# API Input Validation (v1)

The following string values are validated within the APIs and will only allow a finite set of characters. If you send characters which are not allowed, you can receive an `ErrCode` of 7123.



<table><thead><tr><th width="236">Field / fields</th><th>Allowed characters</th></tr></thead><tbody><tr><td><code>Firstname</code>, <code>Lastname</code></td><td>Alphanumeric, single quote, minus sign, period, space, ampersand, comma, question mark, forward slash.</td></tr><tr><td><code>Company</code>, <code>Title</code></td><td>Alphanumeric, minus sign, period, pound sign, underscore, comma, ampersand, forward slash.</td></tr><tr><td><code>Address</code></td><td>Alphanumeric, minus sign, period, pound sign, underscore, comma, forward slash. Single quotes are stripped out.</td></tr><tr><td><code>City</code></td><td>Alpha, space, period.</td></tr><tr><td><code>State</code>, <code>Country</code></td><td>Alpha, space.</td></tr><tr><td><code>Zip</code></td><td>Alphanumeric, space, dash.</td></tr><tr><td><code>ClientRefID</code>, <code>RPGUID</code></td><td>Alphanumeric, minus sign, period, pound sign, comma, underscore, space, equal sign, ampersand. Single quotes are stripped out.</td></tr><tr><td><code>ServiceDescrip</code></td><td>Alphanumeric, space, underscore, period, pound sign, minus sign.</td></tr></tbody></table>



