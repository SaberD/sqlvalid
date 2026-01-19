# sqlvalid

SQL file validator. Validates all `.sql` files recursively.

Supports PostgreSQL and SQLite.

## Installation

Download from [GitHub Releases](https://github.com/saberd/sqlvalid/releases):

```bash
# Linux
wget https://github.com/saberd/sqlvalid/releases/latest/download/sqlvalid-linux-amd64 -O sqlvalid
chmod +x sqlvalid

# macOS (Apple Silicon)
wget https://github.com/saberd/sqlvalid/releases/latest/download/sqlvalid-darwin-arm64 -O sqlvalid
chmod +x sqlvalid

# macOS (Intel)
wget https://github.com/saberd/sqlvalid/releases/latest/download/sqlvalid-darwin-amd64 -O sqlvalid
chmod +x sqlvalid
```

Or build from source (requires Go + C compiler):

```bash
CGO_ENABLED=1 go install github.com/saberd/sqlvalid@latest
sqlvalid ./sql
```

## Usage

```bash
# PostgreSQL (default)
sqlvalid ./sql

# SQLite
sqlvalid -sqlite ./sql
```

## Output

```
✓ users/sql/getUser.sql
✓ users/sql/createUser.sql
✓ posts/sql/getPosts.sql

✗ posts/sql/createPost.sql: invalid SQL
  syntax error at or near "INSRT"

✗ 1 SQL error found
```

Exit code 0 = all valid, 1 = errors found.

## GitHub Actions

```yaml
- name: Validate SQL
  run: |
    wget https://github.com/saberd/sqlvalid/releases/latest/download/sqlvalid-linux-amd64 -O sqlvalid
    chmod +x sqlvalid
    ./sqlvalid ./sql
```

## License

MIT
