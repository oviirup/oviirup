# Run GitHub Actions Locally

GitHub Actions is a powerful tool for automating continuous integration and deployment workflows. It allows you to define custom workflows using YAML file syntax and execute them in response to various events on GitHub. While GitHub Actions provides a convenient way to automate your software development processes, it can be useful to test and debug your workflows locally before committing or pushing them to your GitHub repository. This is where Nekto's `act` tool comes in.

## Introducing Nekto's Act

`act` is an open-source command-line tool developed by Nekto. It enables you to run GitHub Actions workflows locally, simulating the environment and event triggers that occur in a GitHub Actions workflow. By running your workflows locally, you can test and debug them more efficiently, iterate faster, and identify issues before they affect your production environment.

### Key Features

`act` provides several key features that make local testing of GitHub Actions workflows seamless and effective:

1. **Full compatibility**: `act` aims to provide full compatibility with GitHub Actions, ensuring that workflows behave as expected during local testing.

2. **Docker integration**: `act` utilizes Docker containers to simulate the environment in which your actions would run on GitHub. This ensures a consistent and isolated testing environment.

3. **Workflow and job filtering**: `act` allows you to specify which workflows or jobs to run, enabling you to focus on specific parts of your workflow during local testing.

4. **Event simulation**: `act` lets you simulate various events that trigger your workflows on GitHub, such as push events, pull request events, or scheduled events.

### Installation

Before getting started with `act`, you need to have Docker installed on your machine. Docker is an essential component as `act` relies on it to run the workflow containers locally. You can download Docker from their official website: [docker.com](https://www.docker.com/).

Once Docker is installed, you can proceed with installing `act`. The installation process involves downloading the appropriate binary for your operating system and placing it in your system's `PATH`. Detailed installation instructions can be found in the `act` repository on GitHub: [nektos/act](https://github.com/nektos/act).

### Running GitHub Actions locally with act

To illustrate how `act` can be used to run GitHub Actions workflows locally, let's consider a sample repository: [github-actions-demo](https://github.com/cplee/github-actions-demo). This repository contains a basic GitHub Actions workflow that builds and tests a simple Go application.

1. Clone the repository:

   ```
   git clone https://github.com/cplee/github-actions-demo
   cd github-actions-demo
   ```

2. Inspect the workflow file:

   Open the `.github/workflows/main.yml` file to see the details of the workflow. This file contains the steps and actions that will be executed when triggered.

3. Run the workflow with `act`:

   Run the following command to execute the GitHub Actions workflow locally:

   ```
   act
   ```

   `act` will automatically detect the workflow file in the repository and start the local execution.

4. Observe the output:

   As the workflow runs, you will see the output of each step, just like on GitHub. This allows you to check the status, logs, and any errors that occur during the execution of the workflow.

### Workflow and Job Filtering

`act` provides the ability to selectively execute only specific workflows or jobs, which can be quite useful for targeted testing. You can use the `--list` flag to view all available workflows and jobs within the repository, and then specify the desired workflow or job using the `--workflow` or `--job` options.

For example, to run only the `build` job from the main workflow in the `github-actions-demo` sample repository, you can use the following command:

```
act --job build
```

This will execute only the `build` job, providing a faster feedback loop when testing specific steps of your workflow.

### Conclusion

`act` by Nekto is an invaluable tool for running GitHub Actions workflows locally. With its Docker integration and event simulation capabilities, you can thoroughly test and debug your workflows before deploying them to GitHub. This allows for rapid iteration and helps ensure that your workflows function as expected in a controlled environment.

To explore more about GitHub Actions itself, refer to the official GitHub Actions documentation: [docs.github.com/en/actions](https://docs.github.com/en/actions).

To get started with `act`, visit the official repository on GitHub: [nektos/act](https://github.com/nektos/act).

If you'd like to experiment with testing a GitHub Actions workflow locally, the `github-actions-demo` repository serves as a great
