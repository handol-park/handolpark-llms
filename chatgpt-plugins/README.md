# ChatGPT Plugin Research Notes

[OpenAI document](https://platform.openai.com/docs/plugins/introduction)

OpenAI plugins connect ChatGPT to third-party applications. These plugins enable ChatGPT to interact with APIs defined by developers, enhancing ChatGPT's capabilities and allowing it to perform a wide range of actions.

- Retrieve real-time information; e.g., sports scores, stock prices, the latest news, etc.
- Retrieve knowledge-base information; e.g., company docs, personal notes, etc.
- Perform actions on behalf of the user; e.g., booking a flight, ordering food, etc.

## Components of Plugin

- one or more API endpoints
- a standardized manifest file
  - location: yourdomain.com/.well-known/ai-plugin.json
  - includes
    - metadata about the plugin
    - authentication method
    - OpenAPI spec for the endpoints
    - OpenAPI description fields: a natural language description for the different fields
- an OpenAPI specification

## Registration of your plugin

## Conversation with the plugin

- OpenAI injects a compact description of your plugin in a message to ChatGPT, invisible to end users.
  - This will include the plugin description, endpoints, and examples.

## Plugin manifest

```json
{
  "schema_version": "v1",
  "name_for_human": "TODO Plugin",
  "name_for_model": "todo",
  "description_for_human": "Plugin for managing a TODO list. You can add, remove and view your TODOs.",
  "description_for_model": "Plugin for managing a TODO list. You can add, remove and view your TODOs.",
  "auth": {
    "type": "none"
  },
  "api": {
    "type": "openapi",
    "url": "http://localhost:3333/openapi.yaml",
    "is_user_authenticated": false
  },
  "logo_url": "http://localhost:3333/logo.png",
  "contact_email": "support@example.com",
  "legal_info_url": "http://www.example.com/legal"
}
```
