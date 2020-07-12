# learn-rustlang
Notes and code that help me learn rust lang

```bash
# Create new project.
cargo new <project-name>

# Build binary and write it to <project-root>/target/debug/<project-name>
cargo build
# Compile with optimizations and write to <project-root>/target/release/<project-name>
cargo build --release

# Shortcut for building binary and running it.
cargo run

# Check to see if code compiles, but no executable is outputted. Useful for quickly checking code.
cargo check

# Locally build and open documentation in browser for all project dependencies.
cargo doc --open
```

`String` is growable, UTF-8

*associated function* is analogous to *static member functions* in c++.

