# Document Build Actions

## Description

Composite action to build digital books of [Sāsanārakkha Buddhist Sanctuary](https://github.com/orgs/sasanarakkha).

Action uses Makefile of project with common targets.


## Usage

Use it as a step in a workflow like:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container: ghcr.io/sasanarakkha/document-build-actions:main
    permissions:
      contents: write  # For uploading artifacts
    steps:
      - uses: sasanarakkha/document-build-actions@v1
        with:
          validate_epub: false  # To disable corresponding step
          optimize_epub: false  # see inputs section of action.yml
```

## Image

`[Dockerfile](./Dockerfile)` is used to maintain a GNU/Linux environment to build
documents. An images is building with GitHub Actions on `Dockerfile` change and is awailable in 
[packages](https://github.com/sasanarakkha/document-build-actions/pkgs/container/document-build-actions).

To build an image locally for tests run:

```shell
sudo docker image build --compress --force-rm . --tag document-build-actions
```

Than to get shell and delete a container after exit:

```shell
sudo docker run --interactive --tty --rm document-build-actions
```
