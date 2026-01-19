# sqvalid

SQL file validator. Validates all `.sql` files recursively.

Supports PostgreSQL and SQLite.

## Installation

### Option 1: Go Install (Recommended)

```bash
go install github.com/saberd/sqvalid@latest
```

Make sure `~/go/bin` is in your PATH. Add this to `~/.bashrc`, `~/.zshrc`, or `~/.profile`:

```bash
export PATH="$PATH:$(go env GOPATH)/bin"
```

Then reload your shell:

```bash
source ~/.bashrc  # or ~/.zshrc
```

Now you can run:

```bash
sqvalid ./sql
```

### Option 2: Binary Download

Download pre-built binaries from [GitHub Releases](https://github.com/saberd/sqvalid/releases):

```bash
# Linux
curl -L https://github.com/saberd/sqvalid/releases/latest/download/sqvalid-linux-amd64 -o sqvalid
chmod +x sqvalid
./sqvalid ./sql

# macOS (Apple Silicon)
curl -L https://github.com/saberd/sqvalid/releases/latest/download/sqvalid-darwin-arm64 -o sqvalid
chmod +x sqvalid
./sqvalid ./sql

# macOS (Intel)
curl -L https://github.com/saberd/sqvalid/releases/latest/download/sqvalid-darwin-amd64 -o sqvalid
chmod +x sqvalid
./sqvalid ./sql
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
    curl -L https://github.com/saberd/sqvalid/releases/latest/download/sqvalid-linux-amd64 -o sqvalid
    chmod +x sqvalid
    ./sqvalid ./sql
```

## License

MIT
