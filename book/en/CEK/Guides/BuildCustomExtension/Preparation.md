## Preparation {#Preparation}
To develop a custom extension, prepare the following.

* [Interaction model](#InteractionModel)
* (Optional) [Authorization server](#AuthServer)

### Interaction model {#InteractionModel}
When you develop a custom extension, the first thing to do is defining an interaction model on how your extension will receive requests from users. An interaction model is a schema standardizing each type of request that your custom extension will be receiving. Once the interaction model is defined, register the model in Clova Developer Console with the following information.

| Element         | Description                            |
|-------------|--------------------------------|
| Intent              | Specification that defines different types of user requests. Your custom extension must have its own interaction model consisting of a set of *intents*. CEK sends an [IntentRequest](/CEK/References/Custom_Extension_Message_Format.md#IntentRequest) message to your extension containing analysis details of user's speech input. The message is constructed referencing the *intent* defined in the interaction model. |
| slot | A slot contains necessary information for processing a request declared in *intent*. Slots are to be defined along with its corresponding *intent*. Clova analyzes a user request and extracts information related to slots. CEK includes the extracted slot information in an *IntentRequest* message in the form of key-value pairs and sends it to your extension.  |
| Examples of user's speech input        | List of examples showing how a user's spoken request can be put in. You can define several example sentences for each *intent*. Example sentences are denoted with slots. Clova uses this information to analyze user requests. |

Assume a custom extension that provides a pizza ordering service. When it receives a request from a user saying, "I'd like to order two pepperoni pizzas", it can define the user request to an intent as follows.

![](/CEK/Resources/Images/CEK_Interaction_Model_Analysis_Diagram.png)

This is an interaction model defined in JSON format.

{% raw %}
```json
{
  "intents": [
    {
      "intent": "OrderPizza",
      "slots": [
        {
          "name": "PizzaAmount",
          "type": "CLOVA.NUMBER"
        },
        {
          "name": "PizzaType",
          "type": "CUSTOM.PIZZA_TYPE"
        }
      ]
    },
    {
      "intent": "OrderSideDish",
      ...
    }
    ...
  ]
}

```
{% endraw %}

The example shows how a user's spoken request is mapped to pre-defined *intent* and *slot*. You can use this information to process other user requests which have the same intentions but are expressed in different ways.

{% raw %}
```
OrerPizza {CUSTOM.PIZZA_TYPE} 주문해줘
OrderItem {CUSTOM.PIZZA_TYPE} 주문해줄래?
OrderItem {CUSTOM.PIZZA_TYPE} {CLOVA.NUMBER}판 주문해줘
...
OrderSIdeDish  {CUSTOM.SIDE_DISH} 주문해줘
```
{% endraw %}

Your custom extension can receive a message as below based on the interaction model defined as above.

{% raw %}
```json
{
  "version": "0.1.0",
  "session": {
    "new": false,
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "V0qe",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    "System": {
      "user": {
        "userId": "V0qe",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b"
      }
    }
  },
  "request": {
    "type": "IntentRequest",
    "intent": {
      "name": "OrderPIzza",
      "slots": {
        "PizzaAmount": {
          "name": "PizzaAmount",
          "value": "2"
        },
        "PizzaType": {
          "name": "PizzaType",
          "value": "페퍼로니"
        }
      }
    }
  }
}
```
{% endraw %}

<div class="note">
  <p><strong>Note!</strong></p>
  <p>Clova Developer Console is still under development. Contact your counterpart contact personnel to ask for help with defining an interaction model.</p>
</div>


### Authorization server {#AuthServer}
If your custom extension provides a 3rd party service that requires user account authentication such as music, shopping or banking, account linking is necessary. To do so, you have to set up an authorization server. See [Linking user account](/CEK/Guides/LinkUserAccount.md) for more details.