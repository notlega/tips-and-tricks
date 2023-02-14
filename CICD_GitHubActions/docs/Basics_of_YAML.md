# Basics of YAML

This topic covers the history of the language YAML, as well as the basic syntax to get you started.

## History

YAML stands for "Yet Another Markup Language", which is pretty weird.

It was first proposed by Clark Evans back in 2001.

He went on to design the language together with Ingy döt Net and Oren Ben-Kiki.

It is a data serialisation language often used to create configuration files with any programming language (Sharma, 2022).

YAML is a strict superset of JSON and it was designed for human interaction.

A major difference between YAML and JSON is that newlines and indentations are used in YAML, while JSON uses brackets and braces.

## How to YAML

The basic structure of a YAML file is called a map.

It is written in a key-value pair format from top to bottom.

```yaml
key: value
```

### Scalar Types

You can use all types of scalar types as values in YAML files.

For example:
- Numbers
- Booleans
- Strings (Quoted or Unquoted)

Words in keys can be separated by underscores.

Generally, people use underscores.

If the value of a key is a multi-line string, you can use the "literal block" style using the "|" character.

This is extremely helpful when writing shell commands.

```yaml
command: |
    if [ "${BRANCH_NAME}" == "main" ];
        then <do something>;
    fi
```

The leading indentation for the multi-line string will be removed.

### Collection Types

To create collections, use indentations.

```yaml
job:
    build:
        <build script here>
```

If you have a list of items (like docker images), you can denote that sequence using dashes.

```yaml
docker:
    - image: ubuntu:14.04
    - image: mongo:2.6.8
	  command: [mongod, --smallfiles]
    - image: postgres:9.4.1
```

The second item in the sequence has two keys: `image` and `command`.

The `command` key uses a JSON-style sequence because YAML is a superset of JSON.

YAML does not allow tab characters, so have your editor convert them into spaces.

Syntax errors can be an issue, but you can either run the YAML file through an online validator or install linters on your text editors.

## Previous Topic

[Why create a CI/CD pipeline with GitHub Actions](./Why_Create_A_CICD_Pipeline_With_GitHub_Actions.md)

## Next Topic

[Creating a basic CI/CD pipeline with GitHub Actions](./Creating_a_basic_CICD_pipeline_with_GitHub_Actions.md)
