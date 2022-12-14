# Docker-login
***
A github action to perform common authentication in aws using a OIDC role
There is also the possibility to perform an optional login against docker hub.

This will require the permissions id-token:write and contents:read.

## Usage
***


```yaml
jobs:
  deploy:
    permissions:
      id-token: write
      contents: read
    steps:
      - name: Docker login
        uses: sportalliance/docker-login@main
        with:
            # The aws role to assume e.g. github-actions-ecr-reader
            role: arn:aws:iam::<account-id>:role/github-actions-ecr-reader
            # The aws region to use for authentication e.g. eu-central-1
            region: eu-central-1
            # (optional) The username to use for docker hub authentication if a docker hub login is wanted
            docker-hub-username: user
            # (optional) The password to use for docker hub authentication
            docker-hub-password: password
```