# Config-Pipelines

This repository contains a collection of basic and generalized pipelines for Android Studio projects. These pipelines are designed to facilitate continuous integration and continuous delivery (CI/CD) by automating build tests, JUnit tests, and Android tests, as well as automatic deployments to production using JitPack.

## Contents

The following workflows are included in this repository:

### 1. Android API Test

This pipeline is used to run instrumented tests on different levels of Android API. It performs the following actions:

- Runs tests on emulators with different API configurations (23, 27, 29).
- Sets up the Android environment and prepares the emulator.
- Runs instrumented tests on the configured emulator.

**Trigger:** This workflow is activated on `push` and `pull_request` to the specified branch.

```yaml
name: [Workflow Name] / Android Api Test

on:
  push:
    branches:
      - [branch]
  pull_request:
    branches:
      - [branch]

jobs:
  test:
    ...
```

### 2. Release to Production

This pipeline automates the process of building and releasing versions of your application to production on JitPack. It includes the following steps:

- Builds the project using Gradle.
- Retrieves the version from the `build.gradle.kts` file.
- Creates a tag and publishes it to the repository.
- Creates a release on GitHub and publishes it to JitPack.

**Trigger:** This workflow is activated on `push` to the specified branch.

```yaml
name: Release to Production

permissions:
  contents: write

on:
  push:
    branches:
      - [branch]

jobs:
  build:
    ...
```

### 3. Build and Unit Tests

This pipeline is used to build the project and run unit tests. The steps include:

- Checks out the code.
- Sets up JDK and Gradle.
- Builds the application and runs unit tests.

**Trigger:** This workflow is activated on `push` and `pull_request` to the specified branch.

```yaml
name: [Workflow Name] / Build and Unit Tests

on:
  push:
    branches:
      - [branch]
  pull_request:
    branches:
      - [branch]

jobs:
  build:
    ...
```

## How to Use

1. **Clone the repository:**

   ```bash
   git clone https://github.com/darkryh/Config-Pipelines.git
   ```

2. **Configure the workflows:**
   - Modify the `[branch]` and `java-version` values as needed in the YAML files.
   - Ensure that the necessary GitHub secrets are configured for deployment.

3. **Push to your specified branch to trigger the workflows.**

# Want to collaborate
if you want to help or collaborate, feel free to contact me on X account @Darkryh or just make a request.
