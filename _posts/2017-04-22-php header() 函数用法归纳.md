---
layout: post
title: PHP 函数 header() 的用法归纳
date: 2017-04-22 22:26 +0800
tags: [PHP, 函数, 编程语言, 技术]
---

+ 301 永久重定向 
```php
    <?php
    header('HTTP/1.1 301 Moved Permanently');
    header('Location: http://www.example.com');
    exit();
    ?>
```    

+ 302 临时重定向
```php
    <?php
    header('Location: http://www.example.com');
    exit();
    ?>
```

+ 404 页面未找到
```php
    <?php
    header('HTTP/1.1 404 Not Found');
    ?>
```

+ 503 服务不可用
```php
    <?php
    header('HTTP/1.1 503 Service Temporarily Unavailable');
    header('Status: 503 Service Temporarily Unavailable');
    exit();
    ?>
```


+ 设置内容类型
```php
    <?php
    // html 
    header('Content-Type: text/html; charset=iso-8859-1');
    header('Content-Type: text/html; charset=utf-8');

    // plain text 
    header('Content-Type: text/plain'); //纯文本格式

    // css header
    header('Content-Type: text/css'); 
    
    // javascript header 
    header('Content-Type: application/javascript');

    // images header
    header('Content-Type: image/jpeg'); //JPG图片
    header('Content-Type: images/png');
    header('Content-Type: images/bmp');

    // 所有图片类型
    header('Content-Type: images/*'); 

    // zip 文件
    header('Content-Type: application/zip'); // ZIP文件

    // PDF 文件
    header('Content-Type: application/pdf'); // PDF文件

    // 音频文件
    header('Content-Type: audio/mpeg'); // 音频文件

    // flash 动画
    header('Content-Type: application/x-shockwave-flash'); //Flash动画
    ?>
```

+ 缓存（cache）(force browsers not to cache files)
```php
    <?php
    header('Expires: Sat, 26 Jul 1997 05:00:00 GMT');
    header('Cache-Control: not-store, no-cache, must-revalidate');
    header('Cache-Control: pre-check=0, post-check=0, max-age=0');
    header('Pragma: no-cache'); // For IE Browsers
    ?>
```

+ 文件下载 
```php
    <?php
    header('Content-Disposition: attachment;filename=' . urlencode($f));
    header('Content-Type: application/force-download');
    header('Content-Type: application/octet-stream');
    header('Content-Type: application/download');
    header('Content-Description: File Transfer');
    header('Content-Length: '. filesize($f)');
    echo file_get_contents($f);
    ?>
```

+ 权限认证 （force the browsers to pop up a Username/Password input window) - only available when PHP is runnig as an Apache module: 
```php
    <?php
    if (!isset($_SERVER['PHP_AUTH_USER'])) {
        header('WWW-Authenticate: Basic realm="The Realm"');
        header('HTTP/1.0 401 Unauthorized');
        echo 'If cancel is pressed this text shows';
        exit();
    } else {
        $user='user';
        $pass='pass';
        if($_SERVER['PHP_AUTH_USER']==$user && $_SERVER['PHP_AUTH_PW']==$pass){
            echo 'Authorized';
        }
    }
```

> HTTP response codes 的具体解释可以去 Mozilla 的 [MDN 文档](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status)查阅。
