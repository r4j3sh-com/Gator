Gator: Go-based RSS Feed Aggregator

Gator is a robust, command-line based RSS feed aggregator written in Go. It provides a comprehensive solution for managing, following, and browsing RSS feeds, with features including user management, feed aggregation, and post browsing.

## Features

- User management(register, login, reset)
- Feed management (add, list, follow, unfollow)
- Feed aggregation and scraping
- Post browsing

## Project Structure

The project is organized as follows:

- `main.go`: Entry point of the application
- `handler_agg.go`: Handlers for feed aggregation and browsing
- `internal/`: Internal packages
    - `database/`: Database models and queries
    - `config/`: Configuration management
- `sql/`: SQL queries and schema
    - `queries/`: SQL query files
    - `schema/`: Database schema files

## Setup

1. Clone the repository
2. Set up your database (PostgreSQL recommended)
3. Copy `.env.example` to `.env` and fill in your database credentials in json like this. Adding user is optional. While login or register user will be automatically added.
    
    ```json
    {"db_url":"postgres://example","current_user_name":""}
    ```
    
4. Run `go mod tidy` to install dependencies
5. Run `sqlc generate` to generate Go code from SQL queries
6. Build the project with `go build`

## Usage

Run the compiled binary and use the following commands:

- `register <name>`: Add a new user
- `login <name>` : Login as the user
- `reset` : It will reset all the database
- `users`: Lists all the registered users.
- `addfeed <name> <url>`: Add a new feed
- `listfeeds`: List all feeds
- `follow <feed_url>`: Follow a feed
- `following` : List all the feed followed by current user
- `unfollow <url>`: Unfollow a feed
- `agg <time>`: Aggregate posts from added feeds, It is a continuous loop, you can use time `1s, 1m, 1h` like this.
- `browse [limit]`: Browse posts from followed feeds (default limit: 2)

## Development

- Use `Goose` for database migration
- Use `sqlc` for database query generation
- Run `go generate` to update generated code
- Follow Go best practices and conventions

## Environment Variables

- `DATABASE_URL`: Connection string for the database

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License

Copyright (c) 2025 r4j3sh

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.