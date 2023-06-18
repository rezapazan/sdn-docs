## Installing _Ryu_ on _Ubuntu 20.4.1 LTS_

!! _you need to install python 3.8_ !!

```shell
$ wget https://bootstrap.pypa.io/get-pip.py
$ apt install python3.8-distutils
$ python3.8 get-pip.py
$ python3.8 -m pip install ryu
$ apt install gcc python-dev libffi-dev libssl-dev libxml2-dev libxslt1-dev zlib1g-dev python3.8-dev
$ python3.8 -m pip uninstall eventlet
$ python3.8 -m pip install eventlet==0.30.2 //this version is compatible
```

---

## Installing _Ryu_ on _Windows_

!! _you need to install python 3.8
then go to the python directory where you installed it
then open up a CMD as administrator
then run the following commands_ !!

!! _You can also add `python.exe` to your `$Path` system variable_ !!

```shell
$ py get-pip.py
$ py -m pip install ryu
$ py -m pip uninstall eventlet
$ py -m pip install eventlet==0.30.2
$ py -m pip install packaging
```

-   In order to connect Mininet topology to Ryu controller, use the command below:

```shell
$ mn --controller=remote,ip=xxx.xxx.xxx.xxx,port=6633
```
