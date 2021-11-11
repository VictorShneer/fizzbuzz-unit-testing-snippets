# Unit tests snippets

tips, commands, links

## sources 

[Miguel's blog] (https://blog.miguelgrinberg.com/post/how-to-write-unit-tests-in-python-part-1-fizz-buzz)

## coverage 

```bash
pip install pytest-cov
```

```bash
pytest --cov=fizzbuzz --cov-report=term-missing --cov-branch
```

Note that when running tests with code coverage it is useful to always limit coverage to the application module or package, which is passed as an argument to the --cov option as seen above. If the scope is not restricted, then code coverage will apply to the entire Python process, which will include functions from the Python standard library and third-party dependencies, resulting in a very noisy report at the end.

The pytest-cov plugin can generate the final report in several formats. The one you've seen above is the most basic one, called term because it is printed to the terminal. A variant of this report is called term-missing, which adds the lines of code that were not covered.

The code coverage analysis can also be configured to treat lines with conditionals as needing double coverage to account for the two possible outcomes. This is called branch coverage and is enabled with the --cov-branch option.

For cases where you as a developer make a conscious decision that a piece of code does not need to be tested, it is possible to mark these lines as an exception, and with that they will be counted as covered and will not appear in coverage reports as missing. This is done by adding a comment with the text pragma: no cover to the line or lines in question. When an exception is added in a line that begins a control structure, it is applied to the whole code block.

