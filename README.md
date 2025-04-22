<img src="images/logo.png" width="200"/>

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE) [![Documentation Status](https://readthedocs.org/projects/asvin-rbc/badge/?version=latest)](https://asvin-rbc.readthedocs.io/en/latest/?badge=latest)

- [asvin](#asvin)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

# asvin Risk By Context™

asvin facilitates Risk By Context™ solution to manage the cybersecurity risks present in an OT environment.

# Documentation

If you want the world to read asvin documentation in your own language, you are welcome to translate it. The documentation is already available in German and English. Therefore, you can contribute in the existing translations or add a new language if it doesn't exist.

asvin uses [Read the Docs](https://readthedocs.org/) for software documentation. It facilitates automatic building, versioning, and hosting of the documentation. The [Sphinx](https://www.sphinx-doc.org/en/master/) tool is used to build the documentation using the [theme](https://github.com/readthedocs/sphinx_rtd_theme).
The documentation is generated for each commit in the master branch. Therefore, it is advised to build locally for update, preview and design. The [section](#update-documentation) describe the procedure. You could find the latest version of [documentation](https://asvin-rbc.readthedocs.io/en/latest/index.html) online.

## Update Documentation

### Setup

1. Download and install latest version of Python from [here](https://www.python.org/downloads/)
2. Clone the repo
   ```
   git clone https://github.com/asvin-io/asvin-rbc-docs.git
   ```
3. create virtual environment

   ```
   cd documentation/docs/en
   python3 -m venv .venv
   ```

4. activate virtual environment and install dependencies

   ```
   source .venv/bin/activate
   pip3 install -r requirements.txt
   ```

   📝 **Note:** Make sure to activate the virtual environment before installing dependencies.

### Build

Make your changes and run following commands to generate html documentation.

```
cd asvin-docs/docs/locale/en
source .venv/bin/activate
make html
```

### Preview

Open `./build/html/index.html` file in a browser.

### Upload

When all the changes are according to your needs then push changes or make a pull request.

Please find further information about the architecture, getting started and tutorials in our online documentation.

- [latest](https://asvin-rbc.readthedocs.io/en/latest/index.html)

Find out more about us

- [website](https://asvin.io)

# Contributing

We welcome your [contribution](https://asvin-rbc.readthedocs.io/en/latest/contribution/contribution.html) to the Risk By Context™.

# License

The information here is made available under the Apache License, Version 2.0 (Apache-2.0), located in the [LICENSE](LICENSE) file.
