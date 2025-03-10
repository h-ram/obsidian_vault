# Usage
```bash
$ python -m venv myenv # creates the myenv folder
```

```bash
source myenv/bin/activate
```

```
deactivate
```
# venv and ipynb on vs-code
```bash
$ python -m venv venv
$ source venv/bin/activate
(venv) $ pip install ipykernel
(venv) $ python -m ipykernel install --user --name=venv --display-name "Python (venv)"
```
- Restart Vs-code.
- Check if your virtual environment appears as a kernel.
# Installation
```
sudo pacman -S python-virtualenv
```