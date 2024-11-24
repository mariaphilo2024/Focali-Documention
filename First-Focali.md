
### Explanation:
1. **Code Block with Syntax Highlighting**:
   - Encapsulated the YAML code in a fenced code block (` ```yaml `) for proper syntax highlighting in Markdown.

2. **Structure**:
   - Preserved the hierarchy and indentation of the original YAML file to maintain accuracy.

3. **Header**:
   - Added a Markdown header (`#`) for context about the content of the YAML.

Feel free to modify or add more explanations as necessary!

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
