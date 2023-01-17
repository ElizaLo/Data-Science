<img src="https://raw.githubusercontent.com/ElizaLo/Data-Science/master/img/Tools_and_Tips.png" width="1050" height="150"/>

- Install specific version of module in current folder:

		pip install -t . scikit-learn==0.22
- Uninstall module:
		
		pip uninstall -y numpy

- Way to `homebrew`:

		export PATH="/opt/homebrew/bin:$PATH"
		
- [Cheat sheet](https://kapeli.com/cheat_sheets/screen.docset/Contents/Resources/Documents/index) for `Screen` commands
- 
		screen -r <session_id>
		
		screen -X -S [session # you want to kill] quit

## SSH 

- [PuTTY SSH client for Mac OSX - download and tutorial](https://www.ssh.com/academy/ssh/putty/mac)

		ssh -i privatekey.pem user@hostname 
- [Cyberduck - SFTP/FTP Client for Mac](https://www.ssh.com/academy/ssh/cyberduck)

### Connect to servers via Terminal:

1. Install PuTTY:
    - [PuTTY SSH client for Mac OSX](https://www.ssh.com/academy/ssh/putty/mac)
    - [How to Use PuTTY on Windows](https://www.ssh.com/academy/ssh/putty/windows)
2. Convert the `.ppk` format private key to a standard PEM format private key:

		puttygen privatekey.ppk -O private-openssh -o privatekey.pem
  
3. Logins from scripts and command line with:

        ssh -i privatekey.pem user@hostname



## FileZilla

- [FileZilla Forums](https://forum.filezilla-project.org)
- [Support](https://filezilla-project.org/support.php?version=3.53.1&product=#bugs)
- [Wiki](https://wiki.filezilla-project.org/Main_Page)


## Hosts

- [How To Quickly Edit Mac’s Hosts File](https://setapp.com/how-to/edit-mac-hosts-file)

## Libraries

### SQL 

| Title | Description |
| :---:         |          :--- |
|[SQLModel](https://github.com/tiangolo/sqlmodel)|<ul><p>SQLModel is a library for interacting with SQL databases from Python code, with Python objects. It is designed to be intuitive, easy to use, highly compatible, and robust.</p><p>**SQLModel** is based on Python type annotations, and powered by [Pydantic](https://pydantic-docs.helpmanual.io/) and [SQLAlchemy](https://sqlalchemy.org/).</p></ul> |

### Machine Learning 

| Title | Description |
| :---:         |          :--- |
|[Machine Learning Things](https://github.com/gmihaila/ml_things#plot_array-source)|Machine Learning Things is a lightweight python library that contains functions and code snippets that I use in my everyday research with Machine Learning, Deep Learning, NLP.|
|[Ivy](https://github.com/unifyai/ivy)|Ivy is a unified machine learning framework which maximizes the portability of machine learning codebases. Ivy wraps the functional APIs of existing frameworks. Framework-agnostic functions, libraries and layers can then be written using Ivy, with simultaneous support for all frameworks. Ivy currently supports Jax, TensorFlow, PyTorch, MXNet and Numpy. |


## Tools

| Title | Description |
| :---:         |          :--- |
|[PostHog](https://github.com/PostHog/posthog)|Open-source product analytics suite, built for engineers|

### JSON 

| Title | Description |
| :---:         |          :--- |
|[JWT.IO](https://jwt.io/)|JSON Web Tokens are an open, industry standard RFC 7519 method for representing claims securely between two parties. JWT.IO allows you to decode, verify and generate JWT.|
