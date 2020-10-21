# Flan Scan Orb

This is [Flan Scan](https://github.com/cloudflare/flan) orb, which is a shareable package of CircleCI configuration you use in your CI/CD builds to scan your server for open ports, services and vulnerability, then subsequently publish the report to AWS S3 bucket or Google Cloud Storage (or both!) in LaTex, HTML, markdown or JSON format.

## How to use

Include this orb in your CircleCI workflows. Refer to the `example.yml`:

```
description: >
  Scan IP 9.9.9.9 and publish report to AWS S3 bucket in JSON format. Concurrently scan IP 8.8.8.8 and publish report to Google Cloud GCS.
usage:
  version: 2.1
  orbs:
    flanscan: gabanz/flanscan@1.0.1
  workflows:
    scan:
      jobs:
        - flanscan/aws:
            format: json
            ip: 9.9.9.9
            bucket: flanscan
            accesskey: abc123
            secret: abc123
        - flanscan/gcp:
            format: html
            ip: 8.8.8.8
            bucket: flanscan
            cred: key.json
```
