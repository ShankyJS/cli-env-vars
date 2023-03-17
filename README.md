# Reproduce the scenario

This repo intends to demonstrate that Garden deploys with --var option doesn't work to replace the environments[].defaultNamespace field;

````bash
garden deploy --var installCRDs=true --var name=shankyjs
````

Result of the above command:

````bash
➜  cli-env-vars git:(master) ✗ garden deploy --var installCRDs=true --var name=shankyjs
Deploy 🚀


Invalid template string (user-${var.name}): Could not find key name under var.
````

## Expected result

- Garden should be able to replace the defaultNamespace field by providing env vars from the `--var` global option.

## Reproduce the issue

Try to run this configuration with the command `garden deploy  --var installCRDs=true --var name=shankyjs`
