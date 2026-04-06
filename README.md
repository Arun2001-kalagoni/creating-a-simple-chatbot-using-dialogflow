A simple customer support chatbot built with **Dialogflow**, **Node.js**, **Express**, and **MongoDB**.  
This project uses **Dialogflow fulfillment webhook** to identify users, collect service issues, generate a ticket number, and store issue details in MongoDB.

## Overview

This chatbot is designed for a basic service/helpdesk flow. It can:

- Verify a user using an account number
- Greet the user after successful identification
- Show issue categories such as:
  - Internet Down
  - Slow Internet
  - Buffering Problem
  - No Connectivity
- Generate a random trouble ticket
- Store reported issues in MongoDB
- Return responses through Dialogflow fulfillment

## Features

- Dialogflow webhook integration
- Express-based backend service
- MongoDB database connectivity
- Dynamic issue reporting flow
- Random ticket number generation
- Rich response payload support for issue selection

## Tech Stack

- **Node.js**
- **Express.js**
- **Dialogflow Fulfillment**
- **MongoDB**
- **randomstring**

## Project Structure

creating-a-simple-chatbot-using-dialogflow/
│── index.js
│── chatbot.js
│── package.json
│── node_modules/

##How It Works
User sends a request through Dialogflow.
The webhook receives the request at /dialogflow.
The chatbot checks the account number in MongoDB.
If the user exists, it welcomes them.
It displays issue options.
The selected issue is saved in MongoDB.
A random trouble ticket is generated and returned to the user.
Database Collections

This project uses a MongoDB database named:
chatbot

Example collections:

user_table
Stores account number and username
user_issues
Stores submitted issue details such as:
username
issue
status
date
trouble_ticket
Prerequisites

##Before running this project, make sure you have:

Node.js
MongoDB
A Dialogflow agent configured with fulfillment enabled
ngrok (optional, for exposing localhost to Dialogflow) Installation

##Clone the repository:

git clone https://github.com/Arun2001-kalagoni/creating-a-simple-chatbot-using-dialogflow.git
cd creating-a-simple-chatbot-using-dialogflow

##Install dependencies:

npm install
Configuration

Make sure MongoDB is running locally on:

mongodb://localhost:27017/

If needed, update the MongoDB connection URL inside the project files.

Run the Project

Start the server with:

node index.js

Or, if you want auto-reload during development:

npx nodemon index.js

The server runs on:

http://localhost:8080

##Webhook endpoint:

http://localhost:8080/dialogflow
Dialogflow Fulfillment Setup
Open your Dialogflow agent
Go to Fulfillment
Enable Webhook
Add your webhook URL:
https://your-ngrok-url/dialogflow

##Example with ngrok:

ngrok http 8080

Then copy the generated HTTPS URL into Dialogflow.

Sample Chat Flow

User: My account number is 12345
Bot: Welcome Arun!! How can I help you?

Bot shows options:

Internet Down
Slow Internet
Buffering Problem
No Connectivity

User: 2
Bot: Dear Arun, The issue reported is: Slow Internet
The ticket number is: ABC1234

Example MongoDB Records
user_table
{
  "acct_num": 12345,
  "username": "Arun"
}
user_issues
{
  "username": "Arun",
  "issue": "Slow Internet",
  "status": "pending",
  "time_date": "2026-04-06",
  "trouble_ticket": "ABC1234"
}

##Notes
MongoDB must be running before starting the app
Dialogflow fulfillment must point to the correct webhook URL
If testing locally, use ngrok for public access
For production use, move database credentials and configuration into environment variables

##Possible Improvements
Add .env support for database URL and port
Improve input validation
Add status tracking for existing trouble tickets
Add authentication and security checks
Store timestamps in a more standard format
Deploy to Render, Railway, or Heroku-like platforms
