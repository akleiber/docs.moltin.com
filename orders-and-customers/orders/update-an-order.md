# Update an Order

You can only update custom data, `shipping` and `shipping_address` on orders. Everything else inside the order object is immutable.

{% hint style="warning" %}
You can only update order `shipping` and `shipping_address,` if the order has not been fulfilled.
{% endhint %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/orders/:id" %}
{% api-method-summary %}
Update by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the order you wish to update
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
`order`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "type": "order",
    "id": "369ad4a4-ee67-48b0-x347-t50a6e61d83d",
    "status": "incomplete",
    "payment": "unpaid",
    "shipping": "unfulfilled",
    "customer": {
      "name": "Mr John Doe",
      "email": "johndoe@example.com"
    },
    "shipping_address": {
      "first_name": "James",
      "last_name": "Doe",
      "phone_number": "",
      "company_name": "",
      "line_1": "2nd Floor British India House",
      "line_2": "15 Carliol Square",
      "city": "Newcastle Upon Tyne",
      "postcode": "NE1 6UF",
      "county": "Tyne & Wear",
      "country": "United Kingdom",
      "instructions": ""
    },
    "billing_address": {
      "first_name": "John",
      "last_name": "Doe",
      "company_name": "",
      "line_1": "2nd Floor British India House",
      "line_2": "15 Carliol Square",
      "city": "Newcastle Upon Tyne",
      "postcode": "NE1 6UF",
      "county": "Tyne & Wear",
      "country": "United Kingdom"
    },
    "links": {},
    "meta": {
      "display_price": {
        "with_tax": {
          "amount": 237500,
          "currency": "USD",
          "formatted": "$2175.00"
        },
        "without_tax": {
          "amount": 237500,
          "currency": "USD",
          "formatted": "$2175.00"
        }
      },
      "timestamps": {
        "created_at": "2018-04-16T10:11:59.715Z",
        "updated_at": "2018-04-16T10:11:59.715Z"
      }
    },
    "relationships": {
      "items": {
        "data": [
          {
            "type": "item",
            "id": "de9fddf5-011b-4485-abf8-ebb8f53c39ff"
          }
        ]
      }
    },
    "order_reference": null,
    "phone_number": null,
    "shipping_sms_sent": null,
    "delivery_status": null,
    "delivery_details": null,
    "delivery_date": null,
    "confirmation_sms_sent": null,
    "confirmation_email_sent": null,
    "shipping_email_sent": null,
    "refund_sms_sent": null,
    "short_id": null
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X PUT https://api.moltin.com/v2/orders/:id \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer XXXX" \
    -d $'{
      "data": {
        "type": "order"
        "shipping_address": {
          "first_name": "John"
        }
      }
    }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const order = {
  "shipping_address": {
    "first_name": "John"
  }
}

Moltin.Orders.Update(id, order).then(order => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

