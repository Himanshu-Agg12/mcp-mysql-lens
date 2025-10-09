Claude Desktop Config:
{
  "mcpServers": {
    "mysql": {
      "command": "npx",
      "args": [
        "mcp-mysql-lens"
      ],
      "env": {
        "MYSQL_HOST": "<YOUR_MYSQL_HOST>",
        "MYSQL_PORT": "<YOUR_MYSQL_PORT>",
        "MYSQL_USER": "<YOUR_MYSQL_USERNAME>",
        "MYSQL_PASSWORD": "<YOUR_MYSQL_PASSWORD>",
        "MYSQL_DATABASE": "<YOUR_MYSQL_DEFAULT_DB>"
      }
    }
  }
}
