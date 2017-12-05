---
title: To what extent can automation help with development practices?
separator: <!--s-->
verticalSeparator: <!--v-->
theme: ../theme/trainlineeu.css
highlightTheme: monokai-sublime
revealOptions:
  transition: 'fade'
  controls: false
  math: ''
---

<!--# A development workflow filled with automation-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
# How can<br> <strong>automation</strong> help with<br> <strong>development practices</strong>


Note:

- Talk about development workflow for our team
- Talk about automation and specificaly about Gitlab-CI
- Open for discussions: don't take everything for granted and writen in stone. Happy to adapt!

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/14% url(images/capitaine-logo-full.png)" -->

a.k.a
# _**La méthode**_ de dev chez<br> _**Capitaine Train**_

<!--s-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->

## Who am I?

**⌨ + ⚙ + 🚴**

⏸ Software Developer

▶ Linux Infra & Ops

🐦 **@paulRb_r**

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
- Usually once your project has other contributors it's a good idea to have a "workflow" in place ("proces" is too formal and sounds too static)
- work - flow it's really a flow of work and the flow can move it's not static.
- Generic workflow used in all applications developped in Paris (fronteds, backend apps, configuration management)


<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Local changes

💻

Note:

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Pull Request · Merge Request

<i class="em em-github"></i> · <i class="em em-gitlab"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Review

💚

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Review

💔


<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Review

💚

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Integration testing

✅

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Merge Master

<i class="em em-merge"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
### Ship it to Production

🚀

<!--s-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<!-- ### TL; DR

* Local changes 💻
* Pull Request / Merge Request <i class="em em-gitlab"></i>
* Review 💚
* Integration testing ✅
* Merge Master <i class="em em-merge"></i>
* Ship 🚀

-->

### TL; DL

* 💻 Local changes
* <i class="em em-gitlab"></i> Pull Request / Merge Request
* 💚 Review
* ✅ Integration testing
* <i class="em em-merge"></i> Merge Master
* 🚀 Ship
Note: now we know the workflow, let's help Dug
<!--s-->

<!-- .slide: data-background="./images/dog.jpg" -->
## Dug the developer

Willing to contribute code

Note: Dug is about to implement his first feature in the 25kv Application \o/

<!--v-->

<!-- .slide: data-background="./images/dog.jpg" -->
## Dug the developer

Working in the **25kv** team


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
💻 Local changes

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/dev1-.svg" />
💻 Local changes

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/dev2-.svg" />
💻 Local changes

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/MR.svg" />
<i class="em em-gitlab"></i> + 💚 Merge Request & Review

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->
<img src="./images/integrated.svg" />
✅ Integration testing

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
🚀 Ship to Production

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
<!-- .slide: data-background="rgba(255,160,59,0.85)" -->

### Open Source ❤️

<!--v-->
<!-- .slide: data-background="rgba(252,163,38,.8)" -->

## Gitlab

* source code
* merge request
* review
* CI build pipelines
* Artifacts
* Docker registry
* ...much more


<!--s-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

## Gitlab CI

<img src="./images/gitlab.svg" class="plain" style="height: 15%; width: 15%" />

Note:
- Similar to Travis / Concourse...


<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### Open Source ❤️

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### `.gitlab-ci.yml`  file

Note: Travis style, Jenkins also since `Jenkinsfile`

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### versioned within git

Note: You can make changes & propose MR on your pipeline process!
You can review your pipeline process \o/

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### declarative

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

```yaml
job1:
  script: make build

job2:
  script: make test
```

Note: define "what" to do (as opposed to "how" to do it)

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### integrated

<!--s-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

## Pipeline

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### 1 pipeline == n stages

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

```yaml
stages:
  - build
  - test
  - deploy
```

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### 1 stage == n jobs

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->


```yaml
job1-unit-test:
  stage: test

job2-acceptance-test:
  stage: test
```

Note: What is important here is that all jobs within 1 stage can run in // on different runner instances

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### 1 pipeline == `jobs x stages`

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

<img   style="width: 50%;" class="plain"  src="./images/screenshots/mr-pipeline.png" />

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
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`
```yaml
image: ruby:2.4
```
```transparent
bundle:
  stage: build
  script:
    - bundle install --deployment
  artifacts:
    paths: [ '.bundle/', 'vendor/' ]
```
```transparent
test:
  stage: test
  script:
    - bundle exec rake test
```
```transparent
lint:
  stage: test
  script:
    - bundle exec rubocop
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`
```none
image: ruby:2.4
```
```yaml
bundle:
  stage: build
  script:
    - bundle install --deployment
  artifacts:
    paths: [ '.bundle/', 'vendor/' ]
```
```transparent
test:
  stage: test
  script:
    - bundle exec rake test
```
```transparent
lint:
  stage: test
  script:
    - bundle exec rubocop
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```none
bundle:
  stage: build
  script:
    - bundle install --deployment
  artifacts:
    paths: [ '.bundle/', 'vendor/' ]
```
```yaml
test:
  stage: test
  script:
    - bundle exec rake test
```
```transparent
lint:
  stage: test
  script:
    - bundle exec rubocop
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```none
bundle:
  stage: build
  script:
    - bundle install --deployment
  artifacts:
    paths: [ '.bundle/', 'vendor/' ]
```
```none
test:
  stage: test
  script:
    - bundle exec rake test
```
```yaml
lint:
  stage: test
  script:
    - bundle exec rubocop
```

Note: Ruby has a gem called Pronto

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`


```none
image: ruby:2.4
```
```yaml
# …

security:
  stage: test
  script:
    - bundle exec brakeman
```
```transparent
test:
  stage: test
  script:
    - bundle exec rake test
```
```transparent
lint:
  stage: test
  script:
    - bundle exec rubocop
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```none
# …

security:
  stage: test
  script:
    - bundle exec brakeman
```
```yaml
bundle-audit:
  stage: test
  script:
    - bundle exec bundle-audit check --update
```
```transparent
lint:
  stage: test
  script:
    - bundle exec rubocop
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipelines-mr.svg" />
<i class="em em-gitlab"></i> + 💚 Merge Request & Review


<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img style="width: 50%;" class="plain" src="./images/screenshots/mr-failed-pipeline-2.png" />

Note:
- That's how it visually looks like in the UI

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img style="width: 50%;" class="plain" src="./images/screenshots/mr-failed-pipeline.png" />

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img style="width: 70%; height: 70%" src="./images/gitlab-discussion.png" />

Review 💚

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img style="width: 50%;" class="plain" src="./images/screenshots/mr-succeeded-pipeline.png" />

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipelines-integration.svg" />
✅

Note: On top of having the `build` stage + `test` stage that we already defined. We only need a deploy job

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```yaml
deploy:integration:
  stage: deploy
  script:
    - bundle exec rake deploy env=${CI_COMMIT_REF_NAME}
  only:
    - dev
```
```transparent
bundle-audit:
  stage: test
  script:
    - bundle exec bundle-audit check --update
```
```transparent
lint:
  stage: test
  script:
    - bundle exec rubocop
```

Note: We don't have environment per MR. That's why we limit to `only` `dev`.

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```yaml
stages:
  - build
  - test
  - deploy
  - # Something missing?
```
```transparent
#
bundle-audit:
  stage: test
  script:
    - bundle exec bundle-audit check --update
```
```transparent
lint:
  stage: test
  script:
    - bundle exec rubocop
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```yaml
stages:
  - build
  - test
  - deploy
  - qa
```
```transparent
#
bundle-audit:
  stage: test
  script:
    - bundle exec bundle-audit check --update
```
```transparent
lint:
  stage: test
  script:
    - bundle exec rubocop
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```none
deploy:integration:
  stage: deploy
  script:
    - bundle exec rake deploy env=${CI_COMMIT_REF_NAME}
  only:
    - dev
```
```yaml
performance:
  stage: qa
  script:
    - bundle exec rake performance \
      target="https://${CI_COMMIT_REF_NAME}.test.trainline.eu/"
  only:
    - dev
```
```transparent
lint:
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipeline-full-dev.png" />

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
🚀

Note: Our pipeline for the `master` environment is almost done:
build, test and dpeloy stages have already been defined. Remember?

Well not quite as we limited the deployment to "dev"


<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```yaml
deploy:integration:
  stage: deploy
  script:
    - bundle exec rake deploy env=${CI_COMMIT_REF_NAME}
  only:
    - dev
```
```transparent
bundle-audit:
  stage: test
  script:
    - bundle exec bundle-audit check --update
```
```transparent
lint:
  stage: test
  script:
  - bundle exec rubocop
  #
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```yaml
deploy:integration:
  stage: deploy
  script:
    - bundle exec rake deploy env=${CI_COMMIT_REF_NAME}
  only:
    - dev
    - master
```
```transparent
  stage: test
  script:
    - bundle exec bundle-audit check --update
```
```transparent
lint:
  stage: test
  script:
  - bundle exec rubocop
  #
```

Note: Last missing part for the last pipeline to production.. is the definition of the production deployment :)


<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```none
image: ruby:2.4
```
```none
deploy:integration:
  stage: deploy
  script:
    - bundle exec rake deploy env=${CI_COMMIT_REF_NAME}
  only:
    - dev
    - master
```
```yaml
deploy:production:
  stage: deploy
  script:
    - bundle exec rake deploy env=production
  only:
    - master
  when: manual # ← Manual button to trigger Job

```
```transparent
#
```

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/master-build-success-slack.png" />


Note: Once all the `master` commit pipeline has succeeded, we get a notification right into Slack

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipeline-full-master.png" />

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
<img src="images/capitaine-logo-full.png" width="300px" class="plain" />

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

<img src="images/captain-logo-full.png" width="300px" class="plain" />

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

<img src="theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg" width="300px" class="plain" />


<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### mature

Note: a bit like cheese yep :)

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

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

### builds "as code"

<!--v-->
<!-- .slide: data-background="rgba(54, 166, 79,.8)" -->

### for people

<!--s-->

Thank you!


## Questions?

* <small>Slides   → https://paulrbr.gitlab.io/talks/dev-workflow.html</small>
* <small>Demo CI → https://gitlab.com/paulrbr/ruby-ci</small>
