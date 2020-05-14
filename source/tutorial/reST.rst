***************
reST Directives
***************

*reStructuredText*\ 比\ *Markdown*\ 强大很多，这里只介绍一些常用的\ *reST指令*\ .

详细可以参考:

	`reST <https://rest-sphinx-memo.readthedocs.io/en/latest/ReST.html#>`_

	`reStructuredText Directives <http://docutils.sourceforge.net/docs/ref/rst/directives.html>`_


章节标题
========

在文本下一行(或上一行)添加至少与文本长度相同等宽的符号, 即可以使文本成为标题.
但没有规定某一级别的标题必须使用什么符号, 可以参考Python文档的一些约定:

	* ``#`` with overline, for parts
	* ``*`` with overline, for chapters
	* ``=``, for sections
	* ``-``, for subsections
	* ``^``, for subsubsections
	* ``"``, for paragraphs

.. _reStructuredText: http://docutils.sourceforge.net/rst.html


段落
====

段落是构成reST文档的基本单位. 
通过一个或一个以上的空行分隔的文本区块就是一个段落. 
正如Python中一样, reST中的缩进非常重要. 同一段落的多个文本行必须有一样的缩进. 

段落内换行并不会在html文档中生成换行符，要想保持在文本编辑器中的换行符, 需要在这些行的开头加上\ ``|``\ 和空格.

Example:

	.. code-block:: text
		:emphasize-lines: 1, 2, 3, 5, 6, 7

		aaa
		bbb
		ccc

		| aaa
		| bbb
		| ccc

	效果:

		aaa
		bbb
		ccc

		| aaa
		| bbb
		| ccc


行内标记
========

常用的行内标记有:

	* 一个星号 - 字体斜体
	* 两个星号 - 字体加粗
	* 两个反引号 - 代码或内容引用

标记需要注意的一些限制:

	* 不能相互嵌套
	* 内容前后不能有空白
	* 如果内容需要特殊字符分隔，使用反斜杠转义

Example:

	.. code-block:: text
		:emphasize-lines: 1, 2, 3

		*斜体*
		**粗体**
		``代码或引用``

	效果:

		*斜体*

		**粗体**

		``代码或引用``


列表
====

* **符号列表**: 在段落的开头放置一个星号和一个空格

Example:

	.. code-block:: text
		:emphasize-lines: 1, 2, 3

		* item1
		* item2
		* item3

	效果:

		* item1
		* item2
		* itme3


* **编号列表**: 编号加点或加空格, 或\ ``#``\ 加点加空格

Example:

	.. code-block:: text
		:emphasize-lines: 1, 2, 3, 4, 5, 6

		1. item1
		2. item2
		3. item3
		#. item4
		#. item5
		#. item6

	效果:

		1. item1
		2. item2
		3. item3
		#. item4
		#. item5
		#. item6

* **定义列表**: 术语(只能一行)的下一行缩进，下一行为定义内容

Example:

	.. code-block:: text
		:emphasize-lines: 1, 2, 4, 5

		Foo
			This is very interesting.

		BAR
			This is very interesting, too.

	效果:

		FOO
			This is very interesting.

		BAR
			This is very interesting, too.


.. note::

	列表可以嵌套，但是需要跟父列表使用空行进行分隔，并且需要相对父列表缩进.

代码
====

在reST文档中列出代码有三种方式.

* **行内代码**

用两个反单引号包裹代码: ````code````.

.. note::

	反单引号的前后要有空格和其它部分分隔, 如果在显示时不要空格，可以使用反斜杠转义空格.

* **简单代码块**

在代码块的上一个段落后面使用两个冒号，空一行后开始代码块，代码块要缩进.

Example:

	.. code-block:: text
		:emphasize-lines: 1

		source code below::

			void foo()
			{
				int i;
				for(i = 0; i < 10; ++i)
					std::cout << "i: " << i << std::endl;
			}

	效果:

		source code below::

			void foo()
			{
				int i;
				for(i = 0; i < 10; ++i)
					std::cout << "i: " << i << std::endl;
			}

* **复杂代码块**

使用\ ``.. code-block:: <language>``\ 指令，还可以列出行号和高亮重点行等.

Example:

	.. code-block:: text
		:linenos:
		:emphasize-lines: 3, 4, 5

		source code again

		.. code-block:: cpp
			:linenos:
			:emphasize-lines: 1

			void foo()
			{
				int i;

				for(i = 0; i < 10; ++i)
					std::cout << "i: " << i << std::endl;
			}

	效果:

		source code again

		.. code-block:: cpp
			:linenos:
			:emphasize-lines: 1

			void foo()
			{
				int i;
				for(i = 0; i < 10; ++i)
					std::cout << "i: " << i << std::endl;
			}

	.. note::

		`What's the difference between the code and code-block direcitves in ReST? <https://stackoverflow.com/questions/34845889/whats-the-difference-between-the-code-and-code-block-directives-in-rest>`_

		``code`` is a reStructureText directive. ``code-block`` is a Sphinx directive.

		The ``code-block`` has a different set of options to the ``code`` directive. E.g. ``:emphasize-lines:``

		As you are using Sphinx I would recommended using the ``code-block`` directive.

		When using ``code-block`` I always get the correct highlighting. When using ``code`` I sometimes get colors and sometimes just literal code blocks. 
		I have yet to figure out what combinations of setting in *conf.py* that predictably generates colored output.

		The ``code`` directive does have the advantage that the document can be use both in a Sphinx document tree and at the same time as a stand-alone reStructuredText document.


超链接
=======

* **行内超链接** - ```链接文字 <URL>`_``

* **分开的超链接**

    * 使用链接的地方: ```链接文字`_``
    * 定义链接的地方: ``.. _链接文字: URL``

Example:

    .. code-block:: text
    	:emphasize-lines: 1, 3, 5

        visit `google <https://www.google.com/>`_

        visit `google`_

        .. _google: https://www.google.com/

	效果:

    	visit `google <https://www.google.com/>`_

    	visit `google`_

    	.. _google: https://www.google.com/


图片
====

使用\ ``image``\ 指令定义图片.

Example:

	.. code-block:: text
		:emphasize-lines: 1, 2, 3

		.. image:: images/logo.jpg
			:width: 200px
			:height: 200px

	效果:

    	.. image:: images/logo.jpg
    		:width: 200px
    		:height: 200px


表格
====

* **简单表格**

标题行和内容之间，第一行之前和最后一行之后, 用\ ``=``\ 分割, 列之间用空格分割.

Example:

    .. code-block:: text
    	:emphasize-lines: 1, 2, 3, 4,5, 6, 7, 8

        ===== ===== =======
        A      B    A and B
        ===== ===== =======
        False False False
        True  False False
        False True  False
        True  True  True
        ===== ===== =======

	效果:

    	===== ===== =======
    	A      B    A and B
    	===== ===== =======
    	False False False
    	True  False False
    	False True  False
    	True  True  True
    	===== ===== =======

* **网格表格**

横向用\ ``-``\ 分割, 纵向用\ ``|``\ 分割，标题和内容之间可以用\ ``=``\ 分割,横向和纵向的交界处使用\ ``+``\ .

Example:

    .. code-block:: text
    	:emphasize-lines: 1, 3, 4, 5, 6, 7, 8, 9, 10

    	.. table: Caption of table

        	+-------------------------+----------+--------- +----------+
        	| Header row, column 1    | Header 2 | Header 3 | Header 4 |
        	| (header rows optional)  |          |          |          |
        	+=========================+==========+==========+==========+
        	| body row 1, column 1    | column 2 | column 3 | column 4 |
        	+-------------------------+----------+----------+----------+
        	| body row 2              | ...      | ...      | ...      |
        	+-------------------------+----------+----------+----------+

	效果:

    	.. table:: Caption of table

    		+-------------------------+----------+----------+----------+
        	| Header row, column 1    | Header 2 | Header 3 | Header 4 |
        	| (header rows optional)  |          |          |          |
        	+=========================+==========+==========+==========+
        	| body row 1, column 1    | column 2 | column 3 | column 4 |
        	+-------------------------+----------+----------+----------+
        	| body row 2              | ...      | ...      | ...      |
        	+-------------------------+----------+----------+----------+


引用
====

引用，就是使用文本作为标签来表示其它的对象, 在正文中可以使用该文本标签.

定义引用的格式为: ``.. [Ref] content of ref``, 使用引用的格式为: ``[Ref]_``.

Example:

	.. code-block:: text
		:emphasize-lines: 1, 3

		It is mentioned by [Ref]_ that  C++ is good.

		.. [Ref] <<zzq's talk>>

	效果:

		It is mentioned by [abc]_ that C++ is good.

		.. [abc] <<zzq's talk>>


脚注
====

脚注与引用语法类似, 只是它在正文中显示的不是文本, 而是编号.

Example:

	.. code-block:: text
		:emphasize-lines: 1, 3, 5, 6

		orem ipsum [#f1]_ dolor sit amet ... [#f2]_

		Footnotes

		.. [#f1] Text of the first footnote.
		.. [#f2] Text of the second footnote.

	效果:

		orem ipsum [#f1]_ dolor sit amet ... [#f2]_

		Footnotes

			.. [#f1] Text of the first footnote.
			.. [#f2] Text of the second footnote.


替换
====

替换就是使用文本标签来表示其它的对象, 在生成文档时, 正文中所有使用标签的地方都会被实际内容所替换.

Example:

	.. code-block:: text
		:emphasize-lines: 1, 3

		I like eat |apple| very much.

		.. |apple| replace:: 苹果

	效果:

		I like eat |apple| very much.

		.. |apple| replace:: 苹果
