# Flan Scan Orb

[![CircleCI Build Status](https://circleci.com/gh/gabanz/flan-orb.svg?style=shield "CircleCI Build Status")](https://circleci.com/gh/gabanz/flan-orb) [![CircleCI Orb Version](https://img.shields.io/badge/endpoint.svg?url=https://badges.circleci.io/orb/gabanz/flanscan)](https://circleci.com/orbs/registry/orb/gabanz/flanscan) [![GitHub License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://raw.githubusercontent.com/gabanz/flan-orb/master/LICENSE) [![CircleCI Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com/c/ecosystem/orbs)

This is [Flan Scan](https://github.com/cloudflare/flan) orb, which is a shareable package of CircleCI configuration you can use in your CI/CD builds. It uses nmap to scan your server for open ports, services and vulnerability.
As part of the workflow, it will automatically publish the report to AWS S3 bucket or Google Cloud Storage (or both!) in LaTex, HTML, markdown or JSON format.

## How to use

Include this orb in your own CircleCI workflows. You can choose `aws` or `gcp` job, however make sure to include the necessary credentials.
Refer to the `example.yml` for implementation details.

```
version: "2.1"
orbs:
  flanscan: gabanz/flanscan@2.0.1

workflows:
  scan:
    jobs:
      - flanscan/aws:
          format: html
          ip: 9.9.9.9
          bucket: your-s3-bucket-name
          accesskey: your-aws-access-key
          secret: your-aws-secret
      - flanscan/gcp:
          format: md
          ip: 8.8.8.8
          bucket: your-gcs-bucket-name
          cred: "key.json"
```
