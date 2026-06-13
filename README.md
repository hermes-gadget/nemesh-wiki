# nemesh-wiki

Documentation wiki for [nemesh.uk](https://nemesh.uk) — the North East MeshCore network.

Built with [MkDocs](https://www.mkdocs.org/) + [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/).

## Structure

```
├── mkdocs.yml          # MkDocs configuration
├── README.md           # This file
└── docs/               # All wiki pages (Markdown)
    ├── index.md        # Home page
    ├── about.md        # About MeshCore
    ├── faq.md          # Frequently Asked Questions
    ├── join.md         # How to join the network
    ├── hardware.md     # Supported hardware
    ├── coverage.md     # Network coverage
    └── configuration.md # Radio settings & CLI
```

## Editing

Edit any `.md` file in `docs/` and open a PR. On merge, the site rebuilds automatically within 5 minutes.

## Building locally

```bash
pip install mkdocs-material
mkdocs build   # → site/
mkdocs serve   # → http://localhost:8000
```

## License

Content © nemesh.uk
