# QRCODE

方便生成指定字符串或网址的二维码，并且，你可以自定义size。

## 实例效果

![](https://api.mayuko.cn/images/v2/qrcode.png)

## 请求地址

https://api.mayuko.cn/v2/qrcode



## 请求方式

HTTPS	GET



## 请求参数



#### **系统级参数**

所有接入点需要的参数。

| 参数名称 | 类型     | 示例值                              | 必须   | 说明               |
| ---- | ------ | -------------------------------- | ---- | ---------------- |
| SK   | string | c7acff69c5a5acd08fcc4af108b592dd | 必须   | 每一个用户名对应唯一一个SK值。 |

#### **应用级参数**

每个接入点自己的参数。

| 参数名称    | 类型     | 示例值         | 必须   | 说明   |
| ------- | ------ | ----------- | ---- | ---- |
| content | string | Hello World | 必须   | 内容   |
| size    | int    | 8           | 必须   | 图片大小 |



## 返回参数

以JSON格式返回结果。

#### **系统级参数**

所有接入点需要的参数。

| 参数名称 | 类型     | 说明                 |
| ---- | ------ | ------------------ |
| code | string | 1：正常-1：SK错误-2：参数错误 |

#### **应用级参数**

每个接入点自己的参数。

| 参数名称 | 类型    | 说明    |
| ---- | ----- | ----- |
| 图片   | image | 二维码图片 |



## 请求实例

以 PHP 为例的请求实例。

```php
$sk = '';
$url = "https://api.mayuko.cn/v2/qrcode/?sk=sk&content=hello%20world&size=8";
echo get_file($url);
function get_file($url)
{
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, $url);
    curl_setopt($curl, CURLOPT_HEADER, 0);
    curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, FALSE);
    curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, FALSE);
    $data = curl_exec($curl);
    curl_close($curl);
    return $data;
}
                    
                
```

以 JAVA 为例的请求实例。

```java
public static void main(String path[]) throws Exception {
    URL u=new URL("https://api.mayuko.cn/v2/qrcode/?sk=sk&content=hello%20world&size=8");
    InputStream in=u.openStream();
    ByteArrayOutputStream out=new ByteArrayOutputStream();
    try {
        byte buf[]=new byte[1024];
        int read = 0;
        while ((read = in.read(buf)) > 0) {
            out.write(buf, 0, read);
        }
    } finally {
        if (in != null) {
            in.close();
        }
    }
    byte b[]=out.toByteArray( );
    System.out.println(new String(b,"utf-8"));
}
                    
                
```

以 Python 为例的请求实例。

```python
import urllib.parse
import urllib.request

data={}
data['sk']=''
data['参数']=''
url_values=urllib.parse.urlencode(data)
url = 'https://api.mayuko.cn/v2/qrcode/?sk=sk&content=hello%20world&size=8?'
full_url=url+url_values
data=urllib.request.urlopen(full_url).read()
z_data=data.decode('UTF-8')
print(z_data)
                    
                
```



## 返回实例

以IMG格式返回结果。

```
二维码图片
```