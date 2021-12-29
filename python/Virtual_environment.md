
```
python -m venv venv_name

.\venv_name\Scripts\activate

python -m ipykernel install --name=venv_name    # VS Code will do this for you if you haven't already

jupyter kernelspec list                         # verify it is there

jupyter kernelspec uninstall venv_name          # if need to uninstall

deactivate



```