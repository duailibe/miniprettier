# miniprettier

A zero config plugin for running Prettier in Atom. It was inspired by @t9md's [mprettier] but changed to suit my needs.

- no autosave
- no ESLint support
- zero config (you can set prettier default options to format inside projects that don't use prettier)
- cursor support

## How to use?

Run `miniprettier:format` or `ctrl+alt+f`.

It will always run Prettier on the current file even if the file is ignored in `.prettierignore`.

## Which Prettier it uses

`miniprettier` will follow this order to find the Prettier version to use:

- in the root dir of the current project
- a globally installed version of Prettier
- the bundled version in the plugin

## Prettier options

If `miniprettier` can't find Prettier in the current project, it will use options set in `config.cson`.

```coffeescript
  miniprettier:
    options:
      singleQuote: true
      printWidth: 100
      trailingComma: "all"
```

(see Prettier's [available options][prettieroptions])

Prettier will use the project's own configuration (via [`prettier.resolveConfig`](prettierResolveConfig)). If the project doesn't have any options set, it probably means the project uses Prettier's default and `miniprettier` will not pass any options.

`miniprettier` doesn't try to guess which `parser` to use or anything, it relies on Prettier's own inference based on the file extension.

## Credits

Thanks to @t9md for inspiration in [mprettier].

## License

[MIT](./License)

[mprettier]: https://github.com/t9md/atom-mprettier
[prettieroptions]: https://prettier.io/docs/en/options.html
[prettierresolveconfig]: https://prettier.io/docs/en/api.html#prettierresolveconfigfilepath-options
