# Flat Yaml Envsubst

Substitutes env variables listed in flat `env.yaml`.
By default `SUBST_PREFIX` is `K_`. This means if `env.yaml` contains a key/value pair `FOO: bar`, placeholders `${K_FOO}` in target dirs will be replaced with `bar`.

## Usage

### Prepare

env.yaml:
```
FOO: bar
```

```yaml
# target-dir-1/f.yaml
substitution: "I am a cool ${YENV_FOO}."
```

```yaml
# target-dir-2/f.yaml
name: ${YENV_FOO}
```

### Execute

Run `subst`:
```sh
SUBST_PREFIX=YENV_ ./subst target-dir-1/f.yaml target-dir-2/f.yaml
```

### Result

```yaml
# target-dir-1/f.yaml
substitution: "I am a cool bar."
```

```yaml
# target-dir-2/f.yaml
name: bar
```

## Limitations

- No directories with names containing spaces
