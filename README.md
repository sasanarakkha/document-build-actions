# sasanarakkha-build-ebooks-action

Composite action to build digital books of [Sāsanārakkha Buddhist Sanctuary](https://github.com/orgs/sasanarakkha).

Action uses Makefile of project with common targets.


Use it as a step in a workflow like:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container: bergentroll/pali-english-recitations-builder:latest
    permissions:
      contents: write  # For uploading artifacts
    steps:
      - uses: bergentroll/sasanarakkha-build-ebooks-action@v1
        with:
          validate_epub: false  # To disable corresponding step
          optimize_epub: false  # see inputs section of action.yml
```
