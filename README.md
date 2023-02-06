# GitHub Action to Zmicro Package CI

![https://github.com/zmicro-design/action-zmicro-package-ci](https://img.shields.io/github/v/release/zmicro-design/action-zmicro-package-ci)
![https://github.com/zmicro-design/action-zmicro-package-ci](https://github.com/zmicro-design/action-zmicro-package-ci/workflows/Publish/badge.svg)

### Usage

| option | required | description |
| ------ | -------- | ----------- |

### Example

```yml
name: CI

on: [push]

jobs:
  build:
    name: Test
    runs-on: ubuntu-latest
    steps:
      - name: Docker Build
        uses: zmicro-design/action-zmicro-package-ci@v1
        with:
          build-args: |
            VERSION=${{ steps.meta.outputs.version }}
          context: .
          push: ${{ github.event_name != 'pull_request' }}
          cache-from: type=registry,ref=${{ steps.meta.outputs.name }}:buildcache
          cache-to: type=registry,ref=${{ steps.meta.outputs.name }}:buildcache,mode=max
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          platforms: linux/amd64
```

### License

[MIT](./LICENSE)
