# GitHub Actions Workflow for Angular Project

```yaml
name: Angular

on:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: ./angular

    steps:
    - uses: actions/checkout@v2
    - uses: actions/setup-node@v2
      with:
        node-version: '14'
    - run: yarn
    - run: yarn build:prod
