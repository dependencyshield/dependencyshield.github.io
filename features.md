---
title: Features
layout: article
description: Features
---

# Features

## How it works
Dependency Shield serves as an addition to the [OWASP Dependency Check](https://owasp.org/www-project-dependency-check/). 
It exposes a suppression file that is consumed by OWASP Dependency check. Additionally, it exposes an API where you can 
upload your dependency check reports.

Once the reports are uploaded, you can use Dependency Shield UI to make decisions about the vulnerabilities. If you
identify a false positive, you can suppress it and the suppression gets automatically propagated to all connected projects.

## Reports
You can see results of your dependency check reports in Dependency Shield and address the projects that need your attention 

![Reports](/images/screenshots/reports.png){:class="shadow screenshot"}

## Report detail
In report detail you can see the details of the vulnerabilities and decide what to do with them. Either you upgrade 
(manually so far) or suppress the vulnerability if it's a false positive.

![Report detail](/images/screenshots/report-detail.png){:class="shadow screenshot"}

## Usage
Currently, only Gradle is supported out of the box. You add it to you project like this:

```kotlin
plugins {
    id("com.dependencyshield.gradle") version "0.0.6"
}
...
dependencyShield {
    organizationId.set("<GET THIS IN THE APP>")
    configurationId.set("<GET THIS IN THE APP>")
    apiKey.set("<GET THIS IN THE APP>")
}
```
Once the plugin is applied, it will configure OWASP Dependency Check to download the suppression file and upload the report.
You can see the plugin source code [here](https://github.com/dependencyshield/gradle-plugin).

