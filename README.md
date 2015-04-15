# objc2swift

*objc2swift* is an open source project, aiming to create an automatic **Objective-C -> Swift** converter (or at least an useful helper for human).

The project contains an auto-generated Objective-C parser, generated by [ANTLR v4](http://www.antlr.org) with the grammer [ObjC.g4](https://github.com/antlr/grammars-v4/tree/master/objc).

## What it does
* converts `@interface Hoge` to `class Hoge {}`
* ... that's all for now!

## Setup

### 1. Install Scala
```
$ brew install scala
```

### 2. Install ANTLR v4

install:

```
$ cd /usr/local/lib
$ curl -O http://www.antlr.org/download/antlr-4.5-complete.jar
```

add classpath and aliases:

```
$ export CLASSPATH=".:/usr/local/lib/antlr-4.5-complete.jar:$CLASSPATH"
$ alias antlr4='java -Xmx500M -cp "/usr/local/lib/antlr-4.5-complete.jar:$CLASSPATH" org.antlr.v4.Tool'
$ alias grun='java org.antlr.v4.runtime.misc.TestRig'
```

for test, compile the ObjC parser and run the TestRig:

```
$ cd gen/
$ javac ObjC*.java
$ grun ObjC translation_unit ../sample/sample.h -gui
```

you should see something like this:

![ss1.png](doc/ss1.png)

See [Getting Started with ANTLR v4](https://theantlrguy.atlassian.net/wiki/display/ANTLR4/Getting+Started+with+ANTLR+v4) for more detail.


### 3. Import project and run!

Set `src/` for source directory, `gen/` for generated source directory. Pass `sample/sample.h` as the program argument, and run!

```
class A : NSObject {
}
```

Got this? Cool! You've successfully converted the sample Obj-C code to Swift!

```
@interface A : NSObject
@end
```

## LICENSE
This software is released under the MIT License, see [LICENSE.txt](LICENSE.txt).
