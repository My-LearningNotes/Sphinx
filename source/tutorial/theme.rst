主题设置
========


简介
----

Sphinx支持设置文档的主题. 
主题是HTML模板, 样式表和其他静态文件的集合.

通过\ ``conf.py``\ 中的变量\ ``html_theme``\ 设置要使用的主题.

首先, 我们来看看有哪些主题:

-   Theme provided with Sphinx

有些主题是Sphinx内建的, 随Sphinx一起提供, 安装Sphinx后就可以直接使用.

例如, 要使用\ ``classic``\ 主题, 将以下内容添加到\ ``conf.py``:

.. code-block:: text

    html_theme = 'classic'

-   有些主题不随Sphinx一起提供, 它们以静态主题的形式提供

对于静态主题, 可以是目录(包含\ ``theme.conf``\ 以及其他需要的文件), 或者内容相同的zip文件.

目录或zip文件必须放在Sphinx可以找到的地方, 在\ ``conf.py``\ 中, 通过变量\ ``html_theme_path``\ 设置静态主题的路径.

例如, 如果有主题\ ``blue.zip``\ , 可以在\ ``conf.py``\ 中做如下配置:

.. code-block:: text

    html_theme = 'blue'
    # 目录列表，设置html theme的路径
    # 可以是绝对路径或者相对conf.py的相对路径
    html_theme_path = ['.']

-   安装包

有些主题是以安装包(系统包或者Python包)的形式分发的, 可以在安装它们后使用.
如果是在Linux系统中, 可以使用系统的包管理工具(apt/yum)安装; 也可以使用Python的包管理工具\ ``pip``\ 安装.

Example:

.. code-block:: bash

    # installing theme package
    pip3 install sphinxjp.themes.dotted

安装后在\ ``conf.py``\ 中配置要使用的主题:

.. code-block:: text

    html_theme = 'dotted'


选择主题
--------

-   Theme provided with Sphinx

内建主题可以在\ `https://www.sphinx-doc.org/en/master/usage/theming.html#themes <https://www.sphinx-doc.org/en/master/usage/theming.html#themes#Themes>`__\ 的\ *Builtin Themes*\ 一节中查看.

-   第三方主题

常用的第三方主题可以在\ `PyPI`_\ , \ `GitHub`_ \ 和\ `sphinx-themes.org`_\ 上查找.

-   常用主题:

    *   sphinx_rtd_theme

    *   安装

        .. code-block:: shell

            pip3 install -U sphinx_rtd_theme


.. _PyPI: https://pypi.org/search/?q=&o=&c=Framework+%3A%3A+Sphinx+%3A%3A+Theme
.. _GitHub: https://github.com/search?utf8=%E2%9C%93&q=sphinx+theme&type=](https://github.com/search?utf8=✓&q=sphinx+theme&type=
.. _sphinx-themes.org: sphinx-themes.orgs <https://sphinx-themes.org/

--------------

参考:

https://www.sphinx-doc.org/en/master/usage/theming.html#themes

