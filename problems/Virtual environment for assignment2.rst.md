# Quesion1
## 1) operation
    run pip3 install -r requirements.txt
## 2) output
    Building wheels for collected packages: nltk
    Running setup.py bdist_wheel for nltk ... error
    Complete output from command /home/yoyo/cs231/cs231_environments/assignment2/.env/bin/python3 -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-5w26dsib/nltk/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" bdist_wheel -d /tmp/tmpzltncs5ypip-wheel- --python-tag cp35:
    usage: -c [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd2_opts] ...]
     or: -c --help [cmd1 cmd2 ...]
     or: -c --help-commands
     or: -c cmd --help
  
    error: invalid command 'bdist_wheel'
  
    ----------------------------------------
    Failed building wheel for nltk
    Running setup.py clean for nltk
    Failed to build nltk
    ...
    Running setup.py install for nltk ... done
  ...
## 3) reason
not know
## 4) solution
rerun pip3
it seems that all packages are installed.

# Q2
    /home/yoyo/cs231/cs231_environments/assignment2/.env/bin/python: No module named ipykernel_launcher
 
    jupyter notebook -> change kernel 
 
    solved
