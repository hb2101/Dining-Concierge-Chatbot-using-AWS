# Dining Concierge Chatbot using AWS

An intelligent, serverless chatbot system that helps users find restaurants based on natural language queries. It leverages AWS services like **Lex**, **Lambda**, **OpenSearch**, **SES**, and **DynamoDB**, integrated with a web-based frontend.

---

## Architecture Overview

```
                         +-------------------+
                         |   Web Frontend    |
                         | (chat.html + JS)  |
                         +---------+---------+
                                   |
                                   v
                         +-------------------+
                         |   Amazon Lex Bot  |
                         +---------+---------+
                                   |
                    +--------------+--------------+
                    |                             |
        +---------------------+       +-------------------------+
        | Lambda: IntentHandler|       | Lambda: SearchFunction |
        +---------------------+       +-------------------------+
                    |                             |
       +------------+------------+     +-----------+------------+
       |                         |     |                        |
+---------------+     +-------------------+         +--------------------+
| DynamoDB (logs)|     | Amazon OpenSearch|         | Amazon SES (email) |
+---------------+     +-------------------+         +--------------------+
```

---

## Features

- Natural language restaurant search using Amazon Lex
- AI-powered label search via OpenSearch
- Simple, responsive chat frontend with Bootstrap
- Email delivery of restaurant recommendations using Amazon SES
- Serverless backend logic handled by AWS Lambda
- Session logging and analytics via DynamoDB

---

## Tech Stack

- **Frontend**: HTML, JavaScript, Bootstrap
- **Backend**: AWS Lambda, Lex, OpenSearch, SES, DynamoDB
- **API Gateway**: Connects frontend to Lambda
- **IAM**: Manages roles and secure access

---

## Project Structure

```
Dining-Concierge-Chatbot-using-AWS/
├── assets/                     # Test scripts and helper assets
├── frontend/                   # Static frontend site
│   ├── chat.html               # Main chatbot interface
│   └── assets/
│       ├── css/                # Stylesheets
│       ├── js/                 # JS logic and SDK
│       └── sdk/                # API Gateway JavaScript SDK
├── README.md                   # Project documentation
```

---

## Setup Instructions

### Prerequisites

- AWS Account with permissions for Lex, Lambda, OpenSearch, SES
- Configured AWS CLI
- Valid email verified in Amazon SES (sandbox mode)

### Deployment Steps

1. **Create Lex Bot**
   - Define intents (e.g., `DiningSuggestionsIntent`)
   - Configure sample utterances and slot types

2. **Deploy Lambda Functions**
   - One to handle Lex fulfillment logic
   - One to query OpenSearch and send SES emails

3. **Provision Resources**
   - Create DynamoDB table for logging
   - Create OpenSearch index for restaurant metadata

4. **Host Frontend**
   - Upload `frontend/` to an S3 static website bucket or deploy on Amplify

---

## Sample Flow

1. User: *"Find me Italian restaurants in Manhattan for tonight"*
2. Lex bot parses intent and slots
3. Lambda queries OpenSearch with cuisine and location
4. Results displayed in chat + emailed via SES
5. Interaction logged in DynamoDB

---

## License

MIT License. See `LICENSE` file for details.
