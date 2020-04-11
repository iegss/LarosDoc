# 1、接口签名

## 1. 参数排序拼装

根据参数名称（除sign本身以外）将所有请求参数按照参数从小到大先后顺序排序：key1+value1...key2+value2  
例如提交参数如下：  
`machine_no=B0001&method=api.machine.add&pro_no=ffff&pro_code=12312&timestamp=2015-05-18 16:05:40&sign=88d40ba6312eb845b9bde418c0cff9df`

参数名和参数值链接后，得到拼装字符串

```text
machine_noB0001methodapi.machine.addpro_code12312pro_nofffftimestamp2015-05-18 16:05:40
```

## 2. salt 拼接到参数字符串头尾

如: salt=047298b5915b85c25f3030dbdf23b27c，拼接后的字符串为  
`047298b5915b85c25f3030dbdf23b27cmachine_noB0001methodapi.machine.addpro_code12312pro_nofffftimestamp2015-05-18 16:05:40047298b5915b85c25f3030dbdf23b27c`

注：salt 为服务端提供

## 3. MD5签名

对整个字符串做md5再转化16进制小写表达方式，即为sign的内容，如上面字符串得到的sign为：88d40ba6312eb845b9bde418c0cff9df

## 4. 验证方式

如果sign的内容相符则认为是合法的调用，否则作为非法调用处理，返回错误信息。

