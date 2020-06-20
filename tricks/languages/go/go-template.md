---
id: go-template
title: Go 模板
---

# Go Template

## Tips
* [Masterminds/sprig](https://github.com/Masterminds/sprig) - 提供大量模板函数
* [hairyhenderson/gomplate](https://github.com/hairyhenderson/gomplate) - 支持数据源的命令行模板

## 语法

| Syntax                                                          | Description                                                          |
| --------------------------------------------------------------- | -------------------------------------------------------------------- |
| `{{"a" -}} b {{- "c"}}`                                         | 移除空白                                                             |
| `{{/* a comment */}}`                                           | 注释                                                                 |
| `{{pipeline}}`                                                  | 管道                                                                 |
| `{{if pipeline}} A {{else if pipeline}} B {{else}} C {{end}}`   | If-Then-Else                                                         |
| `{{range pipeline}} T1 {{else}} T0 {{end}}`                     | 遍历 array、slice、map、channel，当长度为 0 使用 else 部分           |
| `{{template "name" pipeline}}`                                  | 引入其他模板，可携带参数                                             |
| `{{define "name"}} T1 {{end}}`                                  | 定义模板用于 template 引入                                           |
| `{{block "name" pipeline}} T1 {{end}}`                          | 等于 define + template，用于实现默认，block 定义的模板可以被再次定义 |
| `{{with pipeline}} T1 {{else}} T0 {{end}}`                      | 设置 `.` 作用域，如果结果为空使用 else                               |
| `.`                                                             | 当前上下文                                                           |
| `$`                                                             | 当前模板 root 上下文                                                 |
| `{{ $v:= pipeline }}`                                           | 定义变量                                                             |
| `print (.F1 arg1) (.F2 arg2) (.StructValuedMethod "arg").Field` | 可以括号、对象可以通过 `.` 访问、可以直接调用函数                    |

## 内建函数
* 逻辑 and、or、not
* 比较 eq、ne、lt、le、gt、ge
* 输出 print、printf、println
* call
* html
* index - 索引访问 - map、slice、array
* slice - 切分第一个参数
  * `slice x 1 2` -> `x[1:2]`
* js - 返回转意后的 JS
* len - 返回长度
* urlquery - URL 编码
