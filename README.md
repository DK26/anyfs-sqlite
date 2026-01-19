# anyfs-sqlite

SQLite backend for [AnyFS](https://github.com/DK26/anyfs) - store virtual filesystems in a single database file.

> ⚠️ **Pre-release**: This crate is reserved for future development. Not yet functional.

## Features

- **Single-file storage** - Entire filesystem in one `.db` file
- **Optional encryption** - AES-256 via SQLCipher with `encryption` feature
- **Connection pooling** - Efficient concurrent access
- **WAL mode** - Better write performance
- **Auto-sharding** - Split large databases automatically

## Installation

```toml
[dependencies]
anyfs-sqlite = "0.1"

# For encryption support:
anyfs-sqlite = { version = "0.1", features = ["encryption"] }
```

## Usage

```rust
use anyfs::FileStorage;
use anyfs_sqlite::SqliteBackend;

// Simple usage
let backend = SqliteBackend::open("data.db")?;
let fs = FileStorage::new(backend);

fs.write("/hello.txt", b"Hello, world!")?;

// With encryption (requires `encryption` feature)
let backend = SqliteBackend::open_encrypted("secure.db", "my-password")?;
```

## Design

See the [AnyFS Design Manual](https://dk26.github.io/anyfs-design-manual/) for architecture details.

## License

Licensed under either of:

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or <http://www.apache.org/licenses/LICENSE-2.0>)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or <http://opensource.org/licenses/MIT>)

at your option.
