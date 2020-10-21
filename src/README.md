# Flan Scan Orb

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
