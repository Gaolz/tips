ruby global_variable
===============

#### 1 ```global_variables``` [出处](http://ruby-doc.org/core-2.3.1/Kernel.html#method-i-global_variables)
  > Returns an array of the names of global variables.

   返回一个数组，包含所有的全局变量名。

#### 2 ```self```
  > Execution context of the current method

#### 3 ```$:``` [出处](https://en.wikibooks.org/wiki/Ruby_Programming/Syntax/Variables_and_Constants#Pre-defined_Variables)
  > Load path for scripts and binary modules by load or require.

   是 Ruby 内建的执行环境变量，它返回一个数组，包含了 include 和 require 方法会去寻找的脚本和二进制文件的路径, 会数组的最后一个路径开始依次往前查找。

   alias: ```$LOAD_PATH```.

#### 4 ```$!```
  > The exception information message set by the last 'raise' (last exception thrown).
  
   最近一次的错误信息

   alias: ```$ERROR_INFO```

#### 5 ```$@```
  > Array of the backtrace of the last exception thrown.

   错误产生的位置

   alias: ```$ERROR_POSITION```

#### 6 ```$&```
  > The string matched by the last successful pattern match in this scope.

   最近一次与正则表达式匹配的字符串

   alias: ```$MATCH```

#### 7 $`
  > The string to the left of the last successful match.

   最近一次正则表达式匹配的字符串的左边一个字符串

   alias: ```$PREMATCH```

#### 8 ```$'```
  > The string to the right of the last successful match.

   最近一次正则表达式匹配的字符串的右边一个字符串

   alias: ```$POSTMATCH```

#### 9 ```$+```
  > The last group of the last successful match.

   最近一次匹配的组

   alias: ```$LAST_PAREN_MATCH```

#### 10 ```$1 to $9```
  > The Nth group of the last successful regexp match.

   第N组匹配

#### 11 ```$~```
  > The information about the last match in the current scope.

   最后的正则表达式匹配的内容，子表达式(subexpression)的组(阵列)

   alias: ```$LAST_MATCH_INFO```

#### 12 ```$=```
  > The flag for case insensitive, nil by default(deprecated).

   alias: ```$IGNORECASE```

#### 13 ```$/```
  > The input record separator, newline by default.

   输入记录分隔字符

   alias: ```$INPUT_RECORD_SEPARATOR``` or ```$RS``` or ```$-0```

#### 14 ```$\```
  > The output record separator for the print and IO#write. Default is nil.

   输出记录分隔字符

   alias: ```$OUTPUT_FIELD_SEPARATOR``` or ```$ORS```

#### 15 ```$,```
  > The output field separator for the print and Array#join.

   alias: ```$OUTPUT_FIELD_SEPARATOR``` or ```$OFS```

#### 16 ```$;```
  > The default separator for String#split

   alias: ```$FIELD_SEPARATOR```, ```$FS``` or ```$-F```

#### 17 ```$.```
  > The current input line number of the last file that was read.

   最后读取的行数

   alias: ```$INPUT_LINE_NUMBER``` or ```$NR```

#### 18 ```$<```
  > An object that provides access to the concatenation of the contents of all the files given as command-line arguments, or $stdin (in the case where there are no arguments). Read only.

   alias: ```$DEFAULT_INPUT```

#### 19 ```$FILENAME```
  > Current input file from $<. same as $<.filename

#### 20 ```$>```
  > The destination of output for Kernel.print and Kernel.printf. The default value is $stdout.

   alias: ```$DEFAULT_OUTPUT```

#### 21 ```$_```
  > The last input line of string by gets or readline.

   gets 读取的最后一行字符串

   alias: ```$LAST_READ_LINE```

#### 22 ```$0```
  > Contains the name of the script being executed. May be assignable.

   Ruby 脚本文件的名称

#### 23 ```$*```
  > Command line arguments given for the script. Also known as ```ARGV```.

   命令行参数

   alias: ```ARGV```

#### 24 ```$$```
  > The process number of the Ruby running this script.

   当前进程号

   alias: ```$PROCESS_ID```, ```$PID``` or ```Process.pid```

#### 25 ```$?```
  > The status of the last executed child process.

   离开最后执行的子进程状态

   alias: ```$CHILD_STATUS```

#### 26 ```$"```
  > The array contains the module names loaded by require.

   alias: ```$LOADED_FEATURES``` or ```$-I```

#### 27 ```$stderr```
  > The current standard error output.

#### 28 ```$stdin```
  > The current standard input.

#### 29 ```$stdout```
  > The current standard output.

#### 30 ```$-d```
  > The status of the -d switch. Assignable.

  alias: ```$DEBUG```

#### 31 ```$-K```
  > Character encoding of the source code.

   alias: ```$KCODE```

#### 32 ```$-v```
  > The verbose flag, which is set by the -v switch.

   alias: ```$VERBOSE```

#### 33 ```$-a```
  > True if option -a ("autosplit" mode) is set. Read-only variable.

#### 34 ```$-i```
  > If in-place-edit mode is set, this variable holds the extension, otherwise nil.

#### 35 ```$-l```
  > True if option -l is set ("line-ending processing" is on). Read-only variable.

#### 36 ```$-p```
  > True if option -p is set ("loop" mode is on). Read-only variable.

#### 37 ```$-w```
  > True if option -w is set.
