# gitCommitPrompt
A prompt used to customize and generate git commit messages.Please note that the statement must include `{{diff}}` as a placeholder.

For example,if you want the generated commit message to include a scope, you can write it like this:
```json
"gitCommitPrompt": "Please write a concise and descriptive git commit message based on the following diff. The message should follow conventional commit format (type(scope): description) where scope indicates the affected component/module (e.g. backend, frontend, api, auth, etc). The message should be clear and informative. Here is the diff:\\n\"\"\"\\n{{diff}}\\n\"\"\"\\nCommit(Do NOT wrap with extra quotes): "
```

# experimental
Experimental configurations.

## modelContextProtocolServer
MCP is an open protocol that standardizes how applications provide context to LLMs, for more information about what MCP is, please refer to https://modelcontextprotocol.io/introduction. This configuration option is used to define your MCP service. Monica will probe the MCP service you provide and call it when appropriate.

For example:
```json
"experimental": {
  "modelContextProtocolServers": [
    {
      "transport": {
        "type": "stdio",
        "command": "uv",
        "args": [
            "--directory",
            "/path/to/mcp_service_code",
            "run",
            "my_service"
        ]
      }
    }
  ]
}
```