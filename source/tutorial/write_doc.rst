编写文档
========


*   对于reST, 目前没有什么特别好用的编辑器;
    
    可以使用MarkDown编辑器Typora编写MarkDown文档, 然后转换为rst文档.


*   对于项目中的rst文档, 如果没有在目录树中包含, 编译时会有警告;


*   ``source/index.rst``\ 定义的是项目顶层的目录树, 可以在直接添加文档;
    还可以在其中嵌套子目录的目录树.


    在一个子目录中编写文档, 并在其中定义一个\ ``index.rst``\ 定义子目录的目录树结构;
    在上一层目录的目录树结构中包含子目录的目录树结构.
