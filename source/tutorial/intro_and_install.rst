****************
Sphinx简介和安装
****************


前言
====

写文档是开发人员日常工作中的一项重要内容, 使用标记语言, 可以利用简单免费的文本编辑器编写文档并设置格式,
再生成\ ``html``\ 或\ ``pdf``\ 等格式, 或者直接把编辑好的文件上传到\ *github*\ 或\ *wiki*\ 上, 通过浏览器查看带有格式的文档.

目前标记语言主要有两种:

    *   ``Markdown``
    *   ``reStructured(reST)``

很多开源项目的文档就是使用\ ``sphinx``\ + \ ``reST``\ .


简介
====

*   ``Sphinx``\ 是一种文档工具, 它可以轻松的撰写出清晰且优美的文档;
*   ``Sphinx``\ 已经成为Python项目首选的文档工具, 同时它对C/C++项目也有很好的支持, 并计划对其它开发语言添加特殊支持;
*   ``Sphinx``\ 采用\ ``reST``\ .


安装
====

对于Sphinx的安装, 官方有详细的文档: `Installing Sphinx <https://www.sphinx-doc.org/en/master/usage/installation.html>`_

``Sphinx``\ 本身是使用Python编写的, 需要Python环境, 所以如果没有安装Python, 需要先安装Python.

.. note::

    因为Python2渐渐的已经不再维护, 所以我们使用Python3环境.

Ubuntu系统
----------

*   ``apt``\ 安装

.. code-block:: bash
    :emphasize-lines: 2, 4

    # 安装sphinx
    sudo apt-get install python3-sphinx

    # 安装sphinx_rtd_theme, 常用的html主题
    sudo apt-get install python3-rtd-theme

*   ``pip3``\ 安装

.. code-block:: bash
    :emphasize-lines: 2, 5

    # 安装sphinx
    pip3 install -U Sphinx  # 默认安装路径是~/.local

    # 安装sphinx-rtd-theme, 常用的html主题
    pip3 install -U sphinx-rtd-theme

使用\ ``pip3``\ 安装, 默认的安装路径是\ ``~/.local/bin/``\ , 安装之后需要更新环境变量\ ``PATH``\ , 在\ ``~/.bashrc``\ 中添加如下内容:

.. code-block:: bash
    :emphasize-lines: 1

    export PATH=$PATH:~/.local/bin/


.. note::

    通常, 使用apt安装的版本比较旧; 使用pip3安装的版本比较新.


Windows系统
-----------

通常, Windows系统上默认没有安装Python3, 所以需要先安装Python3.
在Python3安装完成之后, 使用\ ``pip3``\ 安装Sphinx.

\ **以管理员身份打开命令行工具**\ , 执行以下命令:

.. code-block:: bash
    :emphasize-lines: 2, 5

    # 安装sphinx
    pip3 install -U sphinx

    # 安装sphinx-rtd-theme
    pip3 install -U sphinx-rtd-theme

