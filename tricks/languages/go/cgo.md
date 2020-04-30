# CGO

## Tips
* [类型转换](https://gist.github.com/zchee/b9c99695463d8902cd33)

## 初试

```bash
# 生成 libdemo.so libdemo.h
go build -buildmode=c-shared -o libdemo.so ./demo.go
# 编译 main
go build main.go
./main

# macos - 查看内容
nm libdemo.so | grep hello -i
# linux 
nm libdemo.so
# windows
dumpbin /EXPORTS libdemo.dll

# windows 交叉编译 - 需要安装 mingw
brew install mingw-w64

# 32 位 交叉编译
GOOS=windows GOARCH=386 CGO_ENABLED=1 CC=i686-w64-mingw32-gcc go build -buildmode=c-shared -o libdemo.dll ./demo.go
GOOS=windows GOARCH=386 CGO_ENABLED=1 CC=i686-w64-mingw32-gcc go build main.go

# macos wine 不支持 32 位 - mingw 版本低不支持 64 位
# mac 会出现异常 cc1: sorry, unimplemented: 64-bit mode not compiled in
# 通过 docker 编译
docker run --rm -v $HOME/go:/root/go -v $PWD:/host -w /host wener/go:mingw sh

GOOS=windows GOARCH=amd64 CGO_ENABLED=1 CC=x86_64-w64-mingw32-gcc go build -buildmode=c-shared -o libdemo.dll ./demo.go
GOOS=windows GOARCH=amd64 CGO_ENABLED=1 CC=x86_64-w64-mingw32-gcc go build main.go

# 回到 mac 使用 wine 执行
# wine 无法在 macos 上编译安装 - 系统版本问题 - 需要使用 cask 安装
brew cask install wine-stable
wine64 main.exe

# wine 4.0 初始化 dll 失败
# 0010:fixme:winsock:set_dont_fragment IP_DONTFRAGMENT for IPv4 not supported in this platform
# 0009:err:module:attach_dlls "libdemo.dll" failed to initialize, aborting
# 0009:err:module:attach_dlls Initializing dlls for L"Z:\\Users\\wener\\demo\\main.exe" failed, status c0000005
```

__demo.go__

```go
package main

import "C"

//export Version
func Version() int32 {
	return 123
}

//export Hello
func Hello(name *C.char) *C.char {
	return C.CString("Hello "+C.GoString(name)+"!")
}

func main() {}
```

__main.go__

```go
package main

import "fmt"

/*
#cgo CFLAGS: -I.
#cgo LDFLAGS: -L. -ldemo
#include "libdemo.h"
*/
import "C"

func main() {
	fmt.Printf("Int %v String %v\n",C.Version(), C.GoString(C.Hello(C.CString("Wener"))))
}
```
