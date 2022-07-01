安装 yolort
============

.. _required:

**Required**

首先，按照  `官方说明安装 <https://pytorch.org/get-started/locally/>`_ PyTorch 1.8.0+ 和 torchvision 0.9.0+。

要安装 ``yolort``，您可以使用存储库

   https://github.com/zhiqwang/yolov5-rt-stack/

还有 ``setup.py`` 或者用

::

   pip install -U yolort

获取最新版本并

::

   pip install 'git+https://github.com/zhiqwang/yolov5-rt-stack.git'

安装开发版本。

.. _optional:

**Optional**

安装 pycocotools （用于评估 COCO）：

::

  pip install -U 'git+https://github.com/ppwwyyxx/cocoapi.git#subdirectory=PythonAPI'
