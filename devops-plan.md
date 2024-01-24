# Mr-Mandoob DevOps Transformation

## 1- Agile framework:
* Kanban board
* Mr-Mandoob board Status:

```mermaid
flowchart LR
    Development --> Ready_for_Development
    Ready_for_Development --> In_progress
    In_progress --> Under_Review
    Under_Review --> Ready_For_Testing
    Ready_For_Testing --> In_Testing
    In_Testing --> Done_Testing
    Done_Testing --> Ready_For_Release
    Ready_For_Release --> Released
```
|          Stage           |                  Description                     |
|--------------------------|--------------------------------------------------|
| Development              |  description  |
| Ready_for_Development    |  description  |
| In_progress              |  description  |
| Under_Review             |  description  |
| Ready_For_Testing        |  description  |
| In_Testing               |  description  |
| Done_Testing             |  description  |
| Ready_For_Release        |  description  |
| Released                 |  description  |

## 2- Agile software:
* Jira

## 3- Git Branching Startegy:
* feature branching 

```mermaid

gitGraph
   commit
   branch develop
   checkout main
   commit
   branch featureA
   checkout featureA
   commit
   commit
   commit
   checkout develop
   merge featureA
   checkout main
   merge featureA
   commit
   checkout main
   commit
   branch featureB
   checkout featureB
   commit
   commit
   checkout develop
   commit
   checkout main
   commit
   commit
   branch hotfix
   checkout hotfix
   commit
   checkout main
   merge hotfix
   commit
   commit
   checkout develop
   merge hotfix
   commit
   commit

```
* Branchs:

|  Branch Name   |                        Description                              |
|----------------|------------------------------------------------------------------------------------------------|
| main           | it is protected long live branch map to production(only CTO can accept PRs). |
| develop        | it is protected long live branch map to testing environment (only CTO and Team lead can accept PRs).|
| feature branch | it is not protected branch related to certain feature it comes from main, merge to develop for testing and end by merging it to main branch.|
| hotfix branch  | it is not protected branch related to certain feature it comes from main,and end by merging it to main and develop branch. |

## 4- CI/CD Pipeline:

* feature branch pipeline
``` mermaid
flowchart LR
    id1>Commit] --> id2>Post_Commit]
    id2 --> id3>Code_Quality]
```
* hotfix branch pipeline
``` mermaid
flowchart LR
    id1>Commit] --> id2>Post_Commit]
    id2 --> id3>Code_Quality]
```
* merge request pipeline
``` mermaid
flowchart LR
    id1>Commit] --> id2>Post_Commit]
    id2 --> id3>Code_Quality]
```
* develop branch pipeline
``` mermaid
flowchart LR
    id1>Commit] --> id2>Post_Commit]
    id2 --> id3>Code_Quality]
    id3 --> id4>Build]
    id4 --> id5>Unit Test]
    id5 --> id6>Vulnarability Scan]
    id6 --> id7>Deploy on Testing Env]
    id7 --> id8>Automation Testing]

```
* main branch pipeline
``` mermaid
flowchart LR
    id1>Commit] --> id2>Code_Quality]
    id2 --> id3>Build]
    id3 --> id4>Unit Test]
    id4 --> id5>Vulnarability Scan]
    id5 --> id6>Deploy on Production Env]
    id6 --> id7>Health Check]
    
```

* Stages summary:

|    Pipeline Stage    |                        Description                              |
|----------------------|-----------------------------------------------------------------|
| Post_Commit          | verify the current branch has the latest changes on the main.   |
| Code_Quality         | Scan the code with sonarqube or any other PHP code quality tool.|
| Build                | Build docker image and push it to docker registy.               |
| Unit Test            | Run unit test                                                   |
| Vulnarability Scan   | Scan docker images if it has any vulnarabilities.               |
| Deploy               | Deploy to k8s cluster and run db migration.                     |
| Automation Testing   | Run Automation testing scripts.                                 |
| Health Check         | Hit an endpoit to verify that application is up and running     |




