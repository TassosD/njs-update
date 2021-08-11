# njs-update
A bash script to check and install the latest Node.js version. Last installed Node.js global modules are installed to the new version and npm module is also updated. `nvm` module is required for the script to work. Also at least one Node.js version must be installed via `nvm` before script usage.
&nbsp;  
&nbsp;  
&nbsp;  
## Usage
Before using script, script file has to be marked as executable with the following command (after going to the script folder):

```console
foo@bar:~$ chmode +x njs-update
```

Finally, it is recommended to add script folder to `$PATH` environmental variable.

To use the script you just type:

```console
foo@bar:~$ njs-update
```
&nbsp;  
&nbsp;  
## Description
On execution the script does the following:

* Get system current Node.js version and the latest remote one.
* If the system current version **is** the latest one, script just updates the `npm` version
* If the system current version **is older** than the latest one then:
	* If the latest remote version **is already installed** in the system then:
		* `npm` module (on the latest Node.js version) is updated to its last version
		* `.nvmrc` file is updated in current folder for user to switch to new Node.js version
	* If the latest remote version **is not installed** in the system then:
		* _Asks user if they want to install the latest remote version_
		* If user choose *Yes* then:
			* _Asks user if they want to uninstall the last installed version, after new version has been insatlled._
			* New version is installed
			* All global modules of the last installed version are installed to the new Node.js version
			* `npm` module (on the latest Node.js version) is updated to its last version
			* If user has chose to uninstall previous version, then this version is uninstalled from the system
			* `.nvmrc` file is updated in current folder for user to switch to new version
		* If user choose *No* then:
			* `npm` module (on the last installed Node.js version) is updated to its last version
			* `.nvmrc` file is updated in current folder for user to switch to last installed Node.js version

&nbsp;  
After script execution user can use the new Node.js version on the current session by typing:

```console
foo@bar:~$ nvm use
```

*Note: Script creates/updates a `.nvmrc` file in the current folder in order for the above `nvm` command to work.*