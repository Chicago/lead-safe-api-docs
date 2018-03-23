[![Build status](https://img.shields.io/travis/Chicago/lead-safe-api-docs/master.svg?style=flat-square&maxAge=2592000)](https://travis-ci.org/Chicago/lead-safe-api-docs)[![Version](https://img.shields.io/github/release/Chicago/lead-safe-api-docs.svg?maxAge=2592000&style=flat-square)](https://github.com/Chicago/lead-safe-api-docs/releases)

# "Lead Safe" API Documentation

## Building and Testing

The documentation is compiled with [MkDocs](http://www.mkdocs.org/) and is required while testing.

### Local Testing

Test changes to the documentation by opening a terminal and run

```
mkdocs serve
```

Visit `localhost:8000` in a browser to inspect the documentation.

Once changes are acceptable, build the documentation by returning to the terminal and run

```
mkdocs build
```

Commit and push changes to the server.

## License

Copyright &copy; 2017 City of Chicago. Documentation is licensed under [Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/).

## Configuration

### Emailing Forms

The application process uses [Formspree.io](http://formspree.io). Currently using the free service, which limits to 1,000 submissions per month. This can be modified in the `<forms>` element in `docs/apply.md`

### List of Eligible Health Networks

The list of eligible health networks is in `docs/apply.md`. Each institution is listed as an `<option>`