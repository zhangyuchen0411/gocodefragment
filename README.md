# gocodefragment
go代码片段

## coerce

摘抄自 <https://github.com/mreiferson/go-options/blob/master/options.go>

函数声明：`func Coerce(v interface{}, opt interface{}, arg string) (interface{}, error)`

功能：根据opt的类型转换v，例如如果opt的类型是int，那么就将v转换为int类型。当v时数值字符串(如"123")且opt是time.Duration类型时，arg被当做单位，如"1s","2m"，其他时候会被忽略。

## decorate

摘抄自 <https://github.com/nsqio/nsq/blob/master/internal/http_api/api_response.go#L155>

类型和函数：

```go
// 基础函数
type BasicFunc func()

// 装饰者，装饰传入的BasicFunc，返回新的BasicFunc
type Decorator func(BasicFunc) BasicFunc

// 装饰，用ds[0]装饰f, 然后用ds[1]装饰ds[0]...
// 这是在摆多米若骨牌，返回的函数执行时，就是骨牌被推倒时。
func Decorate(f BasicFunc, ds ...Decorator) BasicFunc
```

功能：装饰者模式。Decorator可以在BasicFunc执行前后做些额外的工作，比如记录日志等等。

## filelock

摘抄自 <https://github.com/nsqio/nsq/blob/master/internal/dirlock/dirlock.go#L22>

作用：当前程序会锁定特定文件或目录，其他程序再锁定相同文件或目录则失败。

##  split_text_to_words

摘抄自 <https://github.com/huichen/sego/blob/master/segmenter.go#L153>

作用：将text中的一串字母或数字当做一个Text，其他字当做一个Text输出

比如 `splitTextToWords(Text("中中 ab34c国家bcD12"))`, 分离结果就是：

```
中
中

ab34c
国
家
bcD12
```

