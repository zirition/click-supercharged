[![Tests](https://github.com/zirition/click-supercharged/workflows/Python%20package/badge.svg)](https://github.com/zirition/click-supercharged/actions?query=workflow%3APython%20package)

# Click Supercharged

## Overview

`click-supercharged` is a Python package that enhances the `Click` command line interface framework by providing support for default commands and command aliases. This project allows developers to organize their command-line interfaces in a more flexible and user-friendly manner.

## Features

- **Default Command**: Specify a default command that executes when no command is provided.
- **Command Aliases**: Create multiple aliases for commands to improve usability and avoid lengthy command names.
- **Abbreviations**: Use abbreviations instead the full command. Handles ambiguous command inputs gracefully and informs the user about multiple matches.

## Installation

You can install `click-supercharged` via PyPI:

```bash
pip install click-supercharged
```

## Usage

To use the `SuperchargedClickGroup`, you can set it as the command group in your Click application as shown below:

```python
import click
from click_supercharged import SuperchargedClickGroup

@click.group(cls=SuperchargedClickGroup)
def cli():
    pass

@cli.command(default_command=True, aliases=["bar"])
def foo():
    click.echo("foo")

@cli.command(aliases=["bax", "bez", "buz"])
def baz():
    click.echo("baz")

if __name__ == "__main__":
    cli()
```

### Running your CLI

When you run the script, you can execute:

- `python your_script.py` to invoke the default command `foo`.
- `python your_script.py f` to invoke the command `foo` using its abbreviation.
- `python your_script.py ba` to see error handling for ambiguous commands.

## Testing

The project includes unit tests to ensure functionality. You can run the tests using the following command:

```bash
python -m unittest discover
```

## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss improvements or features.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Click](https://click.palletsprojects.com/) - The command-line interface framework that this project builds upon.