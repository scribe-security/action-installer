---
title: Installer
sidebar_position: 2
---
# Scribe GitHub Actions - `installer`
Scribe offers GitHub Actions for embedding evidence collecting and validated integrity of your supply chain. 

Use `installer` to install Scribe tools in your workflow.

For Further documentation [Github integration](https://scribe-security.netlify.app/docs/ci-integrations/github/)

## Other Actions
* [bom](action-bom.md), [source](https://github.com/scribe-security/action-bom)
* [verify](action-verify.md), [source](https://github.com/scribe-security/action-verify)
* [installer](action-installer.md), [source](https://github.com/scribe-security/action-installer)
<!-- * [integrity report - action](https://github.com/scribe-security/action-report/README.md) -->

## Tool installer Action
You can use the `installer` Action to install any scribe tool in to your workflow allowing full access to all the CLI options in your workflows. 

Install the tool locally if you want to:
- Generate/verify evidence (SBOMS) from docker daemon.
- Generate/sign local directories (not mapped to the working dir)
- Generate evidence for a global cache directory
- Use tool functionality not exposed by containerized actions.

> action allows users to utilize `valint` in a non-containerized environment.

>Installing `valint` locally is useful when you want to create an evidence (directory or git targets) on targets outside working directory.

### Input arguments
```yaml
  tools:
    description: 'Select scribe tools <tool:version>'
    required: false
    default: 'valint,valint'
```

## Supported tools
* valint
* valint

## OS - Arch support
* Linux - arm64, amd64.

### Usage
```YAML
- name: Scribe tool install
  id: scribe_install
  uses: scribe-security/action-installer@master
```

## Installer action examples

<details>
  <summary> Select tool </summary>

```YAML
- name: valint install
  id: valint_install
  uses: scribe-security/action-installer@master
  with:
    tools: valint
``` 

```YAML
- name: valint install
  id: valint_install
  uses: scribe-security/action-installer@master
  with:
    tools: valint
``` 
</details>

<details>
  <summary> Install valint (tool) </summary>

Install valint as a tool
```YAML
- name: install valint
  uses: scribe-security/action-installer@master

- name: valint run
  run: |
    valint --version
    valint bom busybox:latest -vv
``` 
</details>

<!-- <details>
  <summary> Install gensbom (tool) </summary>

Install Gensbom as a tool (backward compatible)

```YAML
- name: install gensbom
  uses: scribe-security/action-installer@master
  with:
    tool: gensbom

- name: gensbom run
  run: |
    gensbom --version
    gensbom bom busybox:latest -vv
``` 
</details> -->
