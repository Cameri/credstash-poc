# Credstash proof-of-concept

## Purpose
Evaluate the feasibility of using credstash to manage secrets in the cloud,
and to provide said secrets to a multi-tenant NodeJS application/service.

## Configuration
* Set the `AWS_PROFILE` env var to the correct one in `~/.aws/credentials` (e.g. `export AWS_PROFILE=default`)
* Set the `AWS_REGION` env var (e.g. `export AWS_REGION=us-east-1`)
* Set the `NW_STAGE` env var (e.g. `export NW_STAGE=dev`)
* Set the `NW_TENANT` env var (e.g. `export NW_TENANT=nestwealth`)

## Installation
* Follow the **Quick Installation** steps in credstash's [README.md](https://github.com/fugue/credstash/blob/master/README.md)
* Install virtualenv with `pip install virtualenv`
* Create virtualenv with `virtualenv --python=$(which python3) .venv`
* Load virtualenv with `source .venv/bin/activate`
* Install credstash with `pip install credtash`

# CLI commands
## Adding/updating new secrets

Secrets can be added with the following command:

`credstash put -a <key> @<secrets file> stage=$NW_STAGE tenant=$NW_TENANT`

The `-a` option ensures that a new version is automatically created for given key.
Stored secrets are immutable so a new version will be created when rotating them.

## Fetching secrets (CLI)

Secrets can be obtained with the following command:

`credstash get <key> stage=$NW_STAGE tenant=$NW_TENANT`

## Deleting secrets (CLI)

Secrets can be deleted with the following command:

`credstash delete <key> stage=$NW_STAGE tenant=$NW_TENANT`

## Notes

The `stage=$NW_STAGE tenant=$NW_TENANT` provide context to the key, and in
this case they were arbitrarily chosen so that we see that it is possible
to store/have multiple secrets with the same key but in different environments.


