# Python Version
```
python --version
```
# Virtual Environment
Stand alone Interpreter, no more pollution in your setup
* [[Virtual Environment.canvas|Virtual Environment]] Note
```
cd ~
mkdir pyworkshop
cd pyworkshop
python3 -m venv env
# -m means: run the next command as a module 
source env/bin/actiavte
```
# VS Code Most Important Shortcuts
`command(Ctrl)+shift+p` open command palate
`command(Ctrl)+p` open Fast File Finder (FFF) 
`command+(back-tick)` open terminal
## Extension
Linter + Pylance (LSP) + Python
# requirement.txt
Store and install your environment from this file
* Store:
	* pip
	  `pip freeze > requirement.txt`
	* conda:
	  `conda list --export`
	* conda yml:
	  `conda env export > environment.yml`
* Create:
	* pip:
	  `pip install -r requirement.txt`
	* conda:
	  `conda create --name <env_name> --file requirements.txt`
	* conda yml:
	  `conda env create -f environment.yml`