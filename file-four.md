### 一些小技巧

#### 简单设置 vim

“工欲善其事，必先利其器”。尽管 vim 非常强大，但默认配置的 vim 看起来还是比较朴素的，为了适合
我们的开发需求，要对 vim 进行一些简单的配置。

- `:set number` 显示行号
- `:set relativenumber` 显示相对行号（这个非常重要，慢慢体会）
- `:set hlsearch` 搜索结果高亮
- `:set autoindent` 自动缩进
- `:set smartindent` 智能缩进
- `:set tabstop=4` 设置 tab 制表符所占宽度为 4
- `:set softtabstop=4` 设置按 `tab` 时缩进的宽度为 4
- `:set shiftwidth=4` 设置自动缩进宽度为 4
- `:set expandtab` 缩进时将 tab 制表符转换为空格
- `:filetype on` 开启文件类型检测
- `:syntax on` 开启语法高亮

这里列出的是命令，你可以通过在 vim 中输入进行设置，但这种方式设置的参数只在本次关闭 vim 前生效，
如果你退出 vim 再打开，之前的设置就失效了。

若要永久生效，需要修改 vim 的一个自动配置文件，一般文件路径是 `/home/<user>/.vimrc`（Linux
系统）或 `/Users/<user>/.vimrc`（Mac OS 系统）

如果没有就新建一个，以 Mac OS 系统为例：

> 在控制台执行如下命令，每行结尾记得回车

```bash
cd ~
vim .vimrc
```

> 现在你已经在 vim 中打开了你的 vim 专属配置文件，将上面提到的配置复制到你的文件中，记得要删除
> 每行开头的 `:`
>
> 修改完成执行 `:wq` 或者 `ZZ` 保存退出，再次进入 vim 时，你的这些配置就已经生效了
>
> 当然，机智如我也为你准备好了一份 vimrc-demo 文件，你可以在控制台执行
> `cp vimrc-demo ~/.vimrc` 直接使用，再次启动 vim 你的配置就应该生效了。

#### 清除搜索高亮

前面提到的配置中，有一项是高亮全部搜索结果 `:set hlsearch`，其作用是当你执行 `/`
、`?`、`*` 或 `#` 搜索后高亮所有匹配结果。

> 如果你已经设置了这个选项，尝试执行 `/set`

看到效果了吧，搜索结果一目了然，但这有时候也是一种困扰，因为知道搜索结果后高亮就没用了，但高亮
本人并不这样认为，它会一直高亮下去，直到你用 `:set nohlsearch` 将其关闭。

但这样需要就打开，不需要就关闭也不是个办法，有没有更好的解决方案呢？当然！请看下面的终极答案：

> **再搜一个不存在的字符串**

通常我用来清除搜索高亮的命令是 `/lfw`，一是因为 `lfw` 这个组合一般不会出现（不适用于
本文档...），二是这三个字母的组合按起来比较舒服，手指基本不需要怎么移动（你感受一下）。

#### 重复上一次命令

vim 有一个特殊的命令 `.`，你可以用它重复执行上一个命令。

> 按下面的说明进行操作

```
按 dd 删除本行
按 . 重复删除操作
2. 再删除两行
这行也没了
p 把刚才删掉的粘回来
3. 又多出 6 行
```

#### 缩进

- `>>` 向右缩进当前行
- `<<` 向左缩进当前行

> 在这一行上依次按 `3>>`，`<<` 和 `<G` 看看效果
>
> 打酱油行

#### 自动排版

- `==` 自动排版当前行
- `gg=G` 当前文档全文自动排版
- `<N>==` 对从当前行开始的 N 行进行自动排版
- `=<N>j` 对当前行以及向下 N 行进行自动排版
- `=<N>k` 对当前行以及向上 N 行进行自动排版

> 另外，还可以利用[第二章](file-two.md)中提到的匹配搜索对代码块进行批量排版，尝试用
> `gf` 命令打开 file-four-demo.js 按照里面的说明进行操作

如果智能缩进设置生效了，执行后会看到如[第二章](file－two.md)中一样的排版效果。

[下一章](file-five.md)将介绍分屏和标签页。
