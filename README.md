# gha-composite-repo-details

A custom GitHub Composite Action that returns formatted details of the invoking repository.

## Description

This action extracts and exposes the repository **name** and **URL** as step outputs, making them easy to consume in downstream workflow steps without needing to parse `github.repository` or `github.repositoryUrl` manually.

## Outputs

| Output | Description | Example |
|--------|-------------|---------|
| `repo-name` | Repository name only (the part after the `/` in `owner/repo`) | `gha-composite-repo-details` |
| `repo-url` | Repository URL in `https://` format (`.git` suffix removed) | `https://github.com/faccomichele-org/gha-composite-repo-details` |

## Usage

```yaml
jobs:
  example:
    runs-on: ubuntu-latest
    steps:
      - name: Get repository details
        id: details
        uses: faccomichele-org/gha-composite-repo-details@main

      - name: Print repository details
        run: |
          echo "Repo name: ${{ steps.details.outputs.repo-name }}"
          echo "Repo URL:  ${{ steps.details.outputs.repo-url }}"
```

## License

This project is licensed under the terms of the [LICENSE](LICENSE) file included in this repository.
