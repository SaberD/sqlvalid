# sqvalid

SQL file validator. Validates all `.sql` files recursively.

Supports PostgreSQL and SQLite.

## Installation

Download from [GitHub Releases](https://github.com/saberd/sqvalid/releases):

```bash
# Linux
wget https://github.com/saberd/sqvalid/releases/latest/download/sqvalid-linux-amd64 -O sqvalid
chmod +x sqvalid

# macOS (Apple Silicon)
wget https://github.com/saberd/sqvalid/releases/latest/download/sqvalid-darwin-arm64 -O sqvalid
chmod +x sqvalid

# macOS (Intel)
wget https://github.com/saberd/sqvalid/releases/latest/download/sqvalid-darwin-amd64 -O sqvalid
chmod +x sqvalid
```

Or build from source (requires Go + C compiler):

```bash
CGO_ENABLED=1 go install github.com/saberd/sqvalid@latest
sqvalid ./sql
```

## Usage

```bash
# PostgreSQL (default)
sqvalid ./sql

# SQLite
sqvalid -sqlite ./sql
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
    wget https://github.com/saberd/sqvalid/releases/latest/download/sqvalid-linux-amd64 -O sqvalid
    chmod +x sqvalid
    ./sqvalid ./sql
```

## License

MIT
