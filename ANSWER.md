- 1.

在 post association 声明中 includes author

- 2.

将 archive vote share 作为 update 的一种操作，在 querystring 中识别

- 3.

```
around_action: wrap_in_transaction :only [:create :archive :vote]

private
  def wrap_in_transaction
    ActiveRecord::Base.transaction do
      begin
        yield
      ensure
        raise ActiveRecord::Rollback
      end
    end
  end
```

- 4.

> reference: https://codepen.io/shshaw/full/gEiDt

a. 

```
.container {
  position: relative;
}
.box {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right:  0;
  width: max-content;
  height: max-content;
  padding: 10px;
}
```
Advantages:
Cross-browser (including IE8-10)
No special markup, minimal styles
Responsive with percentages and min-/max-
Use one class to center any content
Centered regardless of padding (without box-sizing!)
Blocks can easily be resized
Works great on images

Caveats:
Height must be declared (see Variable Height)
Recommend setting overflow: auto to prevent content spillover (see Overflow)


b. 

```
.container {
  text-align: center;
  overflow: auto;
}
.container:after {
  content: '';
  height: 100%;
  margin-left: -0.25em; /* To offset spacing. May vary by font */
}
.box {
  display: inline-block;
  vertical-align: middle;
  max-width: 99%; /* Prevents issues with long content causes the content block to be pushed to the top */
    /* max-width: calc(100% - 0.25em) /* Only for IE9+ */ 
}
```

Advantages:
Content can be any width or height, even overflows gracefully
Can be used for more advanced layout techniques.

Caveats:
No IE8-9 support
Requires a container or styles on the body
Requires many vendor prefixes with different syntaxes to work on modern browsers
Possible performance issues

c.

```
.container {
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
  -webkit-box-align: center;
     -moz-box-align: center;
     -ms-flex-align: center;
  -webkit-align-items: center;
          align-items: center;
  -webkit-box-pack: center;
     -moz-box-pack: center;
     -ms-flex-pack: center;
  -webkit-justify-content: center;
          justify-content: center;
}
```
Advantages:
Content can be any width or height, even overflows gracefully
Can be used for more advanced layout techniques.

Caveats:
No IE8-9 support
Requires a container or styles on the body
Requires many vendor prefixes with different syntaxes to work on modern browsers
Possible performance issues

- 5.

https://jsfiddle.net/0ykcrkbq/6/

- 6.

	- 白色框中，左右和上下留白不统一；上下左右留白应一致，二维码周围的留白应一致
	- 字体大小过多，字体颜色过多，副标题字体太小，文字信息没有深浅变化；副标题字体应稍大，和下方文字一致，颜色比标题稍淡
	- 微信扫码 丁丁扫码 中 “扫码” 为冗余信息；扫码提示应和副标题合并
	- 二维码应合并为一个，在识别后做跳转处理
	- 白色框阴影为等距扩散，应设置 x y 偏移值
	- 知人和"zhirenhr.com"之间留白过小，zhirenhr.com 为冗余信息；删去 "zhirenhr.com" 字样，缩小 logo 并和右边字体大小匹配
	

