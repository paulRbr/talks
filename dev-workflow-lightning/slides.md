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
# How can<br> <strong>automation</strong> help with<br> <strong>development practices</strong>

Note:

- Talk about development workflow for our team
- Talk about automation and specificaly about Gitlab-CI
- As a small introduction I'll present what this talk is NOT about.

<!--s-->
<!-- .slide: data-background="./images/agile.jpg" -->

Note: This talk is NOT about methodologies and project management

Beyond the troll though, I will share a list of words that can describe well our agility and than can describe well a sain development workflow

<!--v-->
### autonomy

<!--v-->
### initiative

<!--v-->
### empathy

<!--v-->
### communication

<!--v-->
### honesty

<!--v-->
### responsibility

<!--v-->
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

<!-- ### TL; DR

* Local changes 💻
* Pull Request / Merge Request <i class="em em-gitlab"></i>
* Review 💚
* Integration testing ✅
* Merge Master <i class="em em-merge"></i>
* Ship 🚀

-->

<ul>
<li class="fragment">💻 Local changes <small>`git commit --verbose`</small> </li>
<li class="fragment"><i class="em em-gitlab"></i> Pull Request / Merge Request</li></li>
<li class="fragment">💚 Review</li>
<li class="fragment">✅ <small>`dev`</small> integration testing</li>
<li class="fragment"><i class="em em-merge"></i> Merge Master</li>
<li class="fragment">✅ <small>`master`</small> integration testing</li>
<li class="fragment">🚀 Ship</li>
</ul>

Note: now we know the workflow, let's help Dug
<!--s-->

<!-- .slide: data-background="./images/dog.jpg" -->
## Dug the developer

Willing to contribute code

Note: Dug is about to implement his first feature in the 25kv Application \o/

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
<img src="./images/dev-workflow.svg" />

<!--s-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## Git<br>Workflow

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

## Build Pipeline / CI / CD<br>Workflow

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
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

## Gitlab CI

<img src="./images/gitlab.svg" class="plain" style="height: 15%; width: 15%" />

Note:
- Similar to Travis / Concourse...

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

- Open Source ❤️ <!-- .element: class="fragment" -->
<li><span><small>`.gitlab-ci.yml`</small> file versioned within git</span></li><!-- .element: class="fragment" -->
- declarative <!-- .element: class="fragment" -->
- integrated UI <!-- .element: class="fragment" -->

Note: Travis style, Jenkins also since `Jenkinsfile`
You can make changes & propose MR on your pipeline process!
You can review your pipeline process \o/

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

##### `.gitlab-ci.yml`

```yaml
image: ruby:2.5

bundle:
  stage: build
  script:
    - bundle install --deployment
  artifacts:
    paths: [ '.bundle/', 'vendor/' ]

test:
  stage: test
  script:
    - bundle exec rake test

rubocop:
  stage: test
  script:
    - bundle exec rubocop
```

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

<img src="./images/pipeline-full-dev-ruby.png" />

<!--s-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipelines-merge-master.svg" />
<i class="em em-merge"></i>

Note: merge-master process

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/merge-master-slack.png" />

<i class="em em-merge"></i>

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/master-build-success-slack.png" />

Note: Once all the `master` commit pipeline has succeeded, we get a notification right into Slack

<!--v-->
<!-- .slide: data-background="rgba(1,119,102,.8)" -->

<img src="./images/pipeline-full-master-ruby.png" />

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

<!--s-->

Thank you!

- Slides   → <a>polr.fr/bathruby2018</a>
- Demo CI → <small>https://gitlab.com/paulrbr/ruby-ci</small>

<small>🐘 **@paulRbr** / 🐦 **@paulRb_r**</small>
