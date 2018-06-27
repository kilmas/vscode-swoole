Simple debuger php-src/swoole-src or c/c++ (if you like) to gdb on vscode(window)

# Launch Debugging to docker on vscode(window)

Most debuggers are not going to support this gracefully, so the simplest thing to do is to
start the docker yourself, and compile the binary, and then launch via `docker exec`

# first
 you can build a docker images with Compiling chain(php,gcc,g++,gdb...)
 for example:
```
docker build -t kilmas/distribute .

```

```
pwd 
$ /c/Users/kilmas/Desktop/git
docker run -d --rm --privileged -v `pwd`:/app --net=host --name distribute kilmas/distribute tail -f /dev/null

git clone https://github.com/php/php-src.git
git clone https://github.com/kilmas/vscode-swoole.git

git clone https://github.com/swoole/swoole-src.git .
cd swoole-src
(re-compile src in docker Container)
cp -r ../vscode-swoole/.vscode .

```

# press F5

debugger Parent Process:
C++ Launch in already running docker container

or

debugger Manager/Master/Worker/Task/other Process:
C++ Launch in already running docker container

(fill Process pid)

# notice

sourceFileMap : Optional source file mappings passed to the debug engine. Example: '{ "/original/source/path":"/current/source/path" }'
files should be download

```
git clone git://sourceware.org/git/glibc.git glibc-2.23
cd glibc-2.23
git checkout -f glibc-2.23.90

"sourceFileMap": {
    "/app/swoole-src": "${workspaceRoot}",
    "/app/php-7.1.16": "C:/Users/kilmas/Desktop/git/php-src",
    "/build/glibc-Cl5G7W/glibc-2.23" : "C:/Users/kilmas/Desktop/git/glibc-2.23",
    "/usr/include" : "C:/Users/kilmas/Desktop/git/include",
    "/usr/lib/x86_64-linux-gnu" : "C:/Users/kilmas/Desktop/git/x86_64-linux-gnu",
},
```

C++ Attach in docker container

Launch with your *favorite* debugger.

