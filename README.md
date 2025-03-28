# Vanity Pubky Generator

A tool for generating pubkys with custom prefixes.

## Overview

This tool allows you to create a vanity pubky that begins with a specific string of your choice. For example, you might want a public key that starts with your name or a meaningful word.

When a matching key is found, the program automatically creates an encrypted recovery file that can be used to import and access your new vanity pubky.

### Single line usage
Just replace [PREFIX] with the desired prefix and [PASSPHRASE] with the desired passphrase.
```bash
git clone https://github.com/coreyphillips/vanity-pubky && cd vanity-pubky && cargo build --release && ./target/release/vanity-pubky [PREFIX] --passphrase [PASSPHRASE]
```

### Building from Source

1. Clone this repository or download the source code:
   ```bash
   git clone https://github.com/coreyphillips/vanity-pubky
    ```
2. Navigate to the project directory:
   ```bash
   cd vanity-pubky
   ```
3. Build the release version:
   ```bash
   cargo build --release
   ```
4. The executable will be available at `target/release/vanity_pubky` (or `target/release/vanity_pubky.exe` on Windows)

## Usage

Run the program with the following command:

```
./vanity_pubky [PREFIX] --passphrase [PASSPHRASE]
```

Where:
- `PREFIX` is the desired beginning letters of your public key
- `PASSPHRASE` is the passphrase used to encrypt the recovery file (default: "password")

### Examples

Generate a key that starts with "bob":
```
./vanity_pubky bob
```

Generate a key that starts with "bob" and provide your own passphrase:
```
./vanity_pubky bob --passphrase my_passphrase
```

## Output

The program will display:
1. The prefix it's searching for
2. The number of threads being used
3. Regular status updates during the search
4. When a match is found:
    - The matching public key
    - The corresponding private key
    - Number of attempts required
    - Time elapsed
    - Average search speed (keys/second)
5. The location of the saved recovery file

## Recovery Files

When a matching key is found, the program automatically creates a recovery file with the naming pattern:
```
PREFIX_pubky_recovery.pkarr
```

This file is encrypted with the passphrase "password" unless another passphrase was specified.

## Building for Different Platforms

### For Windows
```bash
rustup target add x86_64-pc-windows-msvc
cargo build --release --target x86_64-pc-windows-msvc
```

### For macOS
```bash
rustup target add x86_64-apple-darwin
cargo build --release --target x86_64-apple-darwin
```

### For Linux
```bash
rustup target add x86_64-unknown-linux-gnu
cargo build --release --target x86_64-unknown-linux-gnu
```