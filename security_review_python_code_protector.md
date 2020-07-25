## Python code protection via obfuscation or compilation

### Top tools tested and reviewed.

#### TL;DR The winner
Winner by a wide margin is [pyarmor](https://github.com/dashingsoft/pyarmor)

It is able to obfuscate large codebase with complex dependencies like packages scipy, gensim, cython, scikit-learn  

Runtime performance remains unaffected.

All project .py files contents unreadable:
```
__pyarmor__(__name__, __file__, b'\x50\x59\x41\x52\x4d\x4f\x52\x00\x00\........
```

##### Example usage with docker distribution
Build docker image with your source code been obfuscated during build.Assuming entry point to your microservice is the main.py

###### Dockerfile
```
COPY . /code/

# protect source code with pyarmor
RUN pip3 install pyarmor==5.6.6 \
    && pyarmor obfuscate /code/main.py \
    && rm -rf /code/ && mv dist /code

# cleanup unused files
RUN cd /code && rm -rf Dockerfile *.pyc *.pyo *.pye *.md
```

Don't forget to quash docker layers to remove "deleted" files in intermediate layers (unobfuscated python sources, dockerfiles, .py etc)
```bash
docker build --squash .
```


#### Other cryptors tested
* https://pypi.org/project/sourcedefender/
* https://github.com/ga0/pyprotect
* https://github.com/Falldog/pyconcrete
* https://github.com/liftoff/pyminifier
* https://github.com/BuvinJT/Opy


#### Weak obfuscators
* https://github.com/Hnfull/Intensio-Obfuscator - generates syntactically broken code
* https://github.com/PyObfx/PyObfx - slow, not able to handle large codebase
* https://github.com/astrand/pyobfuscate - python 2.x only
* https://github.com/brettcannon/mnfy - python 3.4 only


#### Compile to protect and gain 2-10x runtime speedup

* [pythran compiler](https://github.com/serge-sans-paille/pythran) - great tool, it gives you [parallelized and vectorized compiled code with minimal additional function type annotations](https://pythran.readthedocs.io/en/latest/MANUAL.html) in code 
* [Cythonize it with cython](https://cython.readthedocs.io/en/latest/src/tutorial/cython_tutorial.html) - requires code modifications
* [Nuitka compiler](https://github.com/Nuitka/Nuitka) - compiles python -> C++ looks very promising but compilation process is REAAALY SLOW on a large code base


### Because .pyc is not enough..
Python bytecode decompilers.

* https://github.com/rocky/python-uncompyle6 - successor of uncompyle2
* https://github.com/Mysterie/uncompyle2 - python 2.x only
* http://sourceforge.net/projects/decompyle/  - python 2.x only
* https://github.com/evanw/unwind - python 2.x 3.1


### REFERENCE
* https://www.defcon.org/images/defcon-18/dc-18-presentations/RSmith/DEFCON-18-RSmith-pyREtic.pdf
* https://www.usenix.org/system/files/conference/woot13/woot13-kholia.pdf
* https://stackoverflow.com/questions/5607283/how-can-i-manually-generate-a-pyc-file-from-a-py-file
* https://stackoverflow.com/questions/3344115/how-to-obfuscate-python-code-effectively
* http://bitboost.com/python-obfuscator/articles_and_resources/does_nuitka_remove_names_of_variables_functions_classes_etc/
* https://python-compiler.com/post/how-to-distribute-python-program
* https://bits.theorem.co/protecting-a-python-codebase/
* https://blog.easyaspy.org/post/16/2019-05-15-compiling-python-code-with-cython
* https://stackoverflow.com/questions/35735669/how-do-i-decompile-python-3-5-pyc
* http://code.activestate.com/recipes/576704/

