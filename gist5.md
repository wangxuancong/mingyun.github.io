###php导出excel
```php
header("Content-type:text/csv");   
header("Content-Disposition:attachment;filename=".$filename);   
header('Cache-Control:must-revalidate,post-check=0,pre-check=0');   
header('Expires:0');   
header('Pragma:public');
$str='第一行,第二行';
$str =  iconv('utf-8','GBK//IGNORE',$str);
echo $str;
ob_flush();
flush();
sleep(1); 
```
###[利用pytesser模块识别图像文字](http://www.cnblogs.com/chenbjin/p/4147564.html)
```php
from pytesser import *
im = Image.open('fonts_test.png')
text = image_to_string(im)
print "Using image_to_string(): "
print text
text = image_file_to_string('fonts_test.png', graceful_errors=True)
print "Using image_file_to_string():"
print text
```
###[pdf转中文](https://www.zhihu.com/question/47480852/answer/121215315)
```php
 
# python3 安装使用pip install pdfminer3k
import os import subprocess from os.path import isfile,join ef = 'D:/xpdf/pdftotext.exe' cfg = 'D:/xpdf/xpdfrc' file = 'D:/xpdf/1.pdf' def convert(file): bo = subprocess.check_output([ef,'-f','1','-l','1','-cfg',cfg,'-raw',file,'-']) #这个命令中的所有调用文件参数必须使用full path.否则调用出错。 return bo.decode('utf-8') dr = r'M:\0700 SPEC&GAD' files = [f for f in os.listdir(dr) if isfile(join(dr,f)) and f.endswith('.pdf')] for file in files: bo = convert(join(dr,file)) if len(bo)!=0: print(bo.split('\r\n'))
```
###[使用浏览器打开网页](http://gohom.win/2015/12/22/pyWebbrowser/)
```php
import webbrowser
a=webbrowser.get('safari')
#a=webbrowser.MacOSX('safari')
a.open("http://www.baidu.com")
```
###npm包列表
```php
$ ls `npm root -g`
anywhere       browser-sync  json-server  nodeppt     spy-debugger
apidoc         dredd         jstophp      phantomjs   tianqi
asciify        gulp          livepool     puer        tldr
baidu-ocr-api  hexo          m-console    sails       webpack
bower          http-server   markdown     spawn-sync  weinre
```
###[音乐audio 的 play()](https://segmentfault.com/q/1010000007479793)
```php
#需要用户主动去触发才得行
    <div>
        <audio controls="true" id="audio">
            <source src="http://i.dxlfile.com/app/music/27.mp3" />
            <!-- <source src="http://i.dxlfile.com/app/music/27.ogg" /> -->
            <!-- <source src="http://i.dxlfile.com/app/music/27.ogg" /> -->
        </audio>
        <a href="javascript:;" id="fakeClick"></a>
    </div>
    <script>
    var audio = document.getElementById("audio");
    var aEle = document.getElementById("fakeClick");

    aEle.addEventListener('click', function(e) {
        e.preventDefault();
        audio.play();
    })

    function fakeClick(fn) {
        var evt;
        if (document.createEvent) {
            evt = document.createEvent("MouseEvents");
            if (evt.initMouseEvent) {
                evt.initMouseEvent("click", true, true, window, 0, 0, 0, 0, 0, false, false, false, false, 0, null);
                aEle.dispatchEvent(evt);
            }
        }
    }

    audio.addEventListener("canplay", fakeClick);
    </script>
```
###[返回100条不重复的记录](https://segmentfault.com/q/1010000008024825)
```php
'UPDATE `list` SET `State` = '1', `pid` = ' . getmypid() . '  WHERE `State` = '0' LIMIT 100;'
'SELECT * FROM `list` WHERE `pid` = ' . getmypid() . ' LIMIT 100'
'UPDATE `list` SET `pid` = ' . getmypid() . ' WHERE `pid` = '0''
```
###随机红包
```php
function randomRed($total,$num,$min = 0.01){
        $list = [];
        for($i= 1;$i< $num;$i++){
            $safe_total = ($total-($num-$i)*$min)/($num-$i);//随机安全上限
            $money      = mt_rand($min*100,$safe_total*100)/100;
            $total      = $total-$money;
            $list[$i]   = round($money,2);
        }
        $list[$num] = round($total,2);
        return $list;
    }
```
###[html5lib](https://www.v2ex.com/t/331908#reply6)
```php
# -*- coding: utf-8 -*-

import requests
from bs4 import BeautifulSoup

def get_info_from(url):
    headers = {
        "User-Agent":"Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36"
    }
    web_data = requests.get(url, headers=headers)
    web_data.encoding = 'utf-8'
    # print(web_data.text)    # 输出的结果中，搜索 t_con ，可以搜到
    soup = BeautifulSoup(web_data.text, 'lxml')#xml 改成 html5lib,解析器对非标准的 html 格式的解析结果不一样， lxml 会忽略掉不符合规则的标签， html5lib 会自动补全不正确的
    # print(soup)     # 输出的结果中，搜索 t_con, 搜不到了，为什么经过处理后却搜索不到了呢？

if __name__ == "__main__":
    test_url = "http://tieba.baidu.com/f?kw=%E4%B8%BA%E7%9F%A5%E7%AC%94%E8%AE%B0&ie=utf-8&pn=0"
    get_info_from(test_url)
```
###jquery eq
```php
 var a = Math.ceil($("li").length/2)
    for (var i=0; i<a; i++) { 
    //循环5次
        var j = i + Math.floor($("li").length/2)
        console.log(j) 
    // j = 5，6，7，8，9
        $("li:eq(j)").addClass("display") 
    //失败
        //$("li").eq(j).addClass("display") //或者$("li:eq("+j+")")
    //成功
    }
```
###[顺序读取JSON中的数据](https://segmentfault.com/q/1010000000327993)
```php
var triangle = {a:1, b:2, c:3};
for (var x in triangle) {
    console.log(x)
}
//应尽量避免编写依赖对象属性顺序的代码。如果想顺序遍历一组数据，请使用数组并使用 for 语句遍历。 如果想按照定义的次序遍历对象属性
先把所有 key 取出来，比如用 Object.keys()

var keys = Object.keys(triangle);
然后再把 keys 数组排序，然后再遍历这个数组
```
###[I Don't Know HTML](https://zhuanlan.zhihu.com/p/24748391)
```php
浏览器不支持 JavaScript 时 “隐藏” JavaScript 代码
<script type="text/javascript">
<!--
function displayMsg() {
    alert("Hello World!")
}
//-->
</script> 
<base href="www.zhihu.com/" target="_blank"><a href="liukanshan.gif">

www.zhihu.com/liukanshan.gif 并且有 target 属性，值为 _blank
通过其 dir 属性改变被其包围的文字的书写方向
<bdo dir="rtl">
Thanks for watching my blog.
</bdo>
输出是：

.golb ym gnihctaw rof sknahT
<details>
  <!-- 默认显示 summary 中的内容 -->
  <summary>页面加载后会显示summary包围的内容</summary>
  <!-- 默认以下内容是隐藏的,可以通过点击展开-->
  <p>这里可以放任何内容，但是默认是隐藏的</p>
  <p>也可以通过设置 <details open>默认展开所有内容<p>
</details>


```
###[home目录下所有的文件列表](https://zhuanlan.zhihu.com/p/24722347)
```php
[ item for item in os.listdir(os.path.expanduser('~')) if os.path.isfile(item) ]
home目录下所有目录的目录名到绝对路径之间的字典
{ item: os.path.realpath(item) for item in os.listdir(os.path.expanduser('~')) if os.path.isdir(item) }

```
###[map 有返回值（返回修改后的数组），forEach 没有返回值](https://segmentfault.com/q/1010000007977209)
```php
for 是循环的基础语法，可以有 for...in, foo...of,for(let i = 0; i < len; i++) 等。在for循环中可以使用 continue, break 来控制循环。

forEach 可以当做是for(let i = 0; i < len; i++)的简写，但是不能完成 i + n 这种循环，同时也不支持 continue 和 break，只能通过 return 来控制循环。另外，使用forEach的话，是不能退出循环本身的。

map的用法应该是循环当前可循环对象，并且返回新的可循环对象，跟for和forEach是不同的。
forEach相比普通的for循环的优势在于对稀疏数组的处理，会跳过数组中的空位
var arr = new Array(1000);

arr[0] = 1;
arr[99] = 3;
arr[999] = 5;
// for循环
for (var i = 0, l = arr.length; i < l; i++) {
    console.log('arr[%s]', i, arr[i]);
}
console.log('i :' , i);
// ...
// arr[0] 1
// ...
// arr[99] 3
// ...
// arr[999] 5
// i : 1000

// for - in 循环
var count = 0;
for(var j in arr){
    count ++ ;
    if(arr.hasOwnProperty(j)){
        console.log('arr[%s]', j, arr[j]);
    }
}
console.log('count : ', count);
// arr[0] 1
// arr[99] 3
// arr[999] 5
// i : 1000
var arr = new Array(1000);
arr[0] = 1;
arr[99] = 3;
arr[999] = 5;

var count = 0;
arr.forEach(function(value, index) {
    count++;
    console.log(typeof index);
    console.log(index, value);
});
console.log('count', count);
// number
// 0 1
// number
// 99 3
// number
// 999 5
// count 3
```
###[JavaScript数组去重](https://zhuanlan.zhihu.com/p/24753549)
```php
function unique(arr) {
    var ret = [];
    arr.forEach(function(item){
        if(ret.indexOf(item) === -1){
            ret.push(item);
        }
    });
    return ret;
}
function unique(arr) {
    return arr.filter(function(item, index){
        // indexOf返回第一个索引值，indexOf()使用的是严格比较，也就是===
        // 如果当前索引不是第一个索引，说明是重复值
        return arr.indexOf(item) === index;
    });
}
利用了对象（tmp）的key不可以重复的特性来进行去重
function unique(arr) {
    var ret = [];
    var len = arr.length;
    var tmp = {};
    for(var i=0; i<len; i++){
        if(!tmp[arr[i]]){
            tmp[arr[i]] = 1;
            ret.push(arr[i]);
        }
    }
    return ret;
}
function unique(arr){
    var set = new Set(arr);
    return Array.from(set);
}
```
###php自动执行
```php
$start = 1;
for ($i = 0; $i < 10; $i++) {
    print_r(
        (function ($hello) use (&$start) {
            return json_encode([$start, $hello, $start += rand(1, 5)]);
        })('黑PHP真的好玩吗？') . "\n");
}
```
###[print 打印嵌在其它结构里的字符串会默认 escape 模式](https://www.v2ex.com/t/332933#reply2)
```php
cur.execute(sql+entering) 
results = cur.fetchone() 

print results 
print results[0]
改成 
cur.execute(sql+entering) 
results = cur.fetchone() 

 
#print 中文的话还要加一个 str 
for result in results: 
    print str(result)    
```
###iconv 转换编码
如果出现错误 illegal input sequence at position，可以尝试忽略（iconv -f UTF-8 -t GBK//IGNORE ...）或转换（iconv -f UTF-8 -t GBK//TRANSLIT ...）无效字符。
###[微信如何查看页面源码](http://www.w3cmark.com/2017/weixin-debug-open.html)
在微信会话列表页点击右上角“加号按钮”，选择菜单中的”添加朋友”，在添加朋友界面的搜索框中输入字符串：“:help”，然后点击搜索
里面有四个调试功能：上传日子/修复数据/上传文件/js调试功能
###[词云工具wordcloud2](https://github.com/timdream/wordcloud2.js/)
`WordCloud(document.getElementById('my_canvas'), { list: list } );`
###页面翻转
```php
body{
    -webkit-transform: rotate(3deg);
    -moz-transform: rotate(3deg);
    -o-transform: rotate(3deg);
	padding-top:20px;
    }
    ```
    ###[一行js代码破解百度云大文件下载限制](http://blog.jarjar.cn/one-line-js-crack-baidu-yun/)
    ```php
    Object.defineProperty(this , 'navigator' , {value: { platform: "" }});

Object.defineProperty(navigator,'platform',{get:function(){return 'Android';}});

    ```
###[is_writeable函数bug问题](http://blog.csdn.net/u013474436/article/details/50674040)
```php
function is_really_writable($file)
    {
        // If we're on a Unix server with safe_mode off we call is_writable
        if (DIRECTORY_SEPARATOR == '/' AND @ini_get("safe_mode") == FALSE)
        {
            return is_writable($file);
        }

        // For windows servers and safe_mode "on" installations we'll actually
        // write a file then read it.  Bah...
        if (is_dir($file))
        {
            $file = rtrim($file, '/').'/'.md5(mt_rand(1,100).mt_rand(1,100));

            if (($fp = @fopen($file, FOPEN_WRITE_CREATE)) === FALSE)
            {
                return FALSE;
            }

            fclose($fp);
            @chmod($file, DIR_WRITE_MODE);
            @unlink($file);
            return TRUE;
        }
        elseif ( ! is_file($file) OR ($fp = @fopen($file, FOPEN_WRITE_CREATE)) === FALSE)
        {
            return FALSE;
        }

        fclose($fp);
        return TRUE;
    }
```
###[斐波那契数列](https://www.v2ex.com/t/331932)
```php
$total = [0, 1];

for ($i = 2; $i < 10; $i++)
{
	$total[] = $total[$i - 1] + $total[$i - 2];
}
>>> $total
=> [
     0,
     1,
     1,
     2,
     3,
     5,
     8,
     13,
     21,
     34,
   ]
   a, b = b , a+b
   import numpy 

def mm_fib(n): 
    return (numpy.matrix([[2,1],[1,1]])**(n//2))[0,(n+1)%2] 

[mm_fib(i) for i in range(20)]

def fib1(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    return fib1(n-1) + fib1(n-2)
```
###[git add . 仅仅记录了增加或修改的文件，要用 git add -A](https://www.v2ex.com/t/332492)
```php
Git Version 1.x git add 时候 add 没 add 删除的部分
ignorecase=false
git add -A = git add . + git add -u 
Git v.2.x 中 `git add .`会跟踪删除记录
http://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add 
```
###[代理服务器](https://zhuanlan.zhihu.com/p/24382606)
```php
server {
    location / {
        proxy_pass http://localhost:8080/;
    }

    location ~ \.(gif|jpg|png)$ {
        root /data/images;
    }
}
```
###[@加标签](https://segmentfault.com/q/1010000007971440)
```php
$text = preg_replace_callback('(@[^\s]+)',function($matches){
    //这里直接把要替换的结果return出去就可以了
    return "<a href='javascript:;'>{$matches[0]}</a> ";
},'是否订购@刘一届 @测试 @zxldev');

print_r($text);
是否订购<a href="javascript:;">@刘一届</a> <a href="javascript:;">@测试</a> <a href="javascript:;">@zxldev</a>
```
###填充0
```php
//格式化函数
function formatString($i){
    return str_pad(substr("$i",0,1),strlen($i),'0',STR_PAD_RIGHT);
}
//测试调用
$result = array();
foreach(array(120,560,2360,12345) as $item){
        $result[] = formatString($item);
}
//打印结果
print_r($result);[100,500,2000,10000]
```
###[update时怎么排除当前记录](https://segmentfault.com/q/1010000007981653)
```php
use Illuminate\Validation\Rule;

Validator::make($data, [
    'email' => [
        'required',
        Rule::unique('users')->ignore($user->id),
    ],
]);
backend/user/{id}
public function rules()
    {
        $id = $this->route('id'); //获取当前需要排除的id
        return [
            'email' => "required|email|unique:users,email,".$id,
        ];
    }
```
###ajax post json
```php
$data=json_decode(file_get_contents('php://input'));
先encode然后decode一遍才行$data=json_decode(json_encode($request->all()))
```
###[解决分页效率问题](http://www.moell.cn/article/17)
```php
select name from user where sex='女' order by last_login_time limit 10000000,10
select 字段列...... from table inner join (
            select  主键 from table
            where x.sex='女' order by last_login_time limit 1000000,10
 ) as x using(主键);
```
###[PHP中global的问题](https://segmentfault.com/q/1010000007244617)
```php
function test_global() {
    global $vars;
    $vars='OK';  
}
 
test_global();  
echo $vars;      //OK
<?php
//#1全局的时候$GLOBALS['var']就是$var。
$var=999;
unset($GLOBALS['var']);
var_dump($var); //报错 NULL


//#2在函数内部，$GLOBALS['var']就是外部全局的$var
$var=999;
function test(){
    unset($GLOBALS['var']);
}
test();
var_dump($GLOBALS['var']); //报错 NULL
var_dump($var); //报错 NULL


//#3没有全局$var的时候，函数内部执行global $var;会创建一个空值的内部$var和一个空值的外部$var，在链接起来。
function test2(){
    global $var;
    var_dump($var); //NULL
    var_dump($GLOBALS['var']); //NULL
    $var = 999;
}
test2();
var_dump($var); //999
var_dump($GLOBALS['var']); //999
```
###[SplFixedArray ](https://segmentfault.com/q/1010000007979799)
```php
$arrA = SplFixedArray ::fromArray(array(true));
$arrB = SplFixedArray ::fromArray(array(false));

//json_encode($arrB);

$equal = ($arrA == $arrB);
var_export($equal);
注释掉json_encode($arrB)时，$equal为true，去掉注释，$equal为false

```