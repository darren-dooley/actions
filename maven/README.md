# Snyk Maven Action

A [GitHub Action](https://github.com/features/actions) for using [Snyk](https://snyk.io) to check for
vulnerabilities in your Maven projects.

You can use the Action as follows:

```yaml
name: Example workflow for Maven usng Snyk 
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Run Snyk to check for vulnerabilities
      uses: garethr/snyk-actions/maven@master
      env:
        SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
```

The Snyk Maven Action has properties which are passed to the underlying image. These are
passed to the action using `with`.

| Property | Default | Description |
| --- | --- | --- |
| args |   | Override the default arguments to the Snyk image |
| commands | test | Specifiy which command to run, for instance test or monitor |

For example, you can choose to only report on high severity vulnerabilities.

```yaml
name: Example workflow for Maven usng Snyk 
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Run Snyk to check for vulnerabilities
      uses: garethr/snyk-actions/maven@master
      env:
        SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
      with:
        args: --severity-threshold=high
```