# s3-upload-github-action

S3 uploader for Github Actions.

You can upload files or directories to any S3 compatible cloud buckets.

`S3_Endpoint` is composed of s3 + region + domain, e.g. `s3.us-east-1.amazonaws.com`

## Usage

See the following example.

```YAML
# inside .github/workflows/action.yml
name: Add File to Bucket
on: push

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@master

      - name: Upload file to bucket
        uses: drewble/s3-upload-github-action@master
        env:
          FILE: ./releases/
          S3_ENDPOINT: 'ams3.digitaloceanspaces.com'
          S3_BUCKET: ${{ secrets.S3_BUCKET }}
          S3_ACCESS_KEY_ID: ${{ secrets.S3_ACCESS_KEY_ID }}
          S3_SECRET_ACCESS_KEY: ${{ secrets.S3_SECRET_ACCESS_KEY }}
          S3_ACL: 'private' / 'public' (optional)
          S3_DESINATION: 'somefolder/subfolder' (optional)
```
