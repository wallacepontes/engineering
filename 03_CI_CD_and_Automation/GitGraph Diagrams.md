# GitGraph Diagrams

## Table of Contents

- [GitGraph Diagrams](#gitgraph-diagrams)
  - [Table of Contents](#table-of-contents)
  - [GitGraph Diagrams](#gitgraph-diagrams-1)
    - [Basic git operations](#basic-git-operations)
    - [Adding custom commit id](#adding-custom-commit-id)
    - [Modifying commit type](#modifying-commit-type)
    - [Adding Tags](#adding-tags)
    - [Create a new branch](#create-a-new-branch)
    - [Checking out an existing branch](#checking-out-an-existing-branch)
    - [Merging two branches](#merging-two-branches)
    - [Cherry Pick commit from another branch](#cherry-pick-commit-from-another-branch)
    - [Hiding Branch names and lines](#hiding-branch-names-and-lines)
  - [Real case](#real-case)
  - [References](#references)

## GitGraph Diagrams

### Basic git operations

```mermaid
---
title: Example Git diagram
---
gitGraph
   commit
   commit
   branch develop
   checkout develop
   commit
   commit
   checkout main
   merge develop
   commit
   commit
```

### Adding custom commit id

```mermaid
    gitGraph
       commit
       commit
       commit
```

```mermaid
    gitGraph
       commit id: "Alpha"
       commit id: "Beta"
       commit id: "Gamma"

```

### Modifying commit type

```mermaid
    gitGraph
       commit id: "Normal"
       commit
       commit id: "Reverse" type: REVERSE
       commit
       commit id: "Highlight" type: HIGHLIGHT
       commit

```

### Adding Tags

```mermaid
    gitGraph
       commit
       commit id: "Normal" tag: "v1.0.0"
       commit
       commit id: "Reverse" type: REVERSE tag: "RC_1"
       commit
       commit id: "Highlight" type: HIGHLIGHT tag: "8.8.4"
       commit
```

### Create a new branch

```mermaid
    gitGraph
       commit
       commit
       branch develop
       commit
       commit
       commit
```

### Checking out an existing branch

```mermaid
    gitGraph
       commit
       commit
       branch develop
       commit
       commit
       commit
       checkout main
       commit
       commit

```

### Merging two branches

```mermaid
    gitGraph
       commit
       commit
       branch develop
       commit
       commit
       commit
       checkout main
       commit
       commit
       merge develop
       commit
       commit
```

```mermaid
    gitGraph
       commit id: "1"
       commit id: "2"
       branch nice_feature
       checkout nice_feature
       commit id: "3"
       checkout main
       commit id: "4"
       checkout nice_feature
       branch very_nice_feature
       checkout very_nice_feature
       commit id: "5"
       checkout main
       commit id: "6"
       checkout nice_feature
       commit id: "7"
       checkout main
       merge nice_feature id: "customID" tag: "customTag" type: REVERSE
       checkout very_nice_feature
       commit id: "8"
       checkout main
       commit id: "9"

```

### Cherry Pick commit from another branch

```mermaid
    gitGraph
        commit id: "ZERO"
        branch develop
        branch release
        commit id:"A"
        checkout main
        commit id:"ONE"
        checkout develop
        commit id:"B"
        checkout main
        merge develop id:"MERGE"
        commit id:"TWO"
        checkout release
        cherry-pick id:"MERGE" parent:"B"
        commit id:"THREE"
        checkout develop
        commit id:"C"

```

### Hiding Branch names and lines

```mermaid
---
config:
  logLevel: 'debug'
  theme: 'base'
  gitGraph:
    showBranches: false
---
      gitGraph
        commit
        branch hotfix
        checkout hotfix
        commit
        branch develop
        checkout develop
        commit id:"ash" tag:"abc"
        branch featureB
        checkout featureB
        commit type:HIGHLIGHT
        checkout main
        checkout hotfix
        commit type:NORMAL
        checkout develop
        commit type:REVERSE
        checkout featureB
        commit
        checkout main
        merge hotfix
        checkout featureB
        commit
        checkout develop
        branch featureA
        commit
        checkout develop
        merge hotfix
        checkout featureA
        commit
        checkout featureB
        commit
        checkout develop
        merge featureA
        branch release
        checkout release
        commit
        checkout main
        commit
        checkout release
        merge main
        checkout develop
        merge release
```

## Real case

```mermaid
---
config:
  logLevel: 'debug'
  theme: 'default'
  gitGraph:
    showBranches: true
    showCommitLabel: true
    mainBranchName: 'Production_Master'
  themeVariables:
      'git0': '#ff0000'
      'git1': '#0084ffd5'
      'git2': '#0084ffd5'
      'git3': '#0084ffd5'
      'git4': '#06f806f1'
      'git5': '#4e4f50c2'
      'git6': '#4e4f50c2'
      'git7': '#4e4f50c2'
      'gitBranchLabel0': '#ffffff'
      'gitBranchLabel1': '#ffffff'
      'gitBranchLabel2': '#ffffff'
      'gitBranchLabel3': '#ffffff'
      
---
    gitGraph
       commit id: "1"
       branch uat_preprod_incremental_hotfix
       branch uat_preprod_evolutionary
       branch uat_preprod_ALM_INC
       branch dev_ist_evolutionary
       checkout dev_ist_evolutionary
       commit id: "DEV1"
       branch local_featureA
       branch local_featureB
       branch local_ALM
       checkout local_featureA
       commit id: "FA1"
       commit id: "FA2"
       checkout local_featureB
       commit id: "FB1"
       commit id: "FB2"
       checkout local_ALM
       commit id: "ALM1"
       commit id: "ALM2"
       checkout dev_ist_evolutionary
       merge local_featureA
       merge local_featureB
       merge local_ALM
       checkout uat_preprod_evolutionary
       merge dev_ist_evolutionary id: "release01" tag: "release01" 
       checkout uat_preprod_ALM_INC
       merge uat_preprod_evolutionary
       checkout uat_preprod_evolutionary
       merge uat_preprod_ALM_INC
       commit id:"UATE1"
       checkout Production_Master
       merge uat_preprod_evolutionary
       checkout dev_ist_evolutionary
       merge uat_preprod_evolutionary
       checkout uat_preprod_incremental_hotfix
       commit id:"HOT1"
       merge Production_Master
       commit id:"HOT2"
       checkout Production_Master
       merge uat_preprod_incremental_hotfix
       checkout dev_ist_evolutionary
       merge uat_preprod_incremental_hotfix
       checkout local_featureA
       commit id: "FA3"
       commit id: "FA4"
```


```mermaid

```


## References
1. https://mermaid.js.org/syntax/gitgraph.html