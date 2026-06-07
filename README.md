# nemesh-wiki

Documentation wiki for [nemesh.uk](https://nemesh.uk) — the North East MeshCore network.

This repository is the **source of truth** for the Wiki.js documentation site at wiki.nemesh.uk. All content is edited here on GitHub; the live Wiki.js instance syncs from this repo in pull-only mode.

## Structure

```
├── home.md              # Home page
├── sidebar.md           # Navigation sidebar
├── footer.md            # Global footer
└── <category>/          # Content categories
    └── <page>.md        # Individual pages
```

## Editing

Edit any `.md` file directly on GitHub or clone locally. Changes are synced to the live wiki automatically (Wiki.js polls the repo).

To add a new page:
1. Create a `.md` file in the appropriate category folder
2. Add a link to it in `sidebar.md`
3. Commit and push

## License

Content © nemesh.uk
