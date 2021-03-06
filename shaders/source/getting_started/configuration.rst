命令行参数和配置
===========================

命令行界面
----------------------

使用manim运行一个动画，需要进入到与 ``manim.py`` 同级的目录中，并向命令行中输入如下格式的命令：

.. code-block:: sh

    python manim.py <code>.py <Scene> <flags>

- ``<code>.py`` : 你写的python文件，需要与 ``manim.py`` 同级，否则需要使用绝对路径，或写准相对路径
- ``<Scene>`` : 你想要渲染的场景，或者一些场景。如果没有写或者写错，若文件中只有一个Scene，会直接渲染这个类，否则会列出所有让你选择
- ``<flags>`` : 传入的选项

一些常用的选项
^^^^^^^^^^^^^^^^^

- ``-w`` 把场景写入文件
- ``-o`` 把场景写入文件并打开
- ``-s`` 跳到最后只展示最后一帧

  - ``-so`` 保存最后一帧并打开

- ``-n <number>`` 跳到场景中第 ``n`` 个动画 
- ``-f`` 打开窗口全屏

所有支持的选项
^^^^^^^^^^^^^^^^^^^

========================================================== ========== ==============================================================================
选项                                                        简写       含义
========================================================== ========== ==============================================================================
``--help``                                                 ``-h``     显示提示信息并退出
``--write_file``                                           ``-w``     把场景渲染成视频文件
``--skip_animations``                                      ``-s``     跳到最后一帧
``--low_quality``                                          ``-l``     使用低质量渲染(默认480p15)
``--medium_quality``                                       ``-m``     使用中等质量渲染(默认720p30)
``--hd``                                                              使用高质量渲染(默认1080p30)
``--uhd``                                                             使用4K质量渲染
``--full_screen``                                          ``-f``     全屏呈现窗口
``--save_pngs``                                            ``-g``     把所有帧都保存为png文件
``--save_as_gif``                                          ``-i``     把场景输出为gif文件
``--transparent``                                          ``-t``     渲染alpha通道，视频为mov格式
``--quiet``                                                ``-q``    
``--write_all``                                            ``-a``     渲染文件中的所有场景
``--open``                                                 ``-o``     保存文件后自动打开
``--finder``                                                          打开保存文件的文件夹
``--file_name FILE_NAME``                                             给输出文件重命名
``--start_at_animation_number START_AT_ANIMATION_NUMBER``  ``-n``     后面接两个数(逗号隔开)仅渲染一部分动画，如"3,6"
``--resolution RESOLUTION``                                ``-r``     分辨率，传入格式为"WxH", 如"1920x1080"
``--frame_rate FRAME_RATE``                                           视频帧率（整数）
``--color COLOR``                                          ``-c``     背景颜色
``--leave_progress_bars``                                             保持进度条留在终端中
``--video_dir VIDEO_DIR``                                             存放视频的目录
========================================================== ========== ==============================================================================

个性化默认值
--------------

为了进行更多配置（关于目录等）并且永久更改默认值（不必每次都在命令中添加flags），
可以修改 ``custom_default.yml`` ，其中各选项含义见： :doc:`../documentation/custom_default` 。

你也可以对于不同目录使用不同的custom_default.yml，如按照以下目录结构：

.. code-block:: text

    manim/
    ├── manimlib/
    │   ├── animation/
    │   ├── ...
    │   └── window.py
    ├── project/
    │   ├── code.py
    │   └── custom_default.yml
    ├── custom_default.yml
    └── manim.py

进入 ``project/`` 文件夹中，运行 ``python ../manim.py code.py <Scene>`` 的时候，
会用 ``project/`` 文件夹下的 ``custom_default.yml`` 覆盖 ``manim/custom_default.yml``。