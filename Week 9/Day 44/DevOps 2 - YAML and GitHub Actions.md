#data-engineering 

---

### YAML

**YAML Ain't a Markup Language**.

A markup language designed primarily for humans rather than computers.

Structurally similar to JSON, except indentation defines the structure, like in Python.

### YAML example

```yaml
# Strings don't need quotes (this is a comment BTW)
key1: hello
key2:
  # You can nest keys
  subkey1: 1
  subkey2: hello
  # You can also make lists
  subkey3:
    - listitem1
    - listitem2
    - listitem3
```

---

### GitHub Actions Example

> Let's have a look together at the file `devops/handouts/python-project-example.yml`

This file shows how we might setup a GitHub action to run things for a python project:

```yml
# Name your job/action
name: Python application
# When to run this job
on: [push]

jobs:
    build:
    # Which operating system to test on - e.g. "macos-latest, ubuntu-latest, windows-latest"
    runs-on: [ ubuntu-latest ]

    # The steps to run in the job
    steps:
        # Checkout code from github
      - name: Checkout code
        uses: actions/checkout@v2

        # Install python
      - name: Set up Python
        uses: actions/setup-python@v1
        with:
            python-version: [ 3.10 ]

        # Run pip to install all packages/dependencies
      - name: Install dependencies
        run: pip install -r requirements.txt

        # Further tasks
      - name: Another task
        run : echo "run something here, like your unit tests"

      - name: Another Another task
        run: echo "run another command"
```

### Demo: GitHub Actions

Creating a new GitHub Actions workflow from scratch

Notes: Demonstrate to the class adding a GitHub actions workflow to a repository using the provided `example-action.yml`

Any repository is suitable

Talk learners through the syntax of the file and what function each part of it performs

Recommend that you:

1. Code the yml file step-by step rather than pasting it in whole
2. Create the workflow file in VSCode in the `.github/workflows/` directory and push it
    1. This will demonstrate how workflows are discovered by convention if placed in the appropriate location (as opposed to if creating it via the GitHub web interface)