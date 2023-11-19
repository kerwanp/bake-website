---
title: Your first command
---


# Write your first command 

Bake configuration uses [KDL](https://github.com/kdl-org/kdl), an alternative to YAML and JSON.

Create a file called `bake.kdl` and paste the following content:

```kdl
name "bake"

command "greet" {
    description "Greet someone!"

    exec {
        run "echo Hello World"
    }
}
```

It is now time to execute your first command by running `bake greet`:

```bash
$ bake greet

Hello world
```

:::tip
You can see the help page of your CLI by running `bake -h`
:::


## Add an argument

We are going to add an argument to our command to greet a specific person.
Bake uses [Handlebars](https://handlebarsjs.com/) under the hood, giving you the ability to use the arguments in the executed commands.

```kdl title="bake.dkl"
name "bake"

command "greet" {
    description "Greet someone!"

    argument "to"

    exec {
        run "echo Hello {{to}}"
    }
}
```

```txt
$ bake greet Martin

Hello Martin
```

:::info
Read more about arguments [here](#)
:::

## Run multiple commands

Let's take a real scenario. We are going to create a `setup` command that will install `npm` and `composer` dependencies.
We can also add the `parallel` option to run them simultaneously.

```kdl
command "setup" {
    description "Install dependencies"

    exec {
        parallel
        run "npm install"
        run "composer install"
    }
}
```
