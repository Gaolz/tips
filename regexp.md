Ruby regexp tips
================

##### 1 ```/\p{Han}/u```
  > 匹配汉字

##### 2 ```/\p{Word}+/u```
  > 匹配不限于 a-z0-9 的成词字符(就是非标点制表符空格等杂类的字符)

##### 3 ```/\p{Hiragana,Katakana}+/u```
  > 匹配平假名＋片假名

##### 4 ```/regexp expression/u```
  > u: 让这个正则的编码是 utf-8.
  ```
    /a/.encoding   # US-ASCII
    /a/u.encoding # UTF-8
  ```
