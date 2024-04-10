# Html 常用标签

## **1. 必用**

### `html`

- 是网页的最外层元素，包含着一张网页全部的内容。
- 参考：**表/6.1**

### `body`

- 网页中所有的可视内容都应该包含在 `body` 元素中。
- 参考：**表/6.2**

### `head`

- 用于包含一张网页中抽象的基础信息（元信息），如标题，描述等等。
- 其中的信息通常是给机器看的。
- 参考：**表/6.3**

### `title`

- 用于指定浏览器标签上显示的标题，用于概括整张网页。
- 参考：**表/6.4**

### `div`

- 可用于网页中的区域划分，通常作为容器而存在。
- 参考：**表/6.7**

### `a`

- 用于定义链接。
- 参考：**表/6.8**

### `button`

- 用于定义按钮。
- 参考：**表/6.13**

### `link`

- 用于引入外部资源如 CSS。
- 参考：**表/6.12**

### `script`

- 用于引入脚本（一般为 JS）。
- 参考：**表/6.12**

### `h1`, `h2`, `h3`, `h4`, `h5`, `h6`

- 标题标签，用于概括页面中的部分的内容，其中 `h1` 最大，`h2` 其次，依次类推，没有 `h7`。
- 参考：**表/6.5**

### `span`

- 与 `div` 元素类似，只不过 `div` 用于插入整段（块）而 `span` 用于插入一个词，在表现上和普通文字没有区别。

### `input`

- `<input>` 用于接收用户的输入。没有 `<input>` 用户就没法输入数据，登录注册什么的都不能做，复杂的表单就别想了
- 参考：**表/6.16**
- `<input type="text">` 默认值（可以不填 `type` 属性），用于输入文字，如用户名，昵称等等。
- `<input type="password">` 密码输入，我们平时输密码时的小黑点就是这么来的。
- `<input type="radio">` 单选框，在需要用到单选但选项少的情况下使用。如性别（只有两个选项）。
- `<input type="checkbox">` 多选框（复选框），在需要用到多选但选项少时使用，多选，但是选项少的情况下使用。如性取向 ˙Ꙫ˙ 。
- `<input type="file">` 选择文件，上传文件必用。
- `<input type="reset">` 重置表单。
- `<input type="hidden" value="秘密">` 隐形输入框，一般用于在表单提交时回传重要的令牌（就是一串自产自销的无序字符）来验证用户是真的或状态是对的。
- `<input type="button" value="点我">` 按钮，不推荐，正常情况下使用 `<button>` 即可，因为 `<button>` 可以包含子元素，而 `<input>` 不行，灵活度的问题。

### `select`

- 下拉菜单，多选单选均可。

## **2. 常用**

### `img`

- 用于显示图片。
- 参考：**表/6.9**

### `p`

- 用于给文字划分段落，一个 `p` 就是以自然段。
- 参考：**表/6.6**

### `table`, `thead`, `tbody`, `tr`, `th`, `td`

- 用于插入表格。
- 参考：**表/6.10**
  `table`
  `thead`
  `tbody`
  `tr`
  `td`
  `th`

## **3. 偶尔使用**

### `code`, `pre`

- 都是用于定义代码，`pre` 用于定义长代码（代码块），`code` 用于定义短代码（如变量，函数名等）。
- 参考：**表/6.15**
  `<code>` 一般用于小段代码。
  `<pre>` 用于表示文字在编辑时的状态，比如在编辑器里的状态，所以一般被用于大段代码的展示，因为“所见即所得”。
  用和不用 `<pre>` 的区别：

```
__     __   
\ \   / /

 \ \
_/ /__
___
_  \   / _ \
__   | | (_
) |
   |_|\___/
```

---

\ \ / /
\ _/ /
**\ / ****\ | | (****) | |****|\**/

### `abbr`

- 用于定义缩写（**abbr**eviation）。
- 参考：**表/6.15**

# 整站布局分析-小米

```
行 导航栏
    列 链接组 左
        链接
        链接
        ...
    列 链接组 右
        链接
        链接
        ...
行 首屏
    行 产品导航
        列 LOGO
        列 链接组
        列 搜索
    行 主促销
        列 产品分类
        列 轮播
    行 辅促销
        列 单品
        列 单品
        ...
    行 明星单品
        列 单品
        列 单品
        ...
行 主体
    行 卡片组
        行 卡片组头
            列 所属分类标题
            列 标签组
        行 卡片组体
            列 左
                列 卡片
            列 右
                列 卡片
                列 卡片
                ...
    行 卡片组
    ...
行 页脚
    行 售后
        列 链接
        列 链接
        ...
    行 更多
        列 链接
        列 链接
        ...
    行 元信息
        列 链接
        列 链接
        列 链接
```

## 实战

```html
<div class="行 导航栏">
    <div class="列 链接组 左">
        <a href="#">小米商城</a>
        <a href="#">MIUI</a>
        <a href="#">IoT</a>
        <a href="#">Item</a>
        <a href="#">Item</a>
        <a href="#">Item</a>
    </div>
    <div class="列 链接组 右">
        <a href="#">登录</a>
        <a href="#">注册</a>
        <a href="#">消息通知</a>
    </div>
</div>
<div class="行 首屏">
    <div class="行 产品导航">
        <div class="列 LOGO">
            <img src="#" alt="LOGO">
        </div>
        <div class="列 链接组">
            <a href="#">手机</a>
            <a href="#">电脑</a>
            <a href="#">盒子</a>
            <a href="#">Item</a>
            <a href="#">Item</a>
            <a href="#">Item</a>
            <a href="#">Item</a>
        </div>
        <div class="列 搜索">
            <input type="text">
            <button>搜索</button>
        </div>
    </div>
    <div class="行 主促销">
        <div class="列 产品分类">
            <a href="#">手机 电话卡</a>
            <a href="#">电视 盒子</a>
            <a href="#">Item Item</a>
            <a href="#">Item Item</a>
            <a href="#">Item Item</a>
            <a href="#">Item Item</a>
        </div>
        <div class="列 轮播">
            <a href="#">
                <img src="#">
            </a>
        </div>
    </div>
    <div class="行 辅促销">
        <div class="列 快速通道组">
            <div class="行">
                <div class="列 快速通道">
                    <img>
                    <div>选购手机</div>
                </div>
                <!--2 more-->
            </div>
            <!--1 more-->
        </div>
        <div class="列 单品">
            <img>
        </div>
        <!--2 more-->
    </div>
    <div class="行 明星单品">
        <div class="列 单品">
            <img>
            <div class="文字">
                <div class="标题">Mix 2</div>
                <div class="描述">lorem ipsum ...</div>
                <div class="价格">￥100</div>
            </div>
        </div>
        <!--4 more-->
    </div>
</div>
<div class="行 主体">
    <div class="行 卡片组">
        <div class="行 卡片组头">
            <div class="列 所属分类标题">家电</div>
            <div class="列 标签组">
                <div class="标签">热门</div>
                <div class="标签">电视影音</div>
                <div class="标签">Item</div>
                <div class="标签">Item</div>
            </div>
        </div>
        <div class="行 卡片组体">
            <div class="列 左">
                <img>
            </div>
            <div class="列 右">
                <div class="行">
                    <div class="列 卡片">
                        <img>
                        <div class="文字">
                            <div class="标题">Mix 2</div>
                            <div class="描述">lorem ipsum ...</div>
                            <div class="价格">￥100</div>
                        </div>
                    </div>
                    <!--3 more-->
                </div>
                <!--1 more-->
            </div>
        </div>
    </div>
    <!--...-->
</div>
<div class="行 页脚">
    <div class="行 售后">
        <div class="列 链接">
            <img src="#">
            预约维修服务
        </div>
        <!--...-->
    </div>
    <div class="行 更多">
        <div class="列 链接组">
            <div class="列">
                <a href="#">账户管理</a>
                <a href="#">购物指南</a>
                <a href="#">订单操作</a>
            </div>
            <!--5 more-->
        </div>
        <div class="列 联系方式">
            <div class="电话">400-100-5678</div>
            <div class="描述"></div>
            <button>在线客服</button>
        </div>
    </div>
    <div class="行 元信息">
        <div>
            <a>链接</a>
        </div>
        <!--2 more-->
    </div>
</div>
```

```html
<div class="行 导航栏">
    <div class="列 链接组 左">
        <a href="#">小米商城</a>
        <a href="#">MIUI</a>
        <a href="#">IoT</a>
        <a href="#">Item</a>
        <a href="#">Item</a>
        <a href="#">Item</a>
    </div>
    <div class="列 链接组 右">
        <a href="#">登录</a>
        <a href="#">注册</a>
        <a href="#">消息通知</a>
    </div>
</div>
<div class="行 首屏">
    <div class="行 产品导航">
        <div class="列 LOGO">
            <img src="#" alt="LOGO">
        </div>
        <div class="列 链接组">
            <a href="#">手机</a>
            <a href="#">电脑</a>
            <a href="#">盒子</a>
            <a href="#">Item</a>
            <a href="#">Item</a>
            <a href="#">Item</a>
            <a href="#">Item</a>
        </div>
        <div class="列 搜索">
            <input type="text">
            <button>搜索</button>
        </div>
    </div>
    <div class="行 主促销">
        <div class="列 产品分类">
            <a href="#">手机 电话卡</a>
            <a href="#">电视 盒子</a>
            <a href="#">Item Item</a>
            <a href="#">Item Item</a>
            <a href="#">Item Item</a>
            <a href="#">Item Item</a>
        </div>
        <div class="列 轮播">
            <a href="#">
                <img src="#">
            </a>
        </div>
    </div>
    <div class="行 辅促销">
        <div class="列 快速通道组">
            <div class="行">
                <div class="列 快速通道">
                    <img>
                    <div>选购手机</div>
                </div>
                <!--2 more-->
            </div>
            <!--1 more-->
        </div>
        <div class="列 单品">
            <img>
        </div>
        <!--2 more-->
    </div>
    <div class="行 明星单品">
        <div class="列 单品">
            <img>
            <div class="文字">
                <div class="标题">Mix 2</div>
                <div class="描述">lorem ipsum ...</div>
                <div class="价格">￥100</div>
            </div>
        </div>
        <!--4 more-->
    </div>
</div>
<div class="行 主体">
    <div class="行 卡片组">
        <div class="行 卡片组头">
            <div class="列 所属分类标题">家电</div>
            <div class="列 标签组">
                <div class="标签">热门</div>
                <div class="标签">电视影音</div>
                <div class="标签">Item</div>
                <div class="标签">Item</div>
            </div>
        </div>
        <div class="行 卡片组体">
            <div class="列 左">
                <img>
            </div>
            <div class="列 右">
                <div class="行">
                    <div class="列 卡片">
                        <img>
                        <div class="文字">
                            <div class="标题">Mix 2</div>
                            <div class="描述">lorem ipsum ...</div>
                            <div class="价格">￥100</div>
                        </div>
                    </div>
                    <!--3 more-->
                </div>
                <!--1 more-->
            </div>
        </div>
    </div>
    <!--...-->
</div>
<div class="行 页脚">
    <div class="行 售后">
        <div class="列 链接">
            <img src="#">
            预约维修服务
        </div>
        <!--...-->
    </div>
    <div class="行 更多">
        <div class="列 链接组">
            <div class="列">
                <a href="#">账户管理</a>
                <a href="#">购物指南</a>
                <a href="#">订单操作</a>
            </div>
            <!--5 more-->
        </div>
        <div class="列 联系方式">
            <div class="电话">400-100-5678</div>
            <div class="描述"></div>
            <button>在线客服</button>
        </div>
    </div>
    <div class="行 元信息">
        <div>
            <a>链接</a>
        </div>
        <!--2 more-->
    </div>
</div>
```
