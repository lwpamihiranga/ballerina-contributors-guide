# Ballerina Contributors Guide

This repository contains helpful tips for anyone looking to start contributing to the Ballerina open-source project. When I first became interested in contributing to Ballerina, I struggled to find certain information, so I created this repo to share what I’ve learned along the way. While these tips may seem simple, I hope they will be valuable to others on their journey to becoming Ballerina contributors.

Please note that I’m still at the beginning of my own journey, and I’ll be continuously adding more tips as I learn.

## Pre-requisites

- Start by following the [Download and Install](https://github.com/ballerina-platform/ballerina-distribution?tab=readme-ov-file#download-and-install) instructions in the [ballerina-distribution](https://github.com/ballerina-platform/ballerina-distribution) repository on how to set up Ballerina.

- Next, review the [Contribution Guidelineas](https://github.com/ballerina-platform/ballerina-lang/blob/master/CONTRIBUTING.md) in the [ballerina-lang](https://github.com/ballerina-platform/ballerina-lang) repository to understand the process and expectations for contributing.

## How to build locally

You can run the below command in the root for repository directory. `-x test -x check` flags avoid running tests & checks to make the local build faster.

```shell
./gradlew build -x test -x check
```

## How to run after build

Once you've successfully build Ballerina, you can use the extracted `bal` executor in extracted zip.

To build you project, use the following command:

```shell
<BASE_PATH>/ballerina-lang/distribution/zip/jballerina-tools/build/extracted-distributions/jballerina-tools-<VERSION>-SNAPSHOT/bin/bal build
```

### Setting the Path for the Current Shell

To simplify the use of `bal` commands (e.g., `bal build`, `bal run`), you can temporarily add the build directory to your shell's `PATH`. Run this command in your terminal:

```shell
PATH=<BASE_PATH>/ballerina-lang/distribution/zip/jballerina-tools/build/extracted-distributions/jballerina-tools-<VERSION>-SNAPSHOT/bin:$PATH
```

After setting the `PATH`, you can directly use `bal` commands in your shell session, and it will reference the newly built binaries.
