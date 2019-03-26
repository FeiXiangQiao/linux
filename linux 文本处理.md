&ensp;&ensp;&ensp;&ensp; 版权声明：本文为博主原创文章，转载请注明本文链接。文章内容如有错误望能指正，以免误导更多人。 https://blog.csdn.net/feixiangqiao/article/details/88667990
## 1、grep用法  
### 特殊字符串配置  
原始数据  
```bash
[root@python-test1 ~]# cat 1.txt   
1932840184019
aasdsfsdgfg
SADAFASFASFAS
  aaa
		dfsfds
asdasd2e21321
13112134SASDAsdfsf
,,bbb./.,/aaaaa
.././.111..dsf
./,.,.2222.][['
DDDdsfsfs...111
```
* [:alnum:] 字母和数字   
```bash
[root@python-test1 ~]# grep -E "[[:alnum:]]" 1.txt
```
![alnum](https://img-blog.csdnimg.cn/20190319192952273.jpg)
* [:alpha:] 代表任何英文大小写字符，亦即 A-Z, a-z   
```bash
[root@python-test1 ~]# grep -E "[[:alpha:]]" 1.txt
```
![alpha](https://img-blog.csdnimg.cn/20190319193015584.jpg)
* [:lower:] 小写字母    
```bash
[root@python-test1 ~]# grep -E "[[:lower:]]" 1.txt
```
![lower](https://img-blog.csdnimg.cn/20190319193032441.jpg)
* [:upper:] 大写字母   
```bash
[root@python-test1 ~]# grep -E "[[:upper:]]" 1.txt
```
![upper](https://img-blog.csdnimg.cn/20190319193047724.jpg)
* [:blank:] 空白字符（空格和制表符）   
```bash
[root@python-test1 ~]# grep -E "[[:blank:]]" 1.txt
```
![blank](https://img-blog.csdnimg.cn/20190319193104842.jpg)
>注意：在aaa字段前面的是空格，在dfsfds字段前面是制表符（tab键）   
* [:space:] 水平和垂直的空白字符（比[:blank:]包含的范围广）   
```bash
[root@python-test1 ~]# grep -E "[[:space:]]" 1.txt
```
![space](https://img-blog.csdnimg.cn/20190319193117789.jpg)
>注意：在aaa字段前面的是空格，在dfsfds字段前面是制表符（tab键）   
* [:cntrl:] 不可打印的控制字符（退格、删除、警铃...）   
```bash
[root@python-test1 ~]# grep -E "[[:cntrl:]]" 1.txt
```
![cntrl](https://img-blog.csdnimg.cn/20190319193134736.jpg)
>在dfsfds字段前面是制表符（tab键)  
* [:digit:] 十进制数字    
```bash
[root@python-test1 ~]# grep -E "[[:digit:]]" 1.txt
```
![digit](https://img-blog.csdnimg.cn/20190319193150364.jpg)
* [:xdigit:]十六进制数字   
```bash
[root@python-test1 ~]# grep -E "[[:xdigit:]]" 1.txt
```
![xdigit](https://img-blog.csdnimg.cn/20190319193202400.jpg)
* [:graph:] 可打印的非空白字符   
```bash
[root@python-test1 ~]# grep -E "[[:graph:]]" 1.txt
```
![graph](https://img-blog.csdnimg.cn/20190319193218814.jpg)
* [:print:] 可打印字符   
```bash
[root@python-test1 ~]# grep -E "[[:print:]]" 1.txt
```
![print](https://img-blog.csdnimg.cn/20190319193232379.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXhpYW5ncWlhbw==,size_16,color_FFFFFF,t_70)
* [:punct:] 标点符号   
```bash
[root@python-test1 ~]# grep -E "[[:punct:]]" 1.txt
```
![punct](https://img-blog.csdnimg.cn/20190319193247662.jpg)

## 2、定制vim的工作特性  
### 配置文件：永久有效  
* 全局：/etc/vimrc  
* 个人：~/.vimrc  

### 扩展模式：当前vim进程有效  
1. 行号  
&ensp;&ensp;&ensp;&ensp;显示：set number, 简写为set nu  
&ensp;&ensp;&ensp;&ensp;取消显示：set nonumber, 简写为set nonu  
2. 忽略字符的大小写  
&ensp;&ensp;&ensp;&ensp;启用：set ic  
&ensp;&ensp;&ensp;&ensp;不忽略：set noic  
3. 自动缩进  
&ensp;&ensp;&ensp;&ensp;启用：set ai  
&ensp;&ensp;&ensp;&ensp;禁用：set noai  
4. 复制保留格式  
&ensp;&ensp;&ensp;&ensp;启用: set paste  
&ensp;&ensp;&ensp;&ensp;禁用: set nopaste  
5. 高亮搜索  
&ensp;&ensp;&ensp;&ensp;启用：set hlsearch  
&ensp;&ensp;&ensp;&ensp;禁用：set nohlsearch  
6. 语法高亮  
&ensp;&ensp;&ensp;&ensp;启用：syntax on  
&ensp;&ensp;&ensp;&ensp;禁用：syntax off  
7. 显示Tab和换行符 ^I 和$显示  
&ensp;&ensp;&ensp;&ensp;启用：set list  
&ensp;&ensp;&ensp;&ensp;禁用：set nolist  
8. 文件格式  
&ensp;&ensp;&ensp;&ensp;启用windows格式：set fileformat=dos  
&ensp;&ensp;&ensp;&ensp;启用unix格式：set fileformat=unix  
&ensp;&ensp;&ensp;&ensp;简写： set ff=dos|unix  
10. 设置文本宽度  
&ensp;&ensp;&ensp;&ensp;启用: set textwidth=65 (vim only)  
&ensp;&ensp;&ensp;&ensp;禁用: set wrapmargin=15  
11. 设置光标所在行的标识线  
&ensp;&ensp;&ensp;&ensp;启用:set cursorline，简写cul  
&ensp;&ensp;&ensp;&ensp;禁用:set no cursorline  
## 3、sed命令详解  
用法：
 
`sed [option]... 'script' inputfile...  `

常用选项：  
&ensp;&ensp;&ensp;&ensp;-n：不输出模式空间内容到屏幕，即不自动打印  
&ensp;&ensp;&ensp;&ensp;-e: 多点编辑  
&ensp;&ensp;&ensp;&ensp;-f：/PATH/SCRIPT_FILE: 从指定文件中读取编辑脚本  
&ensp;&ensp;&ensp;&ensp;-r: 支持使用扩展正则表达式  
&ensp;&ensp;&ensp;&ensp;-i.bak: 备份文件并原处编辑  
  
script:   
&ensp;&ensp;&ensp;&ensp;'地址命令'  
地址定界：  
1. 不给地址：对全文进行处理  
2. 单地址：  
&ensp;&ensp;&ensp;&ensp;#: 指定的行，$：最后一行  
&ensp;&ensp;&ensp;&ensp;/pattern/：被此处模式所能够匹配到的每一行  
3. 地址范围：  
&ensp;&ensp;&ensp;&ensp;#,#  
&ensp;&ensp;&ensp;&ensp;#,+#  
&ensp;&ensp;&ensp;&ensp;/pat1/,/pat2/  
&ensp;&ensp;&ensp;&ensp;#,/pat1/  
4. ~：步进  
&ensp;&ensp;&ensp;&ensp;1~2 奇数行  
&ensp;&ensp;&ensp;&ensp;2~2 偶数行  
5. 编辑命令：  
&ensp;&ensp;&ensp;&ensp;d: 删除模式空间匹配的行，并立即启用下一轮循环  
&ensp;&ensp;&ensp;&ensp;p：打印当前模式空间内容，追加到默认输出之后  
&ensp;&ensp;&ensp;&ensp;a [\]text：在指定行后面追加文本  
6. 支持使用\n实现多行追加  
&ensp;&ensp;&ensp;&ensp;i [\]text：在行前面插入文本  
&ensp;&ensp;&ensp;&ensp;c [\]text：替换行为单行或多行文本  
&ensp;&ensp;&ensp;&ensp;w /path/somefile: 保存模式匹配的行至指定文件  
&ensp;&ensp;&ensp;&ensp;r /path/somefile：读取指定文件的文本至模式空间中  
7. 匹配到的行后  
&ensp;&ensp;&ensp;&ensp;=: 为模式空间中的行打印行号  
&ensp;&ensp;&ensp;&ensp;!:模式空间中匹配行取反处理  
&ensp;&ensp;&ensp;&ensp;s///：查找替换,支持使用其它分隔符，s@@@，s###  
8. 替换标记：  
&ensp;&ensp;&ensp;&ensp;g: 行内全局替换  
&ensp;&ensp;&ensp;&ensp;p: 显示替换成功的行  
&ensp;&ensp;&ensp;&ensp;w /PATH/TO/SOMEFILE：将替换成功的行保存至文件中  
  
### sed示例  
```bash
sed ‘2p’ /etc/passwd  
sed –n ‘2p’ /etc/passwd  
sed –n ‘1,4p’ /etc/passwd  
sed –n ‘/root/p’ /etc/passwd  
sed –n ‘2,/root/p’ /etc/passwd 从2行开始   
sed -n ‘/^$/=’ file 显示空行行号   
sed –n –e ‘/^$/p’ –e ‘/^$/=’ file  
sed ‘/root/a\superman’ /etc/passwd行后   
sed ‘/root/i\superman’ /etc/passwd 行前   
sed ‘/root/c\superman’ /etc/passwd 代替行   
sed ‘/^$/d’ file  
sed ‘1,10d’ file  
nl /etc/passwd | sed ‘2,5d’  
nl /etc/passwd | sed ‘2a tea’  
sed 's/test/mytest/g' example  
sed –n ‘s/root/&superman/p’ /etc/passwd 单词后   
sed –n ‘s/root/superman&/p’ /etc/passwd 单词前   
sed -e ‘s/dog/cat/’ -e ‘s/hi/lo/’ pets   
sed –i.bak ‘s/dog/cat/g’ pets 
```

