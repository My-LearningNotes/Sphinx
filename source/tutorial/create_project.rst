**************
项目创建和配置
**************

在Windows系统下的命令行使用Sphinx, 和在Ubuntu下的命令行中使用差不多.


项目创建
========

*   创建工作目录后, 在其中运行\ ``sphinx-quickstart``\ , 运行此命令后需要在命令行中设置一些项目的参数, 根据情况设置即可;

.. note::

    * ``> Separate source and build directories (y/n) [n]``\ 选择\ ``y``\ --- 将源目录和构建目录分开;

    * ``Project language``\ 默认是\ ``en``\ , 可以设置为\ ``zh_CN``, 表示中文简体.

*   执行完上述命令之后, 工作目录中会生成以下几个文件和目录:

    *   ``source/`` - 源文件存放目录
    *   ``make.bat`` - Windows系统下，构建使用的批处理文件
    *   ``Makefile`` - Linux系统下，\ ``make``\ 使用的Makefile
    *   ``build/`` - 编译生成文件的存放目录

*   在\ ``source``\ 目录下有以下文件和目录:

    *   ``conf.py`` - 项目配置文件
    *   ``index.rst`` - 项目顶层页面文件
    *   ``_static`` - html静态主题存放目录
    *   ``_templates`` - 模板存放目录


项目配置
========


配置\ ``conf.py``
-----------------

*   设置\ ``sphinx_rtd_theme``\ 主题样式

    *    在文件头部添加: ``import sphinx_rtd_theme``
    *   设置\ ``html_theme = 'sphinx_rtd_theme'``

*   设置LOGO

    设置\ ``html_logo = 'path/to/logo'``\ .

*   不显示源文件链接

    默认会在生成的html页面中显示rst源文件链接, 设置\ ``html_show_sourcelink = False``\ 后不显示.


``index``\ 页面配置
-------------------

``toctree``\ 指令用来生成文档目录树, 会根据指令中的文档列表，读取它们的文档标题，然后插入到目录树中.

Example:

.. code-block:: text
    :emphasize-lines: 1, 2, 3, 4, 5, 7, 8, 9

    .. toctree::
        :maxdepth: 1
        :numbered:
        :caption: "hello, world"
        :name: ref_name

        intro
        strings
        datatype

*   *文档列表*\ 在\ ``toctree``\ 指令及其选项后, 空一行, 列出各子文档, 子文档可以不加后缀名(注意各子文档的对齐);

    文档路径可以使用相对路径或绝对路径:

        * 相对路径是相对\ ``toctree``\ 指令所在文件的路径
        * 绝对路径是相对于源文件根目录的路径

    *   ``maxdepth``\ - 设置目录树的深度, 即在目录树中显示几级子 文档的标题;
    *   ``numbered``\ - 如果需要给目录树中的各章节添加序号, 就添加该选项;
    *   ``caption``\ - 指定目录树的标题;
    *   ``name``\ - 指定一个用来引用的名称.

.. note::

    如果有文档没有出现在任何\ ``toctree``\ 指令中, 编译时会有警告.


生成文档
========

*   生成\ ``html``\ 文档

    *   Ubuntu

    在项目根目录下执行:

    .. code-block:: bash
        :emphasize-lines: 1

        make html

    * Windows

    在项目根目录下执行:

    .. code-block:: bash
        :emphasize-lines: 1

        ./make.bat html


生成的html文档保存在: ``build/html/``\ 目录下, 可以使用浏览器打开浏览.

