# Extra Tips

## Linting

Since this might be the first time learning YAML, syntax errors might be normal occurrences.

Testing YAML files is also quite tough as there is no normal way to debug them.

To solve this issue, a linter can be installed to link the file before submitting it.

If you are using Visual Studio Code, I recommend the YAML extension by Red Hat.

![](yaml-linter.png)

It is also possible to run the code through an online validator such as [https://www.yamllint.com/](https://www.yamllint.com/).

## GitHub Secrets

GitHub Secrets is a place to store encrypted variables.

They can be created in an organisation, repository, or repository environment.

These encrypted variables can be used in workflows instead of saving the values in plaintext format.

For example, environment variables should be stored in GitHub Secrets instead of being stored plaintext inside your repository.

If leaked out, this might cause a lot of trouble.

### Naming secrets

-   Names can only contain alphanumeric characters (`[a-z]`, `[A-Z]`, `[0-9]`) or underscores (`_`). Spaces are not allowed.
    
-   Names must not start with the `GITHUB_` prefix.
    
-   Names must not start with a number.
    
-   Names are not case-sensitive.
    
-   Names must be unique at the level they are created at.

### Creating secrets for a repository

1.  On GitHub.com, navigate to the main page of the repository.
2. Under your repository name, click **Settings**.

![](../images/repo-actions-settings.png)

3. In the "Security" section of the sidebar, select  **Secrets and variables**, then click **Actions**.
4. Click the **Secrets** tab.

![](../images/actions-secrets-tab.png)

5. Click **New repository secret**.
6. Type a name for your secret in the **Name** input box.
7. Enter the value for your secret.
8. Click **Add secret**.

### Accessing secrets

Access the secrets using the `secrets` context.

```yaml
steps:
  - name: Hello world action
    with: # Set the secret as an input
      super_secret: ${{ secrets.SuperSecret }}
    env: # Or as an environment variable
      super_secret: ${{ secrets.SuperSecret }}
```

## Caching dependencies to speed up workflows

Workflow runs usually reuse the same downloaded dependencies and outputs over multiple runs.

For example, package and dependency management tools such as Maven, Gradle, npm, and Yarn keep a local cache of downloaded dependencies.

To help speed up the time it takes to recreate files like dependencies, GitHub can cache files you frequently use in workflows.

To cache dependencies for a job, you can use GitHub's [`cache` action](https://github.com/actions/cache).

The action creates and restores a cache identified by a unique key.

To use caching, visit [THIS LINK](https://github.com/actions/cache) to learn caching using various languages.

## Previous Topic

[Workflow Syntax for GitHub Actions](Workflow_Syntax_for_GitHub_Actions.md)

## Next Topic

[Glossary](./Glossary.md)
