##################################
yolort 文档
##################################

**yolort 是什么？**

``yolort`` 专注于使目标检测任务的训练和推理更加无缝地结合在一起。 ``yolort`` 现在采用了与官方 ``YOLOv5`` 相同的模型结构。
不同的是， ``yolort`` 采用了动态形状机制，在此机制中，可以将预处理（ ``letterbox``）和后处理（ ``nms``）嵌入到模型 graph 中，简化了部署策略。
从这个意义上说， ``yolort`` 使得在 ``LibTorch``、 ``ONNX Runtime``、 ``TensorRT``、 ``TVM`` 等平台上的部署更加友好成为可能。

.. _about-the-code:

**关于代码**

遵循 `detr <https://github.com/facebookresearch/detr>`_ 设计原则：

..

   目标检测不应该比分类更困难，也不应该需要复杂的库来进行训练和推理。

``yolort`` 的实现和实验非常简单。你喜欢 torchvision 的 faster-rcnn，retinanet 或 detr 的实现吗？你喜欢 yolov5 吗？你会爱上 yolort！

快速上手
================

读取图像源并检测其目标：

.. code:: python

   from yolort.models import yolov5s

   # Load model
   model = yolov5s(pretrained=True, score_thresh=0.45)
   model.eval()

   # Perform inference on an image file
   predictions = model.predict("bus.jpg")
   # Perform inference on a list of image files
   predictions = model.predict(["bus.jpg", "zidane.jpg"])

**从官方 yolov5 加载检查点**

支持从 YOLOv5 加载训练好的权重。请查看文档，了解与 yolov5 的 `share`_ 以及与yolov5的 `differ`_。

.. _share: https://zhiqwang.com/yolov5-rt-stack/notebooks/how-to-align-with-ultralytics-yolov5.html
.. _differ: https://zhiqwang.com/yolov5-rt-stack/notebooks/comparison-between-yolort-vs-yolov5.html

.. code:: python

   from yolort.models import YOLOv5
   from yolort.v5 import attempt_download

   # will downloaded from 'https://github.com/ultralytics/yolov5/releases/download/v6.0/yolov5n6.pt'
   model_path = "yolov5n6.pt"
   checkpoint_path = attempt_download(model_path)

   model = YOLOv5.load_from_yolov5(checkpoint_path, score_thresh=0.25)

   model.eval()
   img_path = "bus.jpg"
   predictions = model.predict(img_path)

用例和解决方案
=======================

.. toctree::
   :maxdepth: 2
   :titlesonly:
   :caption: Getting Started

   installation

.. toctree::
   :maxdepth: 2
   :titlesonly:
   :caption: Tutorials

   notebooks/inference-pytorch-export-libtorch
   notebooks/comparison-between-yolort-vs-yolov5
   notebooks/how-to-align-with-ultralytics-yolov5
   notebooks/anchor-label-assignment-visualization
   notebooks/model-graph-visualization

.. toctree::
   :maxdepth: 2
   :titlesonly:
   :caption: Deployment

   notebooks/export-onnx-inference-onnxruntime
   notebooks/onnx-graphsurgeon-inference-tensorrt
   notebooks/export-relay-inference-tvm

.. toctree::
   :maxdepth: 2
   :caption: API Reference

   models
   yolov5
