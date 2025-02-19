[![Build Status](https://dev.azure.com/cmdotcom/text-sdk-java/_apis/build/status/cmdotcom.text-sdk-java?branchName=master)](https://dev.azure.com/cmdotcom/text-sdk-java/_build/latest?definitionId=1&branchName=master)

## @cmdotcom/text-sdk: A helper library to send messages.

Want to send messages in your Java application? Then you are at the right place.
If you want to get all the functionalities, go to: [CM.com API Docs](https://docs.cmtelecom.com/bulk-sms/v1.0)


## Installing
Add the GSon dependency to your project: https://mvnrepository.com/artifact/com.google.code.gson/gson/2.8.5

[![Build Status](https://dev.azure.com/cmdotcom/text-sdk-java/_apis/build/status/cmdotcom.text-sdk-java?branchName=master)](https://dev.azure.com/cmdotcom/text-sdk-java/_build/latest?definitionId=1&branchName=master)
Download our Jar file and add it to your project. 


## Instantiate the client
Use your productToken which authorizes you on the CM platform. Get yours on CM.com

```cs
MessagingClient client = new MessagingClient("YourproductToken");
```

## Send a message
By calling `SendTextMessage` and providing message text, sender name, recipient phone number(s).

```cs
   MessagingClient client = new MessagingClient("YourProductToken");
      client.sendTextMessage("Message Text", "TestSender", new String[] {"00316012345678"});
   
```


## Sending a rich message
By using the `MessageBuilder` it is possible to create images with media for channels such as WhatsApp and Viber
```cs
 MessagingClient client = new MessagingClient("YourProductToken");

 MessageBuilder builder = new MessageBuilder("Message Text", "TestSender", new String[] {"00316012345678"});

 builder.WithAllowedChannels(new Channel[] {Channel.Viber});

    builder.WithRichMessage(new MediaMessage(
                "cm.com",
                "https://avatars3.githubusercontent.com/u/8234794?s=200&v=4",
                "image/png"));


       Message message = builder.Build();

       client.sendMessage(message);
```

## Get the result
Sending an message returns the response body
```cs
{
	"details": "Created 1 message(s)",
	"errorCode": 0,
	"messages": [{
		"to": "00316012345678",
		"status": "Accepted",
		"reference": null,
		"parts": 1,
		"messageDetails": null,
		"messageErrorCode": 0
	}]
}
```

