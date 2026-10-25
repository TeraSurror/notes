Converse API
- Provides a consistent interface for all Amazon Bedrock models that support models

Amazon Bedrock Prompt Management 
- Parameterized prompt templates avoid building prompt strings manually
- Define a template once and inject the variable parts at runtime
- Prompt templates are versioned, and stored centrally for reuse and audit. Cloudtrail records API calls
- Avoids application code changes when a prompt is updated

Conversation History can be Stored in DynamoDB
- organized by partition key of session id
- Inject convo history dynamically 
- Highly scalable for real time responsiveness 
- Set TTL for large volumes of chat history
- 24-hour expiration for support bot histories