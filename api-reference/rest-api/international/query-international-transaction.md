# Query International Transaction

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Intl/QueryTransaction

_See Notes for Details_

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Query": "(F='328217c4-7059-11ef-a730-a6469c956913')&&(B=3)&&(E=1) "
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Intl_Transaction_QueryResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 1,
    "RespMsg": "Successfully Returned Transaction Records : 1",
    "Transactions": [
      {
        "Action": "SALE",
        "Address": "generating sale",
        "Amount": 0,
        "Card": "0042",
        "Card_Expiration_Date": "12\/2025",
        "Card_Token": "",
        "City": "Auburn",
        "Country": "US",
        "CreatedOn": "\/Date(1726071401083-0400)\/",
        "Currency": null,
        "Decline_Reason": "",
        "Descriptor": "",
        "Email": ndraper@easypaysolutions.com,
        "Fname": "Nancy",
        "ID": 570,
        "Lname": "Draper",
        "MerchID": 1,
        "Order_ID": "B7A6A9DF",
        "Phone": "",
        "PostalCode": "32658",
        "REFID": "",
        "RPGUID": "",
        "Recurring_Token": "",
        "Result": "SUCCESS",
        "Schedule_ID": null,
        "State": "ME",
        "Status": "SETTLED",
        "Trans_Date": "Sep 11 2024  4:16PM",
        "Trans_ID": "328217c4-7059-11ef-a730-a6469c956913",
        "bank_date": null,
        "chargeback_date": null,
        "reason_code": null
      }
    ]
  }
}
```
{% endtab %}

{% tab title="Header Parameters" %}
**SessKey** string <mark style="color:orange;">required</mark>

A unique session key used for authentication in API calls. This key is generated upon successful authentication and must be included in all subsequent requests.

Example: `A1842D663E9A4A72XXXXXXXX303541303234373138`

***

**Content-Type** string <mark style="color:orange;">required</mark>

Example: `application/json`

***

**Accept** string <mark style="color:orange;">required</mark>

Example: `application/json`
{% endtab %}

{% tab title="Notes" %}
#### Query Strings:

EasyPay provides a robust query language which provides a means for you to obtain specific records.

In order to Create a Query you will build logical terms and join them with Logical AND or Logical OR.

Use && for Logical AND

Use || for Logical OR

For instance, Let's say you want to return all records from merchant record 1 which were created in JUNE.

HERE IS THE QUERY: (A=1)&&(C>='6/1/2024')&&(C<'7/1/2024') (notice that any TEXT or DATES use a single Quote delimiter while numeric items do not)

Each Letter represents a variable and the following chart shows each meaning.

| A | MerchID        |
| - | -------------- |
| B | Status         |
| C | CreatedON      |
| D | LastName       |
| E | Result         |
| F | TransID        |
| J | FirstName      |
| L | Amount         |
| M | REFID          |
| Q | CardNum Last 4 |
| N | RPGUID         |
| W | ConsentID      |

EasyPay stores a copy of the transactional data on its servers. For international transactions data is stored in such a way that we may have multiple records in our system for a single credit card authorization or OrderID. Two Fields of Interest are **Result and Status**.

| Seq | OrderID  | Action | Result   | Status   |
| --- | -------- | ------ | -------- | -------- |
| 1   | 09B370DD | SALE   | REDIRECT | REDIRECT |
| 2   | 09B370DD | SALE   | REDIRECT | 3DS      |
| 3   | 09B370DD | SALE   | SUCCESS  | SETTLED  |

<br>

The above table shows three records we record as we process a single transaction on the International Processing Servers. As you request transaction information you are most likely only interested in the last entry which shows SUCCESS and SETTLED as the other two are simply intermediate steps.

The following shows query enum values for RESULT and STATUS and ACTION

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">2n6vZvQN9zHL</td><td valign="top">EjwQR8Q5V452</td><td valign="top">WH7YwoH1PsCs</td></tr><tr><td valign="top"><strong>E Result Values</strong></td><td valign="top"></td><td valign="top"></td></tr><tr><td valign="top">ALL</td><td valign="top">-1</td><td valign="top"></td></tr><tr><td valign="top">SUCCESS</td><td valign="top">1</td><td valign="top"></td></tr><tr><td valign="top">DECLINED</td><td valign="top">2</td><td valign="top"></td></tr><tr><td valign="top">REDIRECT</td><td valign="top">3</td><td valign="top"></td></tr><tr><td valign="top">ACCEPTED</td><td valign="top">4</td><td valign="top"></td></tr><tr><td valign="top">ERROR</td><td valign="top">5</td><td valign="top"></td></tr><tr><td valign="top">UNDEFINED</td><td valign="top">6</td><td valign="top"></td></tr><tr><td valign="top"><strong>B Status Values</strong></td><td valign="top"></td><td valign="top"></td></tr><tr><td valign="top">ALL</td><td valign="top">-1</td><td valign="top"></td></tr><tr><td valign="top">PENDING</td><td valign="top">1</td><td valign="top"></td></tr><tr><td valign="top">REDIRECT</td><td valign="top">2</td><td valign="top"></td></tr><tr><td valign="top">SETTLED</td><td valign="top">3</td><td valign="top"></td></tr><tr><td valign="top">REVERSAL</td><td valign="top">4</td><td valign="top"></td></tr><tr><td valign="top">REFUND</td><td valign="top">5</td><td valign="top"></td></tr><tr><td valign="top">DECLINED</td><td valign="top">6</td><td valign="top"></td></tr><tr><td valign="top">PENDING</td><td valign="top">7</td><td valign="top"></td></tr><tr><td valign="top">CHARGEBACK</td><td valign="top">8</td><td valign="top"></td></tr><tr><td valign="top">VOID</td><td valign="top">9</td><td valign="top"></td></tr><tr><td valign="top"><strong>G Action Values</strong></td><td valign="top"></td><td valign="top"></td></tr><tr><td valign="top">ALL</td><td valign="top">-1</td><td valign="top"></td></tr><tr><td valign="top">SALES</td><td valign="top">1</td><td valign="top"></td></tr><tr><td valign="top">CREDITVOID</td><td valign="top">2</td><td valign="top"></td></tr><tr><td valign="top">RECURRING_SALE</td><td valign="top">3</td><td valign="top"></td></tr></tbody></table>

So, to return all Transactions which are successfully settled please use the following query:

Result ➔ E Use 1 for Success

Status ➔ B Use 3 for Settled

Your query now becomes the following

{\
&#x20; "Query": "(B=3)&&(E=1)"\
}

***

You can further limit your query by specifying a Date Range

{\
&#x20; "Query": "(B=3)&&(E=1)&&(C>’2024-09-01’)"\
}

***

If you want to limit your results to transactions which are REFUNDS then use ACTION CREDITVOID

Or specifically (G=2)

{\
&#x20; "Query": "(B=3)&&(E=1)&&(C>'2024-09-01')&&(G=2)"\
}

***

If you want to limit your results to transactions which are Processed from stored Card use ACTION RECURRING\_SALE

Or specifically (G=3)

{\
&#x20; "Query": "(B=3)&&(E=1)&&(C>'2024-09-01')&&(G=3)"\
}

***

If you are looking for a particular transaction based on its unique TransID, you can do the following:

{\
&#x20; "Query": "(F='328217c4-7059-11ef-a730-a6469c956913')&&(B=3)&&(E=1) "\
}

***

This will return the transaction of interest without returning the intermediate steps as noted above.

If you want to query by Last name on a specific Date

{\
&#x20; "Query": "(C>'2024-09-16')&&(C<'2024-09-17')&&(D='SMITH')&&(B=3)&&(E=1)"\
}

***

If you are looking for a specific Amount

{\
&#x20; "Query": "(L=4.44)&&(B=3)&&(E=1)"\
}

***

If you are looking for a specific Amount within a date range

{\
&#x20; "Query": "(L=4.44)&&(C>'2024-09-16')&&(C<'2024-09-17')&&(B=3)&&(E=1)"\
}

***

If you are looking for a particular Card Number ( use last 4 digits ) for settled records

{\
&#x20; "Query": "(Q='1111')&&(B=3)&&(E=1)"\
}

***

If you are looking for a particular Reference ID

{\
&#x20; "Query": "(M='ABC 888')&&(B=3)&&(E=1)"\
}

***

If you are looking for a particular saved card transaction based on the ConsentID

{\
&#x20; "Query": "(W='c30eca54-75c1-11ef-b9e6-7aa481e33aa5')&&(B=3)&&(E=1)"\
}
{% endtab %}
{% endtabs %}

