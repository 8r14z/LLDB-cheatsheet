# LLDB cheatsheet

> `(lldb) help` to explore all available cmds

## Explore variables value and state
#### `(lldb) expression <expression>` = `(lldb) e <expression>`
To explore and modify variables's value in runtime.

```swift
let a = 10
let b = 20 // break point in this line
let sum = a + b
```
```
(lldb) e <variable> // to print value
(lldb) e a = 11 // now a will be "11" till the end of debugging session
```
> `(lldb) print <expression>` = `(lldb) p <expression>` = `(lldb) e -- <expression>` = `(lldb) e <expression>`

## Get overall app's state and language specific cmds
#### `(lldb) bugreport <expression>` = `(lldb) bu <expression>`
Generate a full report of current app's state. It could be helpful when encountering some problem and want to tackle it later.
```
(lldb) bu unwind --outfile <path>
```

#### `(lldb) frame <expression>` = `(lldb) fr <expression>`
Commands for selecting and examing the current thread's stack frames.
```
(lldb) frame info 
frame #0: 0x0000000106b0f3fe NewYourTimes`HomeViewController.viewDidLoad(self=0x00007fb477810df0) at HomeViewController.swift:42:9
```

#### `(lldb) language <expression>` = `(lldb) la <expression>`
`(lldb) language <language_type> <sub_command>` \
**language_type**: `cplusplus`, `objc`, `swift`, `renderscript`
```
(lldb) language swift refcount <object>
```

## Control app's excution flow
#### `(lldb) process <expression>` = `(lldb) pr <expression>`
To interact with processes on the current platform.
```
(lldb) process status // to explore where debugger is waiting
(lldb) process continue // equivalent to `continue` button in Xcode debugger toolbar
```

#### `(lldb) breakpoint <expression>` = `(lldb) br <expression>` = `(lldb) b <expression>`
To interact with breakpoints (see `(lldb) help b` for shorthand.)
> `(lldb breakpoint <flag> -f <file_name> -l <line_number>` 
```
(lldb) breakpoint list // list of breakpoints
(lldb) breakpoint clear/set -f ViewController.swift -l 10 // delete/set breakpoints
(lldb) breakpoint delete/disable/enable // use same as `clear`. If no breakpoints are specified, delete/disable/enable them all.
```

#### `(lldb) thread <expression>` = `(lldb) th <expression>`
Commands for operating on one or more threads in the current process.
```
(lldb) thread backtrack // show thread call stacks
(lldb) thread info 
(lldb) thread step-over
(lldb) thread step-in
(lldb) thread step-out
(lldb) thread continue
```



