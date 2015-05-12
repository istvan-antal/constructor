# Constructor

Constructor is a tool that can build up infrastructure in an automated way.

The main design goal of constructor was to have infrastructure specifications(blueprints) in code in a versioned manner.

Another important goal of Constructor is to be transparent about everything, show what goes on under the hood rather than try to hide it.

## Setup

```sh
pip install constructor
```

Log in to the AWS console.

Create a personal access key with Administrator privileges.

Run:

```sh
construct --init
```