# rusty-ast

A Rust Abstract Syntax Tree (AST) visualization tool. This tool parses Rust source code and displays its syntactic structure in text or JSON format.

## Features

- Generate AST from Rust source code files or strings
- Display AST in readable text format
- JSON output option
- Support for various Rust syntax elements:
  - Function definitions
  - Struct definitions
  - Enum definitions
  - Variable declarations
  - Control flow (if, while, loop)
  - Expressions (binary operations, function calls, literals, etc.)

## Installation

Install using Cargo:

```bash
cargo install rusty-ast
```

Or clone and build from this repository:

```bash
git clone https://github.com/e-bebe/rusty-ast.git
cd rusty-ast
cargo build --release
```

## Usage

### Command Line Tool

Basic usage:

```bash
# Parse a Rust source file
rusty-ast -f path/to/your/file.rs

# Parse Rust code directly
rusty-ast -c "fn main() { println!(\"Hello, world!\"); }"

# Output in JSON format
rusty-ast -f path/to/your/file.rs -o json

```

### As a Library

Add to your `Cargo.toml`:

```bash
cargo add rusty-ast
```

Example code:

```rust
use rusty_ast::{parse_rust_source, TextVisitor};
use syn::visit::Visit;

fn main() {
    let code = r#"
        fn add(a: i32, b: i32) -> i32 {
            a + b
        }
    "#;
    
    if let Ok(ast) = parse_rust_source(code) {
        // Display AST in text format
        let mut visitor = TextVisitor::new();
        visitor.visit_file(&ast);
    }
}
```

## License

MIT

## Contributing

Contributions are welcome, including bug reports, feature requests, and pull requests.
