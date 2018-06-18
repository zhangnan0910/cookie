### 封装cookie

```
https://www.cnblogs.com/maderlzp/p/7843365.html

/**
* 设置cookie
    * @param name cookie的名称
    * @param value cookie的值
    * @param day cookie的过期时间
*/
```
注意：expires使用GMT或UTC格式的时间， 我这里没有指定路径(path)和域(domain)，  当没有指定路径时默认为当前路径下，如对 于“https://home.cnblogs.com/u/maderlzp/”下设置的cookie，其path为"/u/maderlzp"， 其domain为当前域名“home.cnblogs.com”。

为什么有时候删除不了cookie? 可能是因为删除cookie时没有指定该cookie的path和domain，导致找不到这个cookie来设置过期时间而无法删除。

```
/**
    * 获取对应名称的cookie
        * @param name cookie的名称
        * @returns {null} 不存在时，返回null
*/
```
cookie获取正则解析：
"(^| )" + name + "=([^;]*)(;|$)"  (^| )匹配cookie开头或空格（cookie键值对之间用分号空格隔开），也就是cookie键值对的开始。接着是cookie的名称name，（[^;]*）匹配除分号以外的任意字符，也就是cookie键值对的值。最后(;|$)匹配分号或整个cookie的结尾，也就是cooke键值对的结尾。

/**
    * 删除cookie
        * @param name cookie的名称
*/
```