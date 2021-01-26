# pipeline-library-demo

Demonstrates how to use a Shared Library in Jenkins pipelines. This repository defines a single function, `sayHello`, which will echo a greeting.

## Setup instructions

1. In Jenkins, go to Manage Jenkins &rarr; Configure System. Under _Global Pipeline Libraries_, add a library with the following settings:

    - Name: `jenkins_demo`
    - Default version: Specify a Git reference (branch or commit SHA), e.g. `master`
    - Retrieval method: _Modern SCM_
    - Select the _Git_ type
    - Project repository: `https://github.com/mathanika/jenkins_demo.git`
    - Credentials: (leave blank)

2. Then create a Jenkins job with the following pipeline (note that the underscore `_` is not a typo):

    ```
    @Library('jenkins_demo')_

    stage('Demo') {

      echo 'Hellooo'
   
      sayHello 'Mathanika'

    }
    ```

This will output the following from the build:

```
[Pipeline] stage
[Pipeline] { (Demo)
[Pipeline] echo
Hellooo
[Pipeline] echo
Hello, Mathanika.
[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
Finished: SUCCESS
```

