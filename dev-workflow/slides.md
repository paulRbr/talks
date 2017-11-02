---
title: To what extent can automation help with development practices?
separator: <!--s-->
verticalSeparator: <!--v-->
theme: ../theme/trainlineeu.css
highlightTheme: solarized-light
#highlightTheme: rainbow
revealOptions:
  transition: 'fade'
  controls: false
---

<!--# A development workflow filled with automation-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
# How can<br> <strong>automation</strong> help with<br> <strong>development practices</strong>


Note:

- Talk about development workflow for our team
- Talk about automation and specificaly about Gitlab-CI
- Open for discussions: don't take everything for granted and writen in stone. Happy to adapt!

<!--s-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->

## Who am I?

**⌨ + ⚙ + 🚴** = **Paul Bonaud**

⏸ Software Developer Connection Team

▶ Linux Infra Team & Paris Ops Team

*@paulr* on Slack

Note:

As a small introduction I'll present what this talk is NOT about.

<!--s-->
<!-- .slide: data-background="./images/agile.jpg" -->

Note: This talk is NOT about methodologies and project management

Beyond the troll though, I will share a list of words that can describe well our agility and than can describe well a sain development workflow

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
### autonomy

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
### initiative

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
### empathy

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
### communication

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
### honesty

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
### responsibility

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
### humor

<!--s-->
<!-- Green Mint TL
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## Development<br>Workflow

Note:
- let's dive into the real subject
- Generic workflow used in all applications developped in Paris (fronteds, backend apps, configuration management)


<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Local changes

<i class="em em-computer"></i>

Note:

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Pull Request | Merge Request

<i class="em em-github"></i> | <i class="em em-gitlab"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Review

<i class="em em-green_heart"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Review

<i class="em em-broken_heart"></i>


<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Review

<i class="em em-green_heart"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Integration testing

<i class="em em-ok_noc"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Merge Master

<i class="em em-merge"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Ship it to Production

<i class="em em-rocket"></i>

<!--s-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<!-- ### TL; DR

* Local changes <i class="em em-computer"></i>
* Pull Request / Merge Request <i class="em em-gitlab"></i>
* Review <i class="em em-green_heart"></i>
* Integration testing <i class="em em-ok_noc"></i>
* Merge Master <i class="em em-merge"></i>
* Ship <i class="em em-rocket"></i>

-->

### TL; DL

* <i class="em em-computer"></i> Local changes
* <i class="em em-gitlab"></i> Pull Request / Merge Request
* <i class="em em-green_heart"></i> Review
* <i class="em em-ok_noc"></i> Integration testing
* <i class="em em-merge"></i> Merge Master
* <i class="em em-rocket"></i> Ship
Note: now we know the workflow, let's help Dug
<!--s-->

<!-- .slide: data-background="./images/dog.jpg" -->
## Dug the developer

Willing to contribute code

Note: Dug is about to implement his first feature in the 25kv Application \o/

<!--v-->

<!-- .slide: data-background="./images/dog.jpg" -->
## Dug the developer

Working in the <i class="em em-25kv"></i> team


<!--s-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## Development<br>Workflow

Note: Dug is a good developer. Like every good developer he knows git by <3

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## Git<br>Workflow

Note: That's great because our development workflow is tighly coupled to our Git workflow

<!--
<img src="./images/env-workflow.svg" />
-->

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/integration-platform.svg" />

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/integration3.svg" />

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/fork.svg" />
<i class="em em-computer"></i> Local changes

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/dev1-.svg" />
<i class="em em-computer"></i> Local changes

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/dev2-.svg" />
<i class="em em-computer"></i> Local changes

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/MR.svg" />
<i class="em em-gitlab"></i> + <i class="em em-green_heart"></i> Merge Request & Review

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/integrated.svg" />
<i class="em em-ok_noc"></i> Integration testing

Note: "dev" branch is alive, dug has added some commits but probably other pull requests will be integrated

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/merge-master.svg" />
<i class="em em-merge"></i> Merge Master

Note:
- at some points in the day, some people are willing to push their commits all the way to production.
- So previous to last step is to merge to the preprod env "master"

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/dev-completed.svg" />
<i class="em em-rocket"></i> Ship to Production

<!--s-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## Git<br>Workflow

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## Build Pipeline<br>Workflow

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## ~~Build Pipeline~~ CI<br>Workflow
<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## ~~Build Pipeline~~ ~~CI~~ CD<br>Workflow

Note: You name it...
<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## Build Pipeline<br>Workflow

<!--v-->

<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/dev-workflow.svg" />

Note: If

<!--v-->

<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/pipelines.svg" />

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

### 1 commit == 1 pipeline

Note: before I describe how to configure a pipeline I need to introduce the tool that we use for that

<!--s-->
<!-- Orange Gitlab -->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

## Gitlab

<img src="./images/gitlab.svg" class="plain" style="height: 15%; width: 15%" />

<!--v-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

## Gitlab

* source code
* merge request
* review
* CI build pipelines


<!--s-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

## Gitlab<br>CI

<img src="./images/gitlab.svg" class="plain" style="height: 15%; width: 15%" />

<!--v-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

### `.gitlab-ci.yml`  file

Note: Travis style, Jenkins also since `Jenkinsfile`

<!--v-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

### versioned within git

Note: You can make changes & propose MR on your pipeline process!
You can review your pipeline process \o/

<!--v-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

### declarative

<!--v-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

### declarative

```yaml
job1:
  script: make compile

job2:
  script: make test
```

<!--v-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

### integrated


<!--v-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

### integrated

<img src="./images/gitlab-mr.png"/>

Note: The CI is completely integrated within the source code management UI. You can see build results within your MR. Within your project. Split by environment :)

<!--s-->

## Pipeline

<!--v-->

### 1 pipeline == n stages

<!--v-->

### 1 pipeline == n stages

```yaml
stages:
  - build
  - test
  - deploy
```

<!--v-->

### 1 stage == n jobs

<!--v-->

### 1 stage == n jobs

```yaml
job1-unit-test:
  stage: test

job2-acceptance-test:
  stage: test
```

Note: What is important here is that all jobs within 1 stage can run in // on different runner instances

<!--v-->

### 1 pipeline == `jobs x stages`

<!--v-->

### I.e.
<img src="./images/gitlab-pipeline-ui.png" />

Note:
- A picture is worth thousands words
- Pipeline retry button for *each* job!

<!--v-->

### I.e.
<img src="./images/gitlab-pipeline-ui-failed-job.png" />

<!--v-->

### I.e.
<img src="./images/gitlab-pipeline-ui-running-job.png" />

<!--v-->

### I.e.
<img src="./images/gitlab-pipeline-ui.png" />

<!--s-->


<!-- .slide: data-background="./images/dog.jpg" -->
## Remember Dug?

<!--s-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipelines.svg" />

Note: that's his dev workflow, let's dive into the pipeline definition at each step of the worlfow

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipelines-dev.svg" />

Note: Starting with his local changes, pushed directly to his repository in gitlab
He didn't even bother to run tests locally because he is really confident

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
compile:
  stage: build
  tags: [ shell ]
  script:
    - make compile
  artifacts:
    paths:
      - output/
    expire_in: 10 days
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
test:
  stage: test
  tags: [ shell ]
  script:
    - echo $RUBY_VERSION
    - make test
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
lint:
  stage: test
  tags: [ shell ]
  script:
    - make style-checking
```

Note: Ruby has a gem called Pronto

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
lint:
  stage: test
  tags: [ shell ]
  script:
    - make style-checking
  except:
    - branches@"capitainetrain/25kv"
```

Note: Lint is important only on MRs!

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
security:
  stage: test
  tags: [ shell ]
  script:
    - make scan-flaws

```

Note: Ruby has a gem called Brakeman as a security scanner

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img style="width: 40%; height: 40%" src="./images/gitlab-mr-pipeline.png" />

Note:
- That's how it visually looks like in the UI.
- Let's check the *test* job to see the logs

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img style="width: 90%; height: 90%" src="./images/gitlab-test-log.png" />

Note:

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img style="width: 70%; height: 70%" src="./images/gitlab-discussion.png" />

Review <i class="em em-green_heart"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipelines-integration.svg" />
<i class="em em-ok_noc"></i>

Note: On top of having the `build` stage + `test` stage that we already defined. We only need a deploy job

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
deploy:integration:
  stage: deploy
  tags: [ shell, deploy-runner ]
  script:
    - make deploy env=dev
  only:
    - dev@"capitainetrain/25kv"
```

Note: We don't have environment per MR. That's why we limit to `only` `dev`.

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
stages:
  - build
  - test
  - deploy
  - # Something missing?
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
stages:
  - build
  - test
  - deploy
  - qa
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
performance:
  stage: qa
  tags: [ ui ]
  script:
    - make client-performance target=https://dev.test.trainline.eu/
  only:
    - dev@"capitainetrain/25kv"
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/gitlab-pipeline-dev.png" />

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipelines-merge-master.svg" />
<i class="em em-merge"></i>

Note: merge-master process does happen in the build pipeline (yet!)
Manual script to launch in the project.

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/merge-master-slack.png" />

<i class="em em-merge"></i>


<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipelines-ship.svg" />
<i class="em em-rocket"></i>

Note: Our pipeline for the `master` environment is almost done:
build, test and dpeloy stages have already been defined. Remember?

Well not quite as we limited the deployment to "dev"

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
deploy:integration:
  stage: deploy
  tags: [ shell, deploy-runner ]
  script:
    - make deploy env="dev"
  only:
    - dev@"capitainetrain/25kv"
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
deploy:integration:
  stage: deploy
  tags: [ shell, deploy-runner ]
  script:
    - make deploy env="${CI_BUILD_REF_NAME}"
  only:
    - dev@"capitainetrain/25kv"
    - master@"capitainetrain/25kv"
```

Note: Last missing part for the last pipeline to production.. is the definition of the production deployment :)

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

##### `.gitlab-ci.yml`
```yaml
deploy:production:
  when: "manual" # <= manual job
  stage: deploy
  tags: [ shell, deploy-runner ]
  script:
    - make deploy env="production"
  only:
    - master@"capitainetrain/25kv"
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/master-build-success-slack.png" />


Note: Once all the `master` commit pipeline has succeeded, we get a notification right into Slack

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/gitlab-pipeline-master.png" />

Note: Rollback are free and directly visible in your project's page

<!--s-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

## Heritage

Note: Workflow didn't come in one day

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### 6 years

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### mature

Note: a bit like cheese yep :)

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### mature

<img src="./images/cheese.jpg" />

Note: a bit like cheese yep :)

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### alive

Note: constant changes happen to the pipeline. Merge requests, reviewed & approved by team

- Even yesterday we added the production button :deploy: to :25kv

- This week we are already discussing on removing the `when: manual` line!

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### alive

<img src="./images/gitlab-issue.png" />


<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### builds "as code"

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### for people

<!--s-->

Thank you!

<!--s-->

## Questions?

### References to get started now!

* Gitlab@Trainline<br> <small>**https://gitlab.tools.trainline.eu/**</small>
* `.gitlab-ci.yml` documentation<br> <small>**https://gitlab.com/help/ci/yaml/README.md**</small>
* Slides<br> <small>**https://gitlab.tools.trainline.eu/pbonaud/dev-workflow-slides**</small>
