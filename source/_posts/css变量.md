### css 定义变量
* 定义变量，变量可以放在：root中，且变量前面要加入--前缀
```
:root{
--变量名:变量值
}
```
* examples
```
:root{
--fontColor:red;
}
```
#### 使用变量的规则
```
:root{
fontColor:red;
}
body{
background:var(--fontColor)
}
