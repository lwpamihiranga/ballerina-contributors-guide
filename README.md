# Ballerina Contributors Guide

This repository contains helpful tips for anyone looking to start contributing to the Ballerina open-source project. When I first became interested in contributing to Ballerina, I struggled to find certain information, so I created this repo to share what I’ve learned along the way. While these tips may seem simple, I hope they will be valuable to others on their journey to becoming Ballerina contributors.

Please note that I’m still at the beginning of my own journey, and I’ll be continuously adding more tips as I learn.

> Note: The tips and configurations provided in this guide are based on the tools I use—OS: Pop!_OS, Shell: Zsh, and IDE: IntelliJ IDEA Community Edition. However, the instructions should generally apply to other environments and tools as well, as the overall setup and configurations are quite similar across platforms.

## Pre-requisites

- Start by following the [Download and Install](https://github.com/ballerina-platform/ballerina-distribution?tab=readme-ov-file#download-and-install) instructions in the [ballerina-distribution](https://github.com/ballerina-platform/ballerina-distribution) repository on how to set up Ballerina.

- Next, review the [Contribution Guidelineas](https://github.com/ballerina-platform/ballerina-lang/blob/master/CONTRIBUTING.md) in the [ballerina-lang](https://github.com/ballerina-platform/ballerina-lang) repository to understand the process and expectations for contributing.

## How to build locally

You can run the below command in the root for repository directory. `-x test -x check` flags avoid running tests & checks to make the local build faster.

```shell
./gradlew build -x test -x check
```
![build ballerina](https://github.com/user-attachments/assets/3150aa74-8973-498e-872e-708901ea6593)

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

![run_using_build](https://github.com/user-attachments/assets/5cbdffb3-7954-4e5a-af58-e1eb26653129)

## How to debug attaching a debugger

To debug by attaching a debugger, follow these steps:

- Step 1: Set Up the Debugging Environment

First, configure the necessary environment variable to enable debugging. Set the `BAL_JAVA_DEBUG` variable to the desired port (e.g., `5005`):

```shell
export BAL_JAVA_DEBUG=5005
```

- Step 2: Run the `bal` command 

Execute the desired `bal` command (e.g., `bal build`, `bal run`), and you'll see a message indicating that the debugger is listening on the specified port:

- Step 3: Configure IntelliJ IDEA for Debugging
    
    - Open IntelliJ IDEA.
    - Navigate to **Run -> Edit Configurations**.
    - Click **Add** and select **Remote JVM Debug**.
    - Configure the remote debugger settings, ensuring the port matches the one set in Step 1 (`5005`). The default configuration should work fine.
    - Set a meaningful **Name** for the configuration, then click **Apply**.

- Step 4: Set Breakpoints and Start Debugging 

    - Add breakpoints in your code where you want the debugger to pause.
    - Run the configuration you created in IntelliJ IDEA.
    - The debugger will attach to the running process, and execution will pause at the breakpoints you set. You can now inspect variables, step through code, and debug as needed.

## Setting Up Ballerina VS Code Extension for Debugging

- Step 1: Enable Plugin Development Mode
    
    - Open VS Code and go to the Ballerina Extension Settings.
    - Enable the `Plugin Dev Mode` checkbox to allow the use of the locally built Ballerina distribution.

- Step 2: Set the Ballerina Home Path

Set the `Home` path to the distribution pack you built from the Ballerina platform repository:

```bash
<BASE_PATH>/ballerina-lang/distribution/zip/jballerina-tools/build/extracted-distributions/jballerina-tools-<VERSION>-SNAPSHOT
```

- Step 3: Restart VS Code

To apply the changes, restart VS Code.

### Alternative: Configure via settings.json

Alternatively, you can directly configure these settings in your VS Code `settings.json` file:

```json
{
    "ballerina.pluginDevMode": true,
    "ballerina.home": "<BASE_PATH>/ballerina-lang/distribution/zip/jballerina-tools/build/extracted-distributions/jballerina-tools-<VERSION>-SNAPSHOT"
}
```

Once the configuration is set, restart VS Code, and the extension will use the locally built Ballerina distribution for debugging and other features.
