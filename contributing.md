# bzr
```Bash
# pull changes from configured source
bzr pull

# push changes to configured destination
bzr push

# To link a branch to a bug report you should use 
bzr commit --fixes=lp:$BUGNUM
```

# Software center
```Bash
bzr branch lp:software-center
cd software-center
python setup.py build
PYTHONPATH=. ./bin/software-center
```
