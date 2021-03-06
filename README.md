# frame_pages

此项目是核心库 [frame](https://github.com/smarty-kiki/frame_pages) 的在线文档源码

如果需要本地编程，请确保本地安装了 `node` 和 `npm`，在本地执行如下命令安装 `docsify`

```shell
npm i docsify-cli -g
```

安装完成后，在项目根目录下执行以下命令即可在 [本地](http://localhost:3000) 预览和调试本文档

```shell
docsify serve docs
```


## 维护者原则

为了协作时大家遵循统一的表达形式，特此在这里列举文档中的一些描述格式：

### 标题级别

* 每个文档自身的名字及说明为一级标题 #
* 文档中内容的大分类为二级标题 ##，视情况而定，如果文档中不需要大分类，请直接跳过二级标题使用更低级别的标题以确保与其他文档层次一致
* 文档中具体的方法标题为三级标题 ###
* 文档中方法的参数、返回值、示例等内容块标题使用五级标题 #####

示例:   

#### 查询
----
```php
array db_query($sql_template, array $binds = [], $config_key = 'default')
```
##### 参数
- sql_template:  
    sql 模版

- binds:  
    数据绑定

- config_key:  
    数据库对应的配置 key  

##### 返回值
返回查询结果的数组

##### 示例
```php
$customer_infos = db_query('select * from customer where age = :age', [
    ':age' => 20,
]);
```

### 描述文字中的中英文数字

描述文字中会涉及到中文英文数字等不同内容的混写，按以下协作规范来写:  

* 中英文数字之间需有英文空格来分割
* 描述文字中涉及到的程序相关的词，如路径、文件名、类名、函数名、变量名等，需用代码块来包裹，代码段需与文字在不同的行，用带语言声明的代码块来包裹

示例：  

领域类一般放在 `domain/entity/` 目录中，内容如:  
```php
class order extends entity
{
    ...
}
```