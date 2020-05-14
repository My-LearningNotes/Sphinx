在Sphinx中使用graphviz来画图
============================

-   安装graphviz

.. code-block:: shell

    # Ubuntu
    sudo apt-get install graphviz

安装完成后, 在命令行中输入\ ``dot -V``\ 来验证是否安装成功.

-   修改项目配置文件

修改项目配置文件\ ``conf.py``\ , 在其中开启graphviz插件并设置一些相关的参数:

.. code-block:: python

    # 通过配置开启graphviz插件
    extensions = ['sphinx.ext.graphviz']
  
    # 设置graphviz_dot路径
    graphviz_dot = 'dot'
    # 设置graphviz_dot_args的参数, 这里设置了默认字体
    graphviz_dot_args = ['-Gfontname=Georgia',
                         '-Nfontname=Georgia',
                         '-Efontname=Georgia']
    # 输出格式, 默认png，这里使用svg矢量图
    graphviz_output_format = 'svg'

这里\ ``graphviz_dot``\ 的值是\ ``dot``\ , 为了不把绝对路径写到配置文件中, 防止其他人的路径不一样, 所以这里要求\ ``dot``\ 这个程序在环境变量中, 能够直接使用.

-   画图

在Sphinx文档中使用graphviz段来插入图片, 可以在文档中直接使用dot语言或者使用dot文档.

Example:

.. code-block:: text

    .. graphviz::

        digraph abc{
            a;
            b;
            c;
            d;

            a -> b;
            b -> d;
            c -> d;
        }

或者使用一个dot文档:

.. code:: text

   .. graphviz::external.dot

--------------

参考:

`sphnix文档使用graphviz来画图 <https://www.chenyudong.com/archives/sphinx-docs-draw-graphic-with-graphviz.html>`__
