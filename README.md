# MCP MySQL Lens

A Model Context Protocol (MCP) server that enables Claude Desktop to interact with MySQL databases directly. This server allows Claude to query, analyze, and manage your MySQL databases through natural language.

## Features

- 🔍 **Query Execution**: Run SQL queries directly from Claude Desktop
- 📊 **Schema Inspection**: Explore database structure, tables, and relationships
- 🔄 **Data Analysis**: Analyze and visualize data patterns
- 🛡️ **Safe Operations**: Built-in safeguards for database operations
- 🚀 **Easy Setup**: Simple configuration with environment variables

## Prerequisites

- [Claude Desktop](https://claude.ai/download) installed
- Node.js (v16 or higher)
- MySQL Server (v5.7 or higher)
- install npm
- Valid MySQL credentials with appropriate permissions

## NPM Link

Visit npm package [mcp-mysql-lens](https://www.npmjs.com/package/mcp-mysql-lens)

## Installation

### 1. Install the MCP Server

```bash
npm install -g mcp-mysql-lens
```

### 2. Configure Claude Desktop

Add this configuration to your Claude Desktop config file:

```json
{
  "mcpServers": {
    "mysql": {
      "command": "npx",
      "args": [
        "mcp-mysql-lens"
      ],
      "env": {
        "MYSQL_HOST": "localhost",
        "MYSQL_PORT": "3306",
        "MYSQL_USER": "your_username",
        "MYSQL_PASSWORD": "your_password",
        "MYSQL_DATABASE": "your_database"
      }
    }
  }
}
```

**Configuration File Location:**
- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`
- **Linux**: `~/.config/Claude/claude_desktop_config.json`

### 3. Restart Claude Desktop

After saving the configuration, restart Claude Desktop for the changes to take effect.

## Configuration Parameters

| Parameter | Description | Default | Required |
|-----------|-------------|---------|----------|
| `MYSQL_HOST` | MySQL server hostname | - | Yes |
| `MYSQL_PORT` | MySQL server port | `3306` | Yes |
| `MYSQL_USER` | Database username | - | Yes |
| `MYSQL_PASSWORD` | Database password | - | Yes |
| `MYSQL_DATABASE` | Default database to connect to | - | Yes |

## Usage Examples

Once configured, you can interact with your MySQL database through Claude Desktop:

### Query Data
```
"Show me all users from the users table"
"What are the top 10 products by sales?"
"Find all orders from the last 30 days"
```

### Analyze Schema
```
"What tables are in my database?"
"Describe the structure of the customers table"
"Show me the relationships between tables"
```

### Data Analysis
```
"Calculate the average order value by month"
"Find duplicate records in the products table"
"Show me user registration trends"
```

## Security Best Practices

⚠️ **Important Security Considerations:**

1. **Use Read-Only Credentials**: Create a dedicated MySQL user with read-only permissions for data analysis tasks

2. **Never Commit Credentials**: Don't commit the `claude_desktop_config.json` file with actual credentials to version control

3. **Use Environment Variables**: For production environments, consider using environment variable substitution

4. **Limit Database Access**: Only grant access to specific databases that Claude needs to work with

5. **Use Strong Passwords**: Ensure your MySQL password is strong and unique

6. **Enable SSL/TLS**: For remote connections, always use SSL/TLS encryption

7. **Regular Auditing**: Monitor database access logs regularly

## Troubleshooting

### Connection Issues

**Problem**: "Cannot connect to MySQL server"
- Verify MySQL server is running: `systemctl status mysql` (Linux) or check Services (Windows)
- Check host and port are correct
- Ensure firewall allows connections on MySQL port (default 3306)
- Verify credentials are correct

**Problem**: "Access denied for user"
- Confirm username and password are correct
- Check user has appropriate permissions: `SHOW GRANTS FOR 'your_user'@'localhost';`
- Verify user can connect from the specified host

### Configuration Issues

**Problem**: Claude Desktop doesn't show the MySQL server
- Ensure the config file is in the correct location
- Check JSON syntax is valid (use a JSON validator)
- Restart Claude Desktop after making changes
- Check Claude Desktop logs for errors

### Performance Issues

**Problem**: Queries are slow
- Add appropriate indexes to frequently queried columns
- Optimize complex queries
- Consider increasing MySQL connection timeout
- Check database server resources (CPU, memory)

## Limitations

- **Query Timeout**: Long-running queries may timeout (default: 30 seconds)
- **Result Size**: Large result sets may be truncated
- **Write Operations**: Currently not supported
- **Concurrent Connections**: Limited by MySQL server's max_connections setting

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built on the [Model Context Protocol](https://modelcontextprotocol.io)
- Powered by [Claude](https://claude.ai) by Anthropic
- MySQL connector by [mysql2](https://github.com/sidorares/node-mysql2)
- Inspired by [dpflucas mysql server](https://github.com/dpflucas/mysql-mcp-server)

---



