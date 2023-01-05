# Chat Bot for Meeting Scheduling

This repository contains a Node.js chat bot that can be used to schedule meetings through the Outlook API. It includes an abstract interface for a chat bot (`chatbot.js`) and an implementation for the Outlook platform (`outlook-chatbot.js`).

## Prerequisites

To use the chat bot, you will need to obtain a client ID and client secret for the Outlook API. You can do this by following the steps in the [Outlook API Quick Start Guide](https://docs.microsoft.com/en-us/outlook/rest/quick-start/nodejs).

You will also need the host and path for the token and authorization endpoints for the Outlook API. These can be obtained from the [Outlook API documentation](https://docs.microsoft.com/en-us/outlook/rest/).

## Installation

To install the dependencies for the chat bot, run the following command:

``` 
  npm install
```
## Usage

To use the chat bot, create an instance of the `OutlookChatBot` class and pass the client ID, client secret, token host, authorize path, and token path as parameters to the constructor.

The chat bot includes the following methods:

- `sendMessage(message)`: Sends a message through the Outlook API. The `message` parameter should be an object with the following properties:
  - `subject`: The subject of the message.
  - `text`: The body of the message.
  - `recipientEmail`: The email address of the recipient.

- `receiveMessage(req)`: Receives a message from the Outlook API. The `req` parameter should be the request object sent by the Outlook API.

- `handleCommand(command)`: Handles a specific command from the user. The `command` parameter should be a string containing the command.

- `scheduleMeeting(subject, startDate, endDate, attendees)`: Creates a new calendar event through the Outlook API with the specified subject, start date, end date, and list of attendees. The start and end dates should be strings in the ISO-8601 format (e.g. `"2022-06-01T12:00:00Z"`). The `attendees` parameter should be an array of email addresses.

You can use the abstract `ChatBot` interface to write platform-agnostic code that can be used with any messaging platform that you want to support. Simply create implementations of the interface for each platform, and pass the appropriate implementation to your chat bot code as needed.
