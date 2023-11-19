# Templating


## Helpers

### short_flag

Renders the short version of the specified flag.
Example:

```kdl
(bool)flag "detach" "d"

exec {
    run "docker compose up {{short_flag detach}}"
}
```

```txt
Output: docker compose up -d
```

### long_flag

Renders the long version of the specified flag.
Example:

```kdl
(bool)flag "detach" "d"

exec {
    run "docker compose up {{long_flag detach}}"
}
```

```txt
Output: docker compose up --detach
```
### short_flags

Renders the short version of all the flags.

Example:

```kdl
(bool)flag "detach" "d"
(bool)flag "build" "b"

exec {
    run "docker compose up {{short_flags}}"
}
```

```txt
Output: docker compose up -db
```

### long_flags

Renders the long version of all the flags.

Example:

```kdl
(bool)flag "detach" "d"
(bool)flag "build" "b"

exec {
    run "docker compose up {{long_flags}}"
}
```

```txt
Output: docker compose up --detach --build
```
