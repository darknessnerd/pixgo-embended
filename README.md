## Project Structure 

```
pixgo-embedded/
├── LICENSE
├── README.md
├── go.mod
├── docs/                       # Documentation, design docs, roadmap
│   └── logo.svg
├── cmd/                        # Executables (if any)
│   └── pixgo-demo/ 
│       └── main.go            # Example executable program
├── pkg/                        # Public libraries for external use
│   └── pixgo/                 # Core library code
│       ├── display/
│       ├── input/
│       ├── widgets/
│       └── lvgl_bindings.go
├── internal/                   # Private/internal code you don’t want imported
│   └── simulator/             # e.g. stub build code, desktop simulation
├── third_party/                # External dependencies or vendor sources (optional)
│   └── lvgl/                   # if using as submodule or included source
├── build/                      # Packaging, CI, build scripts
│   └── ci/
├── examples/                   # Example projects
│   ├── hardware/
│   │    └── main.go
│   └── desktop/
│        └── main_stub.go
└── scripts/                    # Utility scripts (build, test, generate)
```

