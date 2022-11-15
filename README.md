---
title: Installer
---
# Scribe GitHub actions - `valint installer`
Scribe offers GitHub actions for embedding evidence collecting and integrity verification to your workflows. \

## Other actions
* [bom - action](https://github.com/scribe-security/action-bom/README.md)
* [verify - action](https://github.com/scribe-security/action-verify/README.md)
* [integrity report - action](https://github.com/scribe-security/action-report/README.md)
* [installer - action](https://github.com/scribe-security/action-installer/README.md)

## Tool installer action
You can use the `installer` action to install any scribe tool in to your workflow allowing full access to all the CLI options in your workflows. \

Install the tool locally if you want to:
- Generate/verify evidence (SBOMS) from docker daemon.
- Generate/sign local directories (not mapped to the working dir)
- Generate evidence for a global cache directory
- Use tool functionality not exposed by containerized actions.
Note: Installing valint locally is very useful when you want to create an SBOM outside the workflow default workspace directory.

> action allows users to utilize `valint bom` in a non-containerized environment.

### Input arguments
```yaml
  tools:
    description: 'Select scribe tools <tool:version>'
    required: false
    default: 'valint'
```

## Supported tools
* valint
* gensbom

## OS - Arch support
* Linux - arm64, amd64.

### Usage
```YAML
- name: Scribe tool install
  id: scribe_install
  uses: scribe-security/actions/installer@master
```

## Installer action examples

<details>
  <summary> Select tool </summary>

```YAML
- name: valint install
  id: valint_install
  uses: scribe-security/actions/installer@master
  with:
    tools: gensbom
``` 

```YAML
- name: valint install
  id: valint_install
  uses: scribe-security/actions/installer@master
  with:
    tools: valint
``` 
</details>

<details>
  <summary> Install valint (tool) </summary>

Install valint as a tool
```YAML
- name: install valint
  uses: scribe-security/actions/valint/installer@master

- name: valint run
  run: |
    valint --version
    valint bom busybox:latest -vv
    valint report --scribe.client-id $SCRIBE_CLIENT_ID $SCRIBE_CLIENT_SECRET
``` 
</details>

