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
```
/**
* 删除cookie
    * @param name cookie的名称
*/
```
设置要删除的cookie的expires为过去的时间即可

### 修改cookie：
```
重新给cookie赋值就行，这样旧的就会被覆盖掉
```
 

 

cookie的主要作用：


### Cookie主要用在以下三个方面:
```
1. 会话状态管理（如用户登录状态、购物车、游戏分数和其它需要记录的信息）
2. 个性化设置（如用户自定义设置、主题等）
3. 浏览器行为跟踪（如跟踪分析用户行为）
```

 

### cookie设置语法：

 
```
document.cookie = "cookieName=mader; expires=Fri, 31 Dec 2017 15:59:59 GMT; path=/mydir; domain=cnblogs.com; max-age=3600; secure=true";

    1. cookieName=mader ：name=value，cookie的名称和值
    2. expires=Fri, 31 Dec 2017 15:59:59 GMT： expires，cookie过期的日期，如果没有定义，cookie会在对话结束时过期。日期格式为 new Date().toUTCString()
    3. path=/mydir: path=path (例如 '/', '/mydir') 如果没有定义，默认为当前文档位置的路径。
    4. domain=cnblogs.com： 指定域(例如 'example.com'， '.example.com' (包括所有子域名), 'subdomain.example.com') 如果没有定义，默认为当前文档位置的路径的域名部分。
    5. max-age=3600： 文档被查看后cookie过期时间，单位为秒
    6. secure=true： cookie只会被https传输 ，即加密的https链接传输
```