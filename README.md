macvim-setting
==============
##Intro

This is my .vimrc setting which is suitable for my C++ programming environment.

这是我的.vimrc 配置文件，主要用来做C++方面的一些开发，弄了一天多，现在顺眼多了。

##配置 Setting

使用平台：

- MacOSX Mavericks 10.9.4
- xcode command line tools
- latest MacVim(7.4)

I use [bundle](https://github.com/gmarik/Vundle.vim) to manage my vim plugins.

我用 [bundle](https://github.com/gmarik/Vundle.vim)来管理我的vim的插件

几个觉得比较好用的插件：

- Plugin `nerdtree`

	[
scrooloose/nerdtree](https://github.com/scrooloose/nerdtree)

- Plugin 'L9'

	新的vundle管理在vimscript网站里的可以直接写名字
- Plugin `auto-pairs`

	自动完成括号的自动补全

- Plugin `YouCompleteMe`
	
	代码补全跳转插件，支持C++标准库
- Plugin `majutsushi/tagbar`  

	显示函数、类信息，也可以使用taglist，个人比较倾向Tagbar
- plugin `tcomment_vim` 

	注释插件
- Plugin `Lokaltog/vim-powerline`

	状态栏插件，记录行数、字符编码、系统信息等

- Plugin `scrooloose/syntastic` 

	配合YouCompleteMe使用，纠错插件
- Plugin `kien/ctrlp.vim`
	
	查找文件插件


##Tips
Although vundle is convenient to finish installing these plugins, there would be some problems with installing YouCompleteMe.

其他的plugin只要按照vundle中的说明就可以搞定了，但是YouCompleteMe会有一些问题。


1. Remember to `./install --clang-completer` and it may cost you a lot of time.

	安装完之后要记得`./install --clang-completer`，如果网络有问题这个过程会很慢。

2. There is no `.ycm_extra_conf.py`. If you dont't want to just use the basic function of the plugin, you have to add this `.py` file to you project or add this command to .vimrc.

	没有`.ycm_extra_conf.py`文件。我安装完之后是没有/cpp这个文件夹的，需要自己放一个`.ycm_extra_conf.py`（配置编译信息啊等等）进去。按照YouCompleteMe的说法是每个工程都该有一个自己的`.ycm_extra_conf.py`文件，但是大部分其实可以统一的，加一行

		let g:ycm_global_ycm_extra_conf='~/.vim/bundle/YouCompleteMe/.ycm_extra_conf.py
		
	设置到你的`.ycm_extra_conf.py`的路径下即可。

3. Can't find iostream after open C++ file.

	打开C++代码提示iostream等标准库找不到

  	这是因为YouCompleteMe的配置文件找不到STL所在的路径，可以通过如下命令来找
  	
  	`echo | clang -std=c++11 -stdlib=libc++ -v -E -x c++ -`
  	
  	[参考文章：YouCompleteMe安装遇到的问题及解决办法](http://blog.marchtea.com/archives/175)

