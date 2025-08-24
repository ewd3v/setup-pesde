<div align="center">
  <h1><code>setup-pesde</code></h1>
  <p>
    <a href="https://github.com/ewd3v/setup-pesde/actions?query=workflow%3Atest"><img src="https://github.com/ewd3v/setup-pesde/workflows/test/badge.svg" alt="test" /></a>
  </p>
</div>

GitHub action to install and run [pesde](https://github.com/pesde-pkg/pesde); a Luau package manager.

## Usage

Use the latest released version of `pesde` with default parameters:

```yaml
steps:
    - uses: ewd3v/setup-pesde@v0.1.0
```

For a list of default parameter values, [check here](https://github.com/ewd3v/setup-pesde/blob/main/action.yml#L5-L20).

### Advanced

For more advanced cases, use the parameters below.

```yaml
steps:
    - uses: ewd3v/setup-pesde@v0.1.0
      with:
          version: v0.7.0 # name of git tag in pesde (uses latest tag by default)
          path: some_dir/my_project # path to project dir containing `pesde.toml` ("." (current dir) by default)
          cache: false # whether to enable caching between runs (false by default)
          token: ${{ github.token }} # GitHub token to bypass rate limit (${{ github.token }} set by default)
```

## Inputs

### `version`

The git tag of `pesde` to install from releases and use. By default this input will be assigned to the latest version of `pesde`.

### `path`

The path to the directory containing the `pesde.toml` to install packages from. The default is the current directory (`.`).

### `cache`

Enable to cache packages installed by `pesde`, the default value of this input is `false`. Note, in many cases enabling this feature will slow down the `setup-pesde` action.

There are a few reasons you may choose to enable caching:

-   Action runs often, causing the GitHub rate-limit to be reached
-   A large amount of tools to install
-   Server downloading from is slow

In any case, it is recommended to benchmark before enabling this feature.

### `token`

Set to a GitHub token to be used while downloading and authenticating with `pesde`. Note, these two options, `${{ github.token }}` and `${{ secrets.GITHUB_TOKEN }}`, are equivalent and passed by default. **Thus, you do not need to specify this parameter unless you are using a token different from the owner of the repository.**

## Credits

[@ok-nick](https://github.com/ok-nick) - For creating `setup-aftman` (which this is a fork of)
