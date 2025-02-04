---
icon: object-intersect
description: The API reference for the SOAP API
---

# SOAP API

<figure><img src="../../.gitbook/assets/SOAP API B.png" alt=""><figcaption></figcaption></figure>

Our SOAP API is continuously maintained and can be used as an alternative to the [REST API](../rest-api/) and our [other integration options](../../documentation/getting-started/integration-options/). You can access everything via the CardProcAPI service.

We recommend following [our SOAP integration guide](../../documentation/getting-started/integration-options/soap-api.md) and using [svcutil](https://learn.microsoft.com/en-us/dotnet/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe) to start using the SOAP API. This way you will have ready-made CardProcessClient class to help you use the service.

{% tabs %}
{% tab title="C#" %}
```csharp
class Test
{
    static void Main()
    {
        CardProcessClient client = new CardProcessClient();

        // Use the 'client' variable to call operations on the service.

        // Always close the client.
        client.Close();
    }
}
```
{% endtab %}

{% tab title="Visual Basic" %}
```visual-basic
Class Test
    Shared Sub Main()
        Dim client As CardProcessClient = New CardProcessClient()
        ' Use the 'client' variable to call operations on the service.

        ' Always close the client.
        client.Close()
    End Sub
End Class
```
{% endtab %}
{% endtabs %}

The base URL of the SOAP service is [https://easypay5.com/APIcardProcR119/CardProcAPI.svc](https://easypay5.com/APIcardProcR119/CardProcAPI.svc)

{% include "../../.gitbook/includes/link-wsdl-files.md" %}
