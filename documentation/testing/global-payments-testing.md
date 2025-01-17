# Global Payments Testing

***



### Test cards

{% hint style="info" %}
**Note:** To receive a FULL CVV MATCH, please use the follow CVV listed in the below table!
{% endhint %}

<table data-full-width="false"><thead><tr><th width="134">Card Brand</th><th width="201">Card Number</th><th width="104">EXP Date</th><th width="82">CVV</th><th width="513">Track Data</th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/1 Visa icon.png" alt="" data-size="original"></td><td>4012 0000 9876 5439</td><td>12/28</td><td>999</td><td>%B4012000098765439^TSYS PAYMENT^25121011796251900000?;4012000098765439=25121011796251900000?</td></tr><tr><td><img src="../../.gitbook/assets/1 Visa icon.png" alt="" data-size="original"></td><td>4012 8818 8881 8888</td><td>12/28</td><td>999</td><td>%B4012881888818888^TSYS PAYMENT^25121011796251900000?;4012881888818888=25121011796251900000?</td></tr><tr><td><img src="../../.gitbook/assets/1 Master card icon.png" alt="" data-size="original"></td><td>5146 3150 0000 0055</td><td>12/28</td><td>998</td><td>%B5146315000000055^TSYS PAYMENT^251210100000?;5146315000000055=251210100000?</td></tr><tr><td><img src="../../.gitbook/assets/1 Master card icon.png" alt="" data-size="original"></td><td>5146 3122 0000 0035</td><td>12/28</td><td>998</td><td>%B5146312200000035^TSYS PAYMENT^251210100000?;5146312200000035=251210100000?</td></tr><tr><td><img src="../../.gitbook/assets/1 Master card icon.png" alt="" data-size="original"></td><td>5146 3126 2000 0045</td><td>12/28</td><td>998</td><td></td></tr><tr><td><img src="../../.gitbook/assets/1 Amex icon.png" alt="" data-size="original"></td><td>3714 4963 5392 376</td><td>12/28</td><td>9997</td><td>%B371449635392376^TSYS PAYMENT^251210100000?;371449635392376=251210100000?</td></tr><tr><td><img src="../../.gitbook/assets/1 Discover icon.png" alt="" data-size="original"></td><td>6011 0009 9302 6909</td><td>12/28</td><td>996</td><td>%B6011000993026909^TSYS PAYMENT^251210100000?;6011000993026909=251210100000?</td></tr></tbody></table>



***



### <img src="../../.gitbook/assets/1 Visa icon.png" alt="" data-size="original">

### VISA - Penny Codes

<table><thead><tr><th width="196">Request Value</th><th width="159">Response Code</th><th width="397">Response Text</th></tr></thead><tbody><tr><td>$0.00</td><td>85</td><td>Card Ok</td></tr><tr><td>$0.01</td><td>01</td><td>Call Issuer</td></tr><tr><td>$0.02</td><td>02</td><td>Call Issuer, Special Cond.</td></tr><tr><td>$0.03</td><td>28</td><td>File Temp. Unavailable</td></tr><tr><td>$0.04</td><td>91</td><td>Issuer Unavailable or Inoperative, No STIP</td></tr><tr><td>$0.05</td><td>04</td><td>Pick Up Card</td></tr><tr><td>$0.06</td><td>07</td><td>Pick Up Card, Special Cond.</td></tr><tr><td>$0.07</td><td>41</td><td>Pick Up Card, Lost</td></tr><tr><td>$0.08</td><td>43</td><td>Pick Up Card, Stolen</td></tr><tr><td>$0.09</td><td>06</td><td>General Error</td></tr><tr><td>$0.10</td><td>79</td><td>Already Reversed</td></tr><tr><td>$0.11</td><td>13</td><td>Invalid amount</td></tr><tr><td>$0.12</td><td>83</td><td>Can't Verify PIN</td></tr><tr><td>$0.13</td><td>86</td><td>Can't Verify PIN</td></tr><tr><td>$0.14</td><td>14</td><td>Invalid Account Number</td></tr><tr><td>$0.15</td><td>82</td><td>Incorrect CVV</td></tr><tr><td>$0.16</td><td>N3</td><td>Cashback Not Available</td></tr><tr><td>$0.17</td><td>06</td><td>General Error</td></tr><tr><td>$0.18</td><td>EC</td><td>CID Format Error</td></tr><tr><td>$0.19</td><td>80</td><td>No Financial Impact</td></tr><tr><td>$0.20</td><td>05</td><td>Decline</td></tr><tr><td>$0.21</td><td>51</td><td>Decline</td></tr><tr><td>$0.22</td><td>N4</td><td>Decline</td></tr><tr><td>$0.23</td><td>61</td><td>EXC APPR AMT LIM</td></tr><tr><td>$0.24</td><td>62</td><td>Decline</td></tr><tr><td>$0.25</td><td>65</td><td>EXC W/D FREQ LIM</td></tr><tr><td>$0.26</td><td>93</td><td>Decline</td></tr><tr><td>$0.27</td><td>81</td><td>Encryption Error</td></tr><tr><td>$0.28</td><td>06</td><td>General Error</td></tr><tr><td>$0.29</td><td>54</td><td>Expired Card</td></tr><tr><td>$0.30</td><td>92</td><td>Invalid Routing</td></tr><tr><td>$0.31</td><td>12</td><td>Invalid Trans</td></tr><tr><td>$0.32</td><td>78</td><td>No Account</td></tr><tr><td>$0.33</td><td>21</td><td>No action taken</td></tr><tr><td>$0.34</td><td>76</td><td>Unsolic Reversal</td></tr><tr><td>$0.35</td><td>77</td><td>No action taken</td></tr><tr><td>$0.36</td><td>52</td><td>No Check Account</td></tr><tr><td>$0.37</td><td>39</td><td>No Credit Acct</td></tr><tr><td>$0.38</td><td>53</td><td>No Save Acct</td></tr><tr><td>$0.39</td><td>15</td><td>No Such Issuer</td></tr><tr><td>$0.40</td><td>75</td><td>PIN Exceeded</td></tr><tr><td>$0.41</td><td>19</td><td>RE-ENTER</td></tr><tr><td>$0.42</td><td>63</td><td>SEC Violation</td></tr><tr><td>$0.43</td><td>57</td><td>Txn not permitted</td></tr><tr><td>$0.44</td><td>58</td><td>Serv Not Allowed</td></tr><tr><td>$0.45</td><td>96</td><td>System Error</td></tr><tr><td>$0.46</td><td>03</td><td>Term ID Error</td></tr><tr><td>$0.47</td><td>55</td><td>Wrong PIN</td></tr><tr><td>$0.48</td><td>N7</td><td>CVV Mismatch</td></tr><tr><td>$0.49</td><td>85</td><td>Card OK</td></tr><tr><td>$0.50*</td><td>00</td><td>APPROVAL</td></tr><tr><td>$0.54</td><td>94</td><td>Duplicate Transaction</td></tr><tr><td>$0.96</td><td>R0</td><td>Stop Recurring</td></tr><tr><td>$0.97</td><td>R1</td><td>Revoke Auth Order</td></tr><tr><td>$1.12</td><td>05</td><td>Decline</td></tr><tr><td>$1.13</td><td>05</td><td>Decline</td></tr><tr><td>$1.30</td><td>00</td><td>Approval</td></tr><tr><td>$1.31</td><td>00</td><td>Approval</td></tr><tr><td>$1.34</td><td>30</td><td>Msg Format Error</td></tr><tr><td>$10.00</td><td>00</td><td>Approval</td></tr><tr><td>$32.48</td><td>00</td><td>Approval</td></tr><tr><td>$32.88</td><td>25</td><td>No Card Number</td></tr><tr><td>$1.34</td><td>30</td><td>Msg Format Error</td></tr><tr><td>$32.85</td><td>11</td><td>Approval</td></tr><tr><td>$64.01</td><td>89</td><td>Ineligible GIV</td></tr><tr><td>$64.02</td><td>H6</td><td>Fail Get BDK</td></tr><tr><td>$64.03</td><td>H7</td><td>Fail Get KPEI</td></tr><tr><td>$64.04</td><td>H8</td><td>Encryption Error</td></tr><tr><td>$64.05</td><td>N9</td><td>System Error</td></tr><tr><td>$64.06</td><td>N6</td><td>N6 Error</td></tr><tr><td>$64.10</td><td>46</td><td>Closed Account</td></tr><tr><td>$64.11</td><td>59</td><td>Suspected Fraud</td></tr><tr><td>$64.12</td><td>6P</td><td>Verification Data Failed</td></tr></tbody></table>



***



### <img src="../../.gitbook/assets/1 Master card icon.png" alt="" data-size="original">

### Master Card - Penny Codes

<table><thead><tr><th width="196">Request Value</th><th width="159">Response Code</th><th width="397">Response Text</th></tr></thead><tbody><tr><td>$0.01</td><td>01</td><td>Call Issuer</td></tr><tr><td>$0.05</td><td>04</td><td>Capture Card</td></tr><tr><td>$0.07</td><td>41</td><td>Lost Card</td></tr><tr><td>$0.08</td><td>43</td><td>Stolen Card</td></tr><tr><td>$0.14</td><td>14</td><td>Invalid Account</td></tr><tr><td>$0.29</td><td>54</td><td>Expired Card</td></tr><tr><td>$0.30</td><td>92</td><td>Invalid Routing</td></tr><tr><td>$0.31</td><td>12</td><td>Invalid Transaction</td></tr><tr><td>$0.39</td><td>15</td><td>No Such Issuer</td></tr><tr><td>$32.85</td><td>08</td><td>Honor With ID</td></tr></tbody></table>



***



### <img src="../../.gitbook/assets/1 Amex icon.png" alt="" data-size="original">

### American Express - Penny Codes

<table><thead><tr><th width="196">Request Value</th><th width="159">Response Code</th><th width="397">Response Text</th></tr></thead><tbody><tr><td>$0.05</td><td>04</td><td>Pick Up Card</td></tr><tr><td>$0.11</td><td>13</td><td>Invalid amount</td></tr><tr><td>$0.14</td><td>14</td><td>Invalid Account Number</td></tr><tr><td>$0.18</td><td>EC</td><td>CID Format Error</td></tr><tr><td>$0.19</td><td>80</td><td>No Financial Impact</td></tr><tr><td>$0.20</td><td>05</td><td>Decline</td></tr><tr><td>$0.29</td><td>54</td><td>Expired Card</td></tr><tr><td>$0.44</td><td>58</td><td>Serv Not Allowed</td></tr><tr><td>$1.00</td><td>00</td><td> </td></tr><tr><td>$1.01</td><td>00</td><td> </td></tr><tr><td>$1.02</td><td>11</td><td></td></tr><tr><td>$1.03</td><td>08</td><td></td></tr><tr><td>$1.04</td><td>03</td><td></td></tr><tr><td>$1.05</td><td>01</td><td></td></tr><tr><td>$1.06</td><td>01</td><td></td></tr><tr><td>$1.07</td><td>05</td><td></td></tr><tr><td>$1.08</td><td>05</td><td></td></tr><tr><td>$1.09</td><td>03</td><td></td></tr><tr><td>$1.10</td><td>06</td><td></td></tr><tr><td>$1.11</td><td>75</td><td></td></tr><tr><td>$1.12</td><td>55</td><td></td></tr><tr><td>$1.13</td><td>57</td><td></td></tr><tr><td>$1.14</td><td>96</td><td></td></tr><tr><td>$1.15</td><td>91</td><td></td></tr><tr><td>$12.00</td><td>00</td><td></td></tr><tr><td>$15.00</td><td>10</td><td></td></tr></tbody></table>



***



### <img src="../../.gitbook/assets/1 Discover icon.png" alt="" data-size="original">

### Discover - Penny Codes

<table><thead><tr><th width="196">Request Value</th><th width="159">Response Code</th><th width="397">Response Text</th></tr></thead><tbody><tr><td>$10.01</td><td>06</td><td> </td></tr><tr><td>$10.02</td><td>06</td><td> </td></tr><tr><td>$10.03</td><td>03</td><td> </td></tr><tr><td>$10.04</td><td>04</td><td> </td></tr><tr><td>$10.05</td><td>05</td><td> </td></tr><tr><td>$10.07</td><td>07</td><td> </td></tr><tr><td>$10.08</td><td>06</td><td> </td></tr><tr><td>$10.10</td><td>10</td><td> </td></tr><tr><td>$10.11</td><td>00</td><td> </td></tr><tr><td>$10.12</td><td>12</td><td> </td></tr><tr><td>$10.13</td><td>13</td><td></td></tr><tr><td>$10.14</td><td>14</td><td></td></tr><tr><td>$10.15</td><td>06</td><td></td></tr><tr><td>$10.19</td><td>19</td><td></td></tr><tr><td>$10.30</td><td>30</td><td></td></tr><tr><td>$10.31</td><td>15</td><td></td></tr><tr><td>$10.33</td><td>06</td><td></td></tr><tr><td>$10.34</td><td>06</td><td></td></tr><tr><td>$10.35</td><td>06</td><td></td></tr><tr><td>$10.36</td><td>06</td><td></td></tr><tr><td>$10.37</td><td>06</td><td></td></tr><tr><td>$10.38</td><td>75</td><td></td></tr><tr><td>$10.39</td><td>39</td><td></td></tr><tr><td>$10.40</td><td>12</td><td></td></tr><tr><td>$10.41</td><td>41</td><td></td></tr><tr><td>$10.43</td><td>43</td><td></td></tr><tr><td>$10.51</td><td>05</td><td></td></tr><tr><td>$10.53</td><td>53</td><td></td></tr><tr><td>$10.54</td><td>54</td><td></td></tr><tr><td>$10.55</td><td>55</td><td></td></tr><tr><td>$10.56</td><td>14</td><td></td></tr><tr><td>$10.57</td><td>57</td><td></td></tr><tr><td>$10.58</td><td>58</td><td></td></tr><tr><td>$10.59</td><td>05</td><td></td></tr><tr><td>$10.60</td><td>01</td><td></td></tr><tr><td>$10.61</td><td>61</td><td></td></tr><tr><td>$10.62</td><td>62</td><td></td></tr><tr><td>$10.63</td><td>63</td><td></td></tr><tr><td>$10.66</td><td>77</td><td></td></tr><tr><td>$10.65</td><td>65</td><td></td></tr><tr><td>$10.66</td><td>01</td><td></td></tr><tr><td>$10.67</td><td>04</td><td></td></tr><tr><td>$10.68</td><td>06</td><td></td></tr><tr><td>$10.67</td><td>04</td><td></td></tr><tr><td>$10.68</td><td>06</td><td></td></tr><tr><td>$10.75</td><td>75</td><td></td></tr><tr><td>$10.76</td><td>14</td><td></td></tr><tr><td>$10.77</td><td>14</td><td></td></tr><tr><td>$10.78</td><td>14</td><td></td></tr><tr><td>$10.79</td><td>85</td><td></td></tr><tr><td>$10.87</td><td>91</td><td></td></tr><tr><td>$10.91</td><td>91</td><td></td></tr><tr><td>$10.92</td><td>92</td><td></td></tr><tr><td>$10.93</td><td>93</td><td></td></tr><tr><td>$10.94</td><td>94</td><td></td></tr><tr><td>$10.96</td><td>96</td><td></td></tr><tr><td>$10.97</td><td>D3</td><td></td></tr></tbody></table>



***



## Address Verification Service Responses <a href="#address-verification-service-responses" id="address-verification-service-responses"></a>

<table><thead><tr><th width="196">Response Code</th><th width="159">CustomerZip</th><th width="397">Response Text</th></tr></thead><tbody><tr><td>Z</td><td>85284</td><td>Zip Match</td></tr><tr><td>U</td><td>99999</td><td>Ver Unavailable</td></tr><tr><td>G</td><td>99998</td><td>Ver Unavailable</td></tr><tr><td>B</td><td>999970001</td><td>Address Match</td></tr><tr><td>C</td><td>999970002</td><td>Serv Unavailable</td></tr><tr><td>D</td><td>999970003</td><td>Exact Match</td></tr><tr><td>I</td><td>999970004</td><td>Ver Unavailable</td></tr><tr><td>M</td><td>999970005</td><td>Exact Match</td></tr><tr><td>P</td><td>999970006</td><td>Zip Match</td></tr><tr><td>A</td><td>999970007</td><td>Address Match</td></tr><tr><td>Y</td><td>999970008</td><td>Exact Match</td></tr></tbody></table>

**To receive a FULL AVS AND CVV MATCH, please use the following card and address:**

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><h3><img src="../../.gitbook/assets/1 Visa icon.png" alt="" data-size="original"></h3></td><td><strong>VISA: 4012 0000 9876 5439</strong><br><strong>EXP DATE: 12/28</strong><br><strong>CVV: 999</strong><br><strong>ADDRESS: 8320</strong><br><strong>ZIP: 85284</strong></td></tr></tbody></table>



***



## Partial Authorization with Global (TSYS) <a href="#partial-authorization-with-global-tsys" id="partial-authorization-with-global-tsys"></a>

If you need to do partial authorizations we offer an option named:

<mark style="color:green;">**`AllowPartialAuth`**</mark>

If this option is turned on (by request only), then it is possible for a transaction to be approved for the partial amount when the card has an available balance which is less than the amount being authorized. In this case we will return the approved amount and the balance due. This remaining balance could potentially be collected in another form of payment or at a later date.

If this option is turned on, then you can monitor the following values which are part of the sale response.

* `IsPartialApproval Flag`
* `ResponseAuthorizedAmount DecimalValue`
* `ResponseApprovedAmount DecimalValue`

#### Partial Authorization Test Data <a href="#partial-authorization-test-data" id="partial-authorization-test-data"></a>

To test a partial authorization you will do the following:

Use one of these cards:

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><h3><img src="../../.gitbook/assets/1 Discover icon.png" alt="" data-size="original"></h3></td><td><strong>DS: 6011 0009 9302 6909</strong><br><strong>EXP DATE: 01/28</strong><br><strong>CVV: 999</strong><br><br>Enter the following amount ($10.10) should get partial approval for ($10.00)</td></tr><tr><td><h3><img src="../../.gitbook/assets/1 Master card icon.png" alt="" data-size="original"></h3></td><td><p><strong>MC: 5146 3126 2000 0045</strong><br><strong>EXP DATE: 01/28</strong></p><p><strong>CVV: 998</strong><br><br>Enter the following amount ($11.10) should get partial approval for ($5.55)</p></td></tr></tbody></table>



***



### Decline Codes

<table><thead><tr><th width="164">Response Code</th><th width="218">Authorization response</th><th width="368">Response definition</th></tr></thead><tbody><tr><td>00</td><td>APPROVAL</td><td>Approved and completed</td></tr><tr><td>01</td><td>CALL</td><td>Refer to issuer</td></tr><tr><td>02</td><td>CALL</td><td>Refer to issuer - Special condition</td></tr><tr><td>03</td><td>TERM ID ERROR</td><td>Invalid Merchant ID</td></tr><tr><td>04</td><td>HOLD-CALL</td><td>Pick up card (no fraud)</td></tr><tr><td>05</td><td>DECLINE</td><td>Do not honor</td></tr><tr><td>06</td><td>ERROR</td><td>General error</td></tr><tr><td>07</td><td>HOLD-CALL</td><td>Pick up card, special condition (fraud account)</td></tr><tr><td>08</td><td>APPROVAL</td><td>Honor MasterCard with ID</td></tr><tr><td>10</td><td>PARTIAL APPROVAL</td><td>Partial approval for the authorized amount returned in Group III version 022</td></tr><tr><td>11</td><td>APPROVAL</td><td>VIP approval</td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>

{% hint style="danger" %}
## Decline Codes to implement <a href="#decline-codes" id="decline-codes"></a>
{% endhint %}

\
