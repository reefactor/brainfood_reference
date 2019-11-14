## Python code protection via obfuscation or compilation

### Top tools tested and reviewed.

#### Winner
Winner by a wide margin is https://github.com/dashingsoft/pyarmor


#### Other cryptors
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

