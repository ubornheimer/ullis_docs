https://pkgdocs.julialang.org/v1/creating-packages/

To generate files for a new package, use `pkg> generate`.

```julia-repl
(v1.0) pkg> generate HelloWorld
```

This creates a new project `HelloWorld` with the following files (visualized with the external [`tree` command](https://linux.die.net/man/1/tree)):

```julia-repl
julia> cd("HelloWorld")

shell> tree .
.
├── Project.toml
└── src
    └── HelloWorld.jl

1 directory, 2 files
```

The `Project.toml` file contains the name of the package, its unique UUID, its version, the authors and potential dependencies:

```toml
name = "HelloWorld"
uuid = "b4cd1eb8-1e24-11e8-3319-93036a3eb9f3"
version = "0.1.0"
authors = ["Some One <someone@email.com>"]

[deps]
```

The content of `src/HelloWorld.jl` is:

```julia
module HelloWorld

greet() = print("Hello World!")

end # module
```

We can now activate the project and load the package:

```julia-repl
pkg> activate .

julia> import HelloWorld

julia> HelloWorld.greet()
Hello World!
```