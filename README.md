# sasanarakkha-build-ebooks-action

## Description

Composite action to build digital books of [Sāsanārakkha Buddhist Sanctuary](https://github.com/orgs/sasanarakkha).

Action uses Makefile of project with common targets.


## Usage

Use it as a step in a workflow like:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container: bergentroll/pali-english-recitations-builder:latest
    permissions:
      contents: write  # For uploading artifacts
    steps:
      - uses: sasanarakkha/document-build-actions@v1
        with:
          validate_epub: false  # To disable corresponding step
          optimize_epub: false  # see inputs section of action.yml
```

## Image

[Dockerfile](./Dockerfile) is used to maintain a GNU/Linux environment to build
documents. The pipeline fetching a docker image from the https://hub.docker.com
hub. Image usually built with a command like following (note to replace `TAG`):

```shell
sudo docker image build --compress --force-rm . \
    --tag 'bergentroll/pali-english-recitations-builder:TAG' \
    --tag 'bergentroll/pali-english-recitations-builder:latest' \
```

and uploaded with:

```shell
sudo docker push --all-tags bergentroll/pali-english-recitations-builder
```
