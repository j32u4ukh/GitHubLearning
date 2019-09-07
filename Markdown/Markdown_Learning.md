# 1個 # 符號，相當於 h1
## 2個 # 符號，相當於 h2
### 3個 # 符號，相當於 h3
#### 4個 # 符號，相當於 h4
##### 5個 # 符號，相當於 h5
###### 6個 # 符號，相當於 h6

下方使用 ======== 也可產生同 h1 的效果
========

下方使用 ------------- 也可產生同 h2 的效果
-------------

小區塊(或稱代碼區)用`1個反引號`，而且可以打在句子當中。

  另一種小區塊可利用 1 個 tab

    或是 4 個 space。

```大區塊用
3個反引號
可透過第一行標註語言
第二行開始呈現程式碼```

```js
$scope.cookieGet = function(key){
  $scope.cookieResult = $cookieStore.get(key);
  console.log($scope.cookieResult);
}
```

```ruby
def index
puts "hello world"
end
```

```csharp
private void index(){
  MessageBox.Show("hello world");
}
```

[參考：Markdown支援的程式語言](http://support.codebasehq.com/articles/tips-tricks/syntax-highlighting-in-markdown)

> 多行區塊
> 使用大於符號
> (>)
>> 當使用 2 個 >
>> 則會形成巢式結構

![圖片代替文字，github內部路徑](/image/inner_demo.png)

![圖片代替文字，外部路徑](https://i.imgur.com/IgvGsB3.jpg)

*斜體* _有這2種打法(單底線)_

**粗體** __有這2種打法(雙底線)__

***粗斜體*** ___有這2種打法(3底線)___

~~雙波浪，可打出刪除線~~

若想換行，
必須按 2 次 Enter，
否則會在同一行。

超連結方法1，以[參考來源1](https://read01.com/zh-tw/J848LL.html#.XXNYzSgzZPZ)為例。

超連結方法2，以[參考來源2](https://kingofamani.gitbooks.io/git-teach/content/chapter_6_gitbook/markdown.html)為例。

# 分割線有以下 3 種方式:可以在單獨一行里輸入3個或以上的短橫線、星號或者下劃線實現。短橫線和星號之間可以輸入任意空格。

***

---

_ _ _


1. 有序列表
2. 透過編號 1, 2, 3
3. 來達成
4. 似乎不用像前面按 2 次 Enter 也可以正常分行

* 無序列表
* 可以透過單個星號

- 或是透過單個減號(-)
- 也可以

+ 加號也可以
+ 產生無序列表

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| 表格 | 第一行 | 是標題 |
| 靠左 | 置中| 靠右 |
| 則是透過 | 第二行的標記|來定義 |
| 現在是第幾欄 | 則是透過直線符號|來定義，和實際長寬無關|

<table width="100%" border="1">
  <tr>
    <td width="150">1</td>
    <td width="80%" rowspan="3">html 標籤呈現</td>
  </tr>
  <tr>
    <td>2</td>
  </tr>
  <tr>
    <td>3</td>
  </tr>
</table>

![](https://dl.dropboxusercontent.com/u/2226591/GIT/avatar2.png)文字不置中

<img style="vertical-align:middle;" src="https://dl.dropboxusercontent.com/u/2226591/GIT/avatar2.png"/>文字置中

<iframe src="https://player.vimeo.com/video/108799588?badge=0%20color=ff0179" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen>嵌入影片</iframe>


