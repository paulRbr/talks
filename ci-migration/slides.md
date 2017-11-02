---
title: Migrating to Docker focusing on our build pipelines
separator: <!--s-->
verticalSeparator: <!--v-->
theme: ../theme/trainlineeu.css
highlightTheme: monokai-sublime
revealOptions:
  transition: 'fade'
  controls: false
---

<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->
# A **smooth** migration to **Docker** focusing on **build pipelines**

<p class="left">Paul Bonaud<br/><b>@paulrb_r</b></p>
<p class="right">Maxime Visonneau<br/><b>@mvisonneau</b></p>

<!--v-->

<img src="images/capitaine-logo-full.png" width="300px" class="plain" />

↓

<img src="images/captain-logo-full.png" width="300px" class="plain" />

↓

<img src="theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg" width="300px" class="plain" />

Note:
- mini presentation of CT → TL

<!--v-->
<!-- .slide: data-background="no-repeat 98% 98%/7% url(theme/images/trainline-logo-white-8f87ae08035d6750c1a5e836909ecd1a.svg)" -->

<p class="left">
**Paul Bonaud**
<br/>
**⌨ + ⚙ + 🚴**
<br/>
<br/>
▶ Infra & Ops Engineer
<br/>
<small>⏸ Software Developer</small>
<br/>
</p>

<p class="right">
**Maxime Visonneau**
<br/>
**⌨ + 📷 + 🏃**
<br/>
<br/>
Infrastructure Engineer
<br/>
</p>

<!--s-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### Meet Maurice

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

<img src='images/the-amazing-maurice.jpg' style='height: 15em; margin-top: 0em;'/>


<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### Meet Maurice
##### _aka `build2`_

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

<img src='images/the-real-maurice.jpg' style='height: 15em; margin-top: 0em;'/>

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

Manually administrated

<!--v-->
<!-- .slide: data-background="./images/please-no.jpg" -->

Note:
→ _/o\ nope nope nope_

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

Building all projects

_Android, JS (Ember), C++, Ruby_

<!--v-->
<!-- .slide: data-background="./images/traffic-jam.jpg" -->

Note:→ _Tuesday afternoon traffic jam_

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

Deploying everything

_Nginx, apps, infrastructure_

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->
<img src="./images/see-no-evil.png" class="plain" />
Note: → _Secrets, ssh accesses, all in one place :/_

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

Single architecture (Debian 7)

<!--v-->
<!-- .slide: data-background="./images/upgrade.jpg" -->
Note:

How to solve of these problems?
First step of our migration was to insulate builds into Docker containers.

<!--s-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

### New era

Note:

Env multiple
arch multiple


<!--v-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

<img src='images/runner01.jpg' />

<!--v-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

### Docker

<img src="./images/docker-logo-only.png" height="150px" class="plain"/>

<!--v-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

Open Source ❤️

<!--v-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

Isolated

<!--v-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

Immutable

<!--v-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

Stateless

<!--v-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

Version controlled

👋 `Dockerfile`

Note: greater control to project maintainers' build env

For example in a Ruby app

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`Dockerfile`</small>

```docker
FROM ruby:2.4-jessie
```
```none
RUN apt-get update
RUN apt-get -y install libpq-dev ghostscript
```
```none
WORKDIR /opt/app
COPY Gemfile Gemfile.lock /opt/app
RUN  bundle install
```
```none
VOLUME /opt/app
CMD [ "make", "run" ]
```

Note:
- Base image
- /!\ this is just like running a binary
- don't use images from anywhere:
  - either docker hub
  - from scratch

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`Dockerfile`</small>

```none
FROM ruby:2.4-jessie
```
```docker
RUN apt-get update
RUN apt-get -y install libpq-dev ghostscript
```
```none
WORKDIR /opt/app
COPY Gemfile Gemfile.lock /opt/app
RUN  bundle install
```
```none
VOLUME /opt/app
CMD [ "make", "run" ]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`Dockerfile`</small>

```none
FROM ruby:2.4-jessie
```
```docker
RUN apt-get update && \
    apt-get -y install libpq-dev ghostscript && \
    rm -rf /var/lib/apt/lists/*
```
```none
WORKDIR /opt/app
COPY Gemfile Gemfile.lock /opt/app
RUN  bundle install
```
```none
VOLUME /opt/app
CMD [ "make", "run" ]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`Dockerfile`</small>

```none
FROM ruby:2.4-jessie
```
```none
RUN apt-get update && \
    apt-get -y install libpq-dev ghostscript && \
    rm -rf /var/lib/apt/lists/*
```
```docker
WORKDIR /opt/app
COPY Gemfile Gemfile.lock /opt/app
RUN  bundle install
```
```none
VOLUME /opt/app
CMD [ "make", "run" ]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`Dockerfile`</small>

```none
FROM ruby:2.4-jessie
```
```none
RUN apt-get update && \
    apt-get -y install libpq-dev ghostscript && \
    rm -rf /var/lib/apt/lists/*
```
```none
WORKDIR /opt/app
COPY Gemfile Gemfile.lock /opt/app
RUN  bundle install
```
```docker
VOLUME /opt/app
CMD [ "make", "run" ]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`Dockerfile`</small>

```docker
FROM ruby:2.4-jessie
```
```docker
RUN apt-get update && \
    apt-get -y install libpq-dev ghostscript && \
    rm -rf /var/lib/apt/lists/*
```
```docker
WORKDIR /opt/app
COPY Gemfile Gemfile.lock /opt/app
RUN  bundle install
```
```docker
VOLUME /opt/app
CMD [ "make", "run" ]
```

<!--s-->
<!-- Orange Gitlab -->
<!-- .slide: data-background="rgba(255,160,59,0.85)" -->

### GitLab
<img src="./images/gitlab.svg" height="150" class="plain"/>

<!--v-->
<!-- .slide: data-background="rgba(255,160,59,0.85)" -->

Open Source ❤️

<!--v-->
<!-- .slide: data-background="rgba(255,160,59,0.85)" -->

<img src="./images/gitlab_screenshot.png" class="plain"/>

<!--v-->
<!-- .slide: data-background="rgba(255,160,59,0.85)" -->

Integrated Docker registry!

<small>`registry.gitlab.com`</small>

Note:
- You can individually manage registry permissions on each project

<!--s-->
<!-- Orange Gitlab -->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

### Gitlab-CI

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

Open Source ❤️

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

Declarative

Note: yaml syntax

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

Integrated

Note:
- MR UI
- Pipeline page

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

Version controlled

👋 `.gitlab-ci.yml`

Note:
- travis / concourse like


<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```yaml
stages:
  - build
  - test
  - package
  - deploy
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```yaml
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}
  LATEST_IMAGE: ${CI_REGISTRY}/${CI_PROJECT_PATH}:latest
```
<br>
```none
build:docker:
  stage: build
```
```none
  tags: [ privileged ]
  image: "docker:latest"
```
```none
  before_script:
    - docker login -u gitlab-ci-token
                   -p ${CI_JOB_TOKEN} ${CI_REGISTRY}
  script:
    - docker pull ${LATEST_IMAGE} || true
    - docker build --cache-from ${LATEST_IMAGE}
                   -t ${IMAGE} -t ${LATEST_IMAGE} .
    - docker push ${IMAGE}
    - docker push ${LATEST_IMAGE}
```
<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}
  LATEST_IMAGE: ${CI_REGISTRY}/${CI_PROJECT_PATH}:latest
```
<br>
```yaml
build:docker:
  stage: build
```
```none
  tags: [ privileged ]
  image: "docker:latest"
```
```none
  before_script:
    - docker login -u gitlab-ci-token
                   -p ${CI_JOB_TOKEN} ${CI_REGISTRY}
  script:
    - docker pull ${LATEST_IMAGE} || true
    - docker build --cache-from ${LATEST_IMAGE}
                   -t ${IMAGE} -t ${LATEST_IMAGE} .
    - docker push ${IMAGE}
    - docker push ${LATEST_IMAGE}
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}
  LATEST_IMAGE: ${CI_REGISTRY}/${CI_PROJECT_PATH}:latest
```
<br>
```none
build:docker:
  stage: build
```
```yaml
  tags: [ privileged ]
  image: "docker:latest"
```
```none
  before_script:
    - docker login -u gitlab-ci-token
                   -p ${CI_JOB_TOKEN} ${CI_REGISTRY}
  script:
    - docker pull ${LATEST_IMAGE} || true
    - docker build --cache-from ${LATEST_IMAGE}
                   -t ${IMAGE} -t ${LATEST_IMAGE} .
    - docker push ${IMAGE}
    - docker push ${LATEST_IMAGE}
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}
  LATEST_IMAGE: ${CI_REGISTRY}/${CI_PROJECT_PATH}:latest
```
<br>
```none
build:docker:
  stage: build
```
```none
  tags: [ privileged ]
  image: "docker:latest"
```
```yaml
  before_script:
    - docker login -u gitlab-ci-token
                   -p ${CI_JOB_TOKEN} ${CI_REGISTRY}
  script:
    - docker pull ${LATEST_IMAGE} || true
    - docker build --cache-from ${LATEST_IMAGE}
                   -t ${IMAGE} -t ${LATEST_IMAGE} .
    - docker push ${IMAGE}
    - docker push ${LATEST_IMAGE}
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}

# (...)
```
```yaml
image: ${IMAGE}
```
```transparent
test:
  stage: test
  script:
    - make test
```
```transparent
package: &package
  stage: package
  script:
    - make package > release.tar.gz
  artifacts:
    paths: [ release.tar.gz ]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}

# (...)
```
```none
image: ${IMAGE}
```
```yaml
test:
  stage: test
  script:
    - make test
```
```transparent
package:jessie: &package
  stage: package
  script:
    - make package > release.tar.gz
  artifacts:
    paths: [ release.tar.gz ]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}

# (...)
```
```none
image: ${IMAGE}
```
```none
test:
  stage: test
  script:
    - make test
```
```yaml
package:
  stage: package
  script:
    - make package > release.tar.gz
  artifacts:
    paths: [ release.tar.gz ]
   
   
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}

# (...)
```
```yaml
deploy:integration:
  stage: deploy
  image: ${CI_REGISTRY}/infra/ansible:latest
  variables:
    ENV: integration
  script:
    - make deploy file=release.tar.gz env=${ENV}
```
```transparent
deploy:production:
  <<: *deploy
  when: manual
  variables:
    ENV: production
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}

# (...)
```
```yaml
deploy:integration: &deploy
  stage: deploy
  image: ${CI_REGISTRY}/infra/ansible:latest
  variables:
    ENV: integration
  script:
    - make deploy file=release.tar.gz env=${ENV}
```
```yaml
deploy:production:
  <<: *deploy
  when: manual
  variables:
    ENV: production
```

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

What about easy `OS` testing and upgrades?!

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->


<small>`Dockerfile`</small>

```docker
FROM ruby:2.4-jessie
```
```none
RUN apt-get update
RUN apt-get -y install libpq-dev ghostscript
```
```none
WORKDIR /opt/app
COPY Gemfile Gemfile.lock /opt/app
RUN  bundle install
```
```none
VOLUME /opt/app
CMD [ "make", "run" ]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->


<small>`Dockerfile`</small>

```docker
FROM ruby:2.4-stretch
```
```none
RUN apt-get update
RUN apt-get -y install libpq-dev ghostscript
```
```none
WORKDIR /opt/app
COPY Gemfile Gemfile.lock /opt/app
RUN  bundle install
```
```none
VOLUME /opt/app
CMD [ "make", "run" ]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```yaml
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${CI_COMMIT_SHA}

# (...)
```
```none
image: ${IMAGE}
```
```transparent
test:jessie: &test
  stage: test
  variables:
    OS: jessie
  script:
    - make test
```
```transparent
test:stretch:
  <<: *test
  variables:
    OS: stretch
```
```transparent
-
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```yaml
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${OS}_${CI_COMMIT_SHA}

# (...)
```
```none
image: ${IMAGE}
```
```transparent
test:jessie: &test
  stage: test
  variables:
    OS: jessie
  script:
    - make test
```
```transparent
test:stretch:
  <<: *test
  variables:
    OS: stretch
```
```transparent
-
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```yaml
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${OS}_${CI_COMMIT_SHA}

# (...)
```
```none
image: ${IMAGE}
```
```yaml
test:jessie:
  stage: test
  variables:
    OS: jessie
  script:
    - make test
```
```transparent
test:stretch:
  <<: *test
  variables:
    OS: stretch
```
```transparent
-
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```yaml
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${OS}_${CI_COMMIT_SHA}

# (...)
```
```none
image: ${IMAGE}
```
```yaml
test:jessie: &test
  stage: test
  variables:
    OS: jessie
  script:
    - make test
```
```yaml
test:stretch:
  <<: *test
  variables:
    OS: stretch
```

```transparent
-
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${OS}_${CI_COMMIT_SHA}

# (...)
```
```none
image: ${IMAGE}
```
```yaml
package:jessie: &package
  stage: package
  variables:
    OS: jessie
  script:
    - make package > release-${OS}.tar.gz
  artifacts:
    paths: [ release-${OS}.tar.gz ]
```
```yaml
package:stretch:
  <<: *package
  variables:
    OS: stretch
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`.gitlab-ci.yml`</small>

```none
variables:
  IMAGE: ${CI_REGISTRY_IMAGE}:${OS}_${CI_COMMIT_SHA}

# (...)
```
```yaml
deploy:integration: &deploy
  stage: deploy
  image: ${CI_REGISTRY}/infra/ansible:latest
  variables:
    OS: stretch
    ENV: integration
  script:
    - make deploy file=release-${OS}.tar.gz env=${ENV}
```
```yaml
deploy:production:
  <<: *deploy
  when: manual
  variables:
    OS: jessie
    ENV: production
```

<!--v-->
<!-- .slide: data-background="rgba(11,85,101,0.85)" -->

<img src="./images/gitlab-pipeline-example.png" class="plain"/>

Note: We build our own docker images within our pipeline but could do it in the open on the docker hub


<!--s-->

### Runners

<img src="./images/gitlab_runner_logo.png" height="150" class="plain"/>

<!--v-->

Different Executors / Multiple OSes
<table>
  <tr>
    <td>
      Shell<br/>
      Docker<br/>
      VirtualBox<br/>
      Parallels<br/>
      SSH<br/>
      Kubernetes<br/>
    </td>
    <td>
      Linux<br/>
      Windows<br/>
      Mac OS X<br/>
      FreeBSD<br/>
    </td>
  </tr>
</table>

<!--v-->

Different Executors / Multiple OSes
<table>
  <tr>
    <td>
      Shell<br/>
      <b>Docker</b><br/>
      VirtualBox<br/>
      Parallels<br/>
      SSH<br/>
      Kubernetes<br/>
    </td>
    <td>
      <b>Linux</b><br/>
      Windows<br/>
      Mac OS X<br/>
      FreeBSD<br/>
    </td>
  </tr>
</table>

<!--v-->

Portable

Note:
- Go binary
- your own laptop can act as a build server

<!--v-->

Light system dependencies

<table>
  <tr>
    <td><img src="./images/tux.png" height="150" class="plain"/></td>
    <td><img src="./images/docker.png" height="150" class="plain"/></td>
    <td><img src="./images/gitlab_runner_logo.png" height="150" class="plain"/></td>
  </tr>
</table>

<!--v-->

Easily configurable and maintainable

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="150" class="plain"/>

```yaml
---
classes:
  - docker
  - gitlab::ci

gitlab::ci::runners:
  "%{::fqdn}_docker":
    executor: docker
    docker-image: docker:latest
```
```transparent
    docker-volumes: "/var/run/docker.sock:/var/run/docker.sock"
    docker-privileged: true
```

Note: Puppet role is as simple as this!

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="150" class="plain"/>

```yaml
---
classes:
  - docker
  - gitlab::ci

gitlab::ci::runners:
  "%{::fqdn}_docker":
    executor: docker
    docker-image: docker:latest
```
```yaml
    docker-volumes: "/var/run/docker.sock:/var/run/docker.sock"
    docker-privileged: true
```

Note: Puppet role is as simple as this!

<!--s-->
<!-- .slide: data-background="rgba(246, 141, 17, .9)" -->

### AWS

<!--s-->
<!-- .slide: data-background="rgba(117, 26, 255, .9)" -->

### Terraform
<img src="./images/terraform.png" height="150px" class="plain"/>

<!--v-->
<!-- .slide: data-background="rgba(117, 26, 255, .9)" -->

Open Source ❤️

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`terraform.tf`</small>

```ruby
resource "aws_instance" "gitlab_runner" {
  count         = 10
  ami           = "ami-6b2cd712"
  instance_type = "m4.large"
  [..]
}
```

<!--s-->
<!-- .slide: data-background="./images/all-is-well-meme.jpg" -->

<!--v-->
<!-- .slide: data-background="rgba(183, 55, 76, .9)" -->

<img src="./images/red-mark-cross.png" class="plain"/>

<!--v-->
<!-- .slide: data-background="rgba(183, 55, 76, .9)" -->

### `MISSINGDEP`

Who had any clue this system library was required?

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### `MISSINGDEP`

Update Dockerfiles with missing dependencies


<!--v-->
<!-- .slide: data-background="rgba(183, 55, 76, .9)" -->

### `ENOSPC`

No space left on device

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### `ENOSPC`

Increase space / Automate cleanup of old containers and images

<!--v-->
<!-- .slide: data-background="rgba(183, 55, 76, .9)" -->

### `UNAUTH_DEPLOY`

Where are my SSH keys for Ansible?

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### `UNAUTH_DEPLOY`

Enhance security by creating individual keys per project/env

<!--v-->
<!-- .slide: data-background="rgba(183, 55, 76, .9)" -->

### `SHM_OOM`

Less than 64MB of free space in temporary directory for shared memory files

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### `SHM_OOM`

Configure max SHM size

<!--v-->
<!-- .slide: data-background="rgba(183, 55, 76, .9)" -->

### `IOWAIT`

On heavy load tests

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### `IOWAIT`

Bigger disks

Provisioned IOPS

Leverage `tmpfs`

<!--s-->
<!-- .slide: data-background="./images/all-is-well-meme.jpg" -->

<!--v-->
<!-- .slide: data-background="./images/traffic-jam.jpg" -->

<!--v-->
<!-- .slide: data-background="./images/empty_railtrack.jpg" -->

<!--s-->
<!-- .slide: data-background="rgba(246, 141, 17, .9)" -->

### AWS

<!--s-->
<!-- .slide: data-background="rgba(0, 138, 183, .9)" -->

### Docker

<!--s-->
<!-- .slide: data-background="rgba(117, 26, 255, .9)" -->

### Terraform

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<small>`terraform.tf`</small>

```ruby
resource "aws_autoscaling_group" "gitlab_runner" {
  desired_capacity     = 10
  min_size             = 4
  max_size             = 24
  launch_configuration = "${aws_launch_configuration.runner.name}"
  [..]
}
```

<!--s-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### 💡 We can do better and easier!

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### Ourselves

with an interesting challenge

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### Software engineers

with a reliable CI implementation

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### Finance

by making some savings

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

👋 `docker-machine` integrated

**out-of-the-box** with `gitlab-runner`

scheduling jobs on `spot` instances 💸

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="90" class="plain" style='float:right;'/>

```yaml
gitlab::ci::runners:
  'aws_spot_docker_machine':
```
```none
    executor: docker+machine
```
```none
    limit: 24
```
```none  
    machine-IdleCount: 4
    machine-IdleTime: 600
```
```none
    machine-OffPeakPeriods:
      - "* * 0-8,18-23 * * mon-fri *"
      - "* * * * * sat,sun *"
    machine-OffPeakIdleCount: 0
    machine-OffPeakIdleTime: 600
```
```none
    machine-MaxBuilds: 30
```
```none
    machine-MachineDriver: amazonec2
    machine-MachineOptions:
      - amazonec2-instance-type=m4.large
      - amazonec2-request-spot-instance=true
      - amazonec2-spot-price=0.10
      [..]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="90" class="plain" style='float:right;'/>

```yaml
gitlab::ci::runners:
  'aws_spot_docker_machine':
```
```yaml
    executor: docker+machine
```
```none
    limit: 24
```
```none  
    machine-IdleCount: 4
    machine-IdleTime: 600
```
```none
    machine-OffPeakPeriods:
      - "* * 0-8,18-23 * * mon-fri *"
      - "* * * * * sat,sun *"
    machine-OffPeakIdleCount: 0
    machine-OffPeakIdleTime: 600
```
```none
    machine-MaxBuilds: 30
```
```none
    machine-MachineDriver: amazonec2
    machine-MachineOptions:
      - amazonec2-instance-type=m4.large
      - amazonec2-request-spot-instance=true
      - amazonec2-spot-price=0.10
      [..]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="90" class="plain" style='float:right;'/>

```yaml
gitlab::ci::runners:
  'aws_spot_docker_machine':
```
```yaml
    executor: docker+machine
```
```yaml
    limit: 24
```
```none  
    machine-IdleCount: 4
    machine-IdleTime: 600
```
```none
    machine-OffPeakPeriods:
      - "* * 0-8,18-23 * * mon-fri *"
      - "* * * * * sat,sun *"
    machine-OffPeakIdleCount: 0
    machine-OffPeakIdleTime: 600
```
```none
    machine-MaxBuilds: 30
```
```none
    machine-MachineDriver: amazonec2
    machine-MachineOptions:
      - amazonec2-instance-type=m4.large
      - amazonec2-request-spot-instance=true
      - amazonec2-spot-price=0.10
      [..]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="90" class="plain" style='float:right;'/>

```yaml
gitlab::ci::runners:
  'aws_spot_docker_machine':
```
```yaml
    executor: docker+machine
```
```yaml
    limit: 24
```
```yaml  
    machine-IdleCount: 4
    machine-IdleTime: 600
```
```none
    machine-OffPeakPeriods:
      - "* * 0-8,18-23 * * mon-fri *"
      - "* * * * * sat,sun *"
    machine-OffPeakIdleCount: 0
    machine-OffPeakIdleTime: 600
```
```none
    machine-MaxBuilds: 30
```
```none
    machine-MachineDriver: amazonec2
    machine-MachineOptions:
      - amazonec2-instance-type=m4.large
      - amazonec2-request-spot-instance=true
      - amazonec2-spot-price=0.10
      [..]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="90" class="plain" style='float:right;'/>

```yaml
gitlab::ci::runners:
  'aws_spot_docker_machine':
```
```yaml
    executor: docker+machine
```
```yaml
    limit: 24
```
```yaml  
    machine-IdleCount: 4
    machine-IdleTime: 600
```
```yaml
    machine-OffPeakPeriods:
      - "* * 0-8,18-23 * * mon-fri *"
      - "* * * * * sat,sun *"
    machine-OffPeakIdleCount: 0
    machine-OffPeakIdleTime: 600
```
```none
    machine-MaxBuilds: 30
```
```none
    machine-MachineDriver: amazonec2
    machine-MachineOptions:
      - amazonec2-instance-type=m4.large
      - amazonec2-request-spot-instance=true
      - amazonec2-spot-price=0.10
      [..]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="90" class="plain" style='float:right;'/>

```yaml
gitlab::ci::runners:
  'aws_spot_docker_machine':
```
```yaml
    executor: docker+machine
```
```yaml
    limit: 24
```
```yaml  
    machine-IdleCount: 4
    machine-IdleTime: 600
```
```yaml
    machine-OffPeakPeriods:
      - "* * 0-8,18-23 * * mon-fri *"
      - "* * * * * sat,sun *"
    machine-OffPeakIdleCount: 0
    machine-OffPeakIdleTime: 600
```
```yaml
    machine-MaxBuilds: 30
```
```none
    machine-MachineDriver: amazonec2
    machine-MachineOptions:
      - amazonec2-instance-type=m4.large
      - amazonec2-request-spot-instance=true
      - amazonec2-spot-price=0.10
      [..]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/puppet.png" height="90" class="plain" style='float:right;'/>

```yaml
gitlab::ci::runners:
  'aws_spot_docker_machine':
```
```yaml
    executor: docker+machine
```
```yaml
    limit: 24
```
```yaml  
    machine-IdleCount: 4
    machine-IdleTime: 600
```
```yaml
    machine-OffPeakPeriods:
      - "* * 0-8,18-23 * * mon-fri *"
      - "* * * * * sat,sun *"
    machine-OffPeakIdleCount: 0
    machine-OffPeakIdleTime: 600
```
```yaml
    machine-MaxBuilds: 30
```
```yaml
    machine-MachineDriver: amazonec2
    machine-MachineOptions:
      - amazonec2-instance-type=m4.large
      - amazonec2-request-spot-instance=true
      - amazonec2-spot-price=0.10
      [..]
```
<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

<img src="./images/aws-spot-instances.png" />

<!--s-->
<!-- .slide: data-background="./images/all-is-well-meme.jpg" -->

<!--s-->
<!-- .slide: data-background="rgba(0, 128, 255, .1)" -->

### A small drawback..

<!--v-->
<!-- .slide: data-background="rgba(0, 128, 255, .1)" -->

### Scheduling

Note:
 - There are a few issues opened on both GitLab and docker-machine for some minor bugs.
 - The scheduling of the containers is not very efficient and we do not use our instances at top capacity.
 - Job density per instance is not optimum

<!--v-->
<!-- .slide: data-background="rgba(0, 128, 255, .1)" -->

### 👋 Kubernetes

<img src="./images/kubernetes.png" height="150" class="plain"/>

Note:
  - As we plan on scheduling some containers workloads onto Kubernetes we have given it a try and it seems very interesting as well

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

<img src="./images/kubernetes.png" height="110" class="plain"/>

```yaml
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: gitlab-runner
  namespace: gitlab-ci
data:
  config.toml: |
    [[runners]]
      name = "k8s_runner"
      url = "https://gitlab.example.com/"
      executor = "kubernetes"
      [runners.kubernetes]
        cpu_limit = "1"
        memory_limit = "256Mi"
        [..]
```

<!--v-->
<!-- .slide: data-background="rgba(33, 33, 33, .8)" -->

```shell
~$ kubectl -n gitlab-ci get po
NAME                    READY     STATUS    RESTARTS   AGE
runner-315e4d80-0qj79g  2/2       Running   0          3m
runner-315e4d80-9kdkee  2/2       Running   0          2m
runner-315e4d80-kdfdfe  2/2       Running   0          1m
runner-315e4d80-ldorpk  2/2       Running   0          1m
runner-315e4d80-pleofi  2/2       Running   0          20s
```

<!--s-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### Definitely promising

<!--v-->
<!-- .slide: data-background="rgba(96, 169, 105, .9)" -->

### Still a work in progress for us

<!--v-->

<img src="./images/architecture_diagram.png" class="plain"/>

<!--s-->

## Questions?

<!--v-->

## References

* <small>`Dockerfile`</small> documentation

<small>**https://docs.docker.com/engine/reference/builder/**</small>

* <small>`.gitlab-ci.yml`</small> documentation

<small>**https://gitlab.com/help/ci/yaml/README.md**</small>

* Slides<br/> <small>**http://polr.fr/tiaddocker**</small>
