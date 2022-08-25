# React To Issue
[![CI](https://github.com/aidan-mundy/react-to-issue/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/aidan-mundy/react-to-issue/actions/workflows/ci.yml)
[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-React%20To%20Issue-blue?colorA=24292e&colorB=0366d6&style=flat&longCache=true&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAM6wAADOsB5dZE0gAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAAERSURBVCiRhZG/SsMxFEZPfsVJ61jbxaF0cRQRcRJ9hlYn30IHN/+9iquDCOIsblIrOjqKgy5aKoJQj4O3EEtbPwhJbr6Te28CmdSKeqzeqr0YbfVIrTBKakvtOl5dtTkK+v4HfA9PEyBFCY9AGVgCBLaBp1jPAyfAJ/AAdIEG0dNAiyP7+K1qIfMdonZic6+WJoBJvQlvuwDqcXadUuqPA1NKAlexbRTAIMvMOCjTbMwl1LtI/6KWJ5Q6rT6Ht1MA58AX8Apcqqt5r2qhrgAXQC3CZ6i1+KMd9TRu3MvA3aH/fFPnBodb6oe6HM8+lYHrGdRXW8M9bMZtPXUji69lmf5Cmamq7quNLFZXD9Rq7v0Bpc1o/tp0fisAAAAASUVORK5CYII=)](https://github.com/marketplace/actions/react-to-issue)

A GitHub action for reacting to an issue or pull request.

## Usage

### Add reactions to an issue (or pull request)

```yml
      - name: Add reactions
        uses: aidan-mundy/react-to-issue@v1.INSERT.VERSION
        with:
          issue-number: 9
          reactions: +1, hooray, laugh
```

### Action inputs

| Name | Description | Default |
| --- | --- | --- |
| `token` | `GITHUB_TOKEN` (`issues: write`, `pull-requests: write`) or a `repo` scoped [PAT](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token). | `GITHUB_TOKEN` |
| `repository` | The full name of the repository (OWNER/REPO) to work in. | Current repository |
| `issue-number` | The number of the issue or pull request to react to. | |
| `reactions` | A comma separated list of reactions to add. (`+1`, `-1`, `laugh`, `confused`, `heart`, `hooray`, `rocket`, `eyes`) | |

Note: In *public* repositories this action does not work in `pull_request` workflows when triggered by forks.
Any attempt will be met with the error, `Resource not accessible by integration`.
This is due to token restrictions put in place by GitHub Actions. Private repositories can be configured to [enable workflows](https://docs.github.com/en/github/administering-a-repository/disabling-or-limiting-github-actions-for-a-repository#enabling-workflows-for-private-repository-forks) from forks to run without restriction. See [here](https://github.com/peter-evans/create-pull-request/blob/main/docs/concepts-guidelines.md#restrictions-on-repository-forks) for further explanation. Alternatively, use the [`pull_request_target`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#pull_request_target) event to comment on pull requests.


### Accessing issues in other repositories

You can react to issues and pull requests in another repository by using a [PAT](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token) instead of `GITHUB_TOKEN`.
The user associated with the PAT must have write access to the repository.

## License

[MIT](LICENSE)

This code was originally sourced from https://github.com/peter-evans/create-or-update-comment subject to the MIT License under copyright of Peter Evans. Files sourced substantially from the original repository have been annotated as such (where possible).

I've repurposed the code for adding reactions to issues and pull requests, and I am releasing the code with the MIT license under which it was originally obtained.
