# Tools and Tips

- `pip install -t . scikit-learn==0.22` - install specific version of module in current folder 
- `pip uninstall -y numpy` - uninstall module

- `export PATH="/opt/homebrew/bin:$PATH"` - way to `homebrew`

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
