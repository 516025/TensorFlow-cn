TensorFlow Installation
================

The most up-to-date installation method can be acquired through the official website (https://tensorflow.google.cn/install). TensorFlow supports multiple languages like Python, Java and Go and a variety of OS like Windows, OSX and Linux. We use Python in this handbook.

We provide both simple and full installation method for readers from different levels.

Simple Installation
^^^^^^^^^^^^^^^^^^^^^^
You are good to follow these steps if you only want to install TensorFlow on your personal computer without GPU or spending too much effort configuring the environment (taking Windows as an example):

- Download and install Python IDE `Anaconda <https://www.anaconda.com/download/>`_ (with Python Ver 3.6);
- Download and install Python IDE `PyCharm <http://www.jetbrains.com/pycharm/>`_ (Community version, students can apply for free Professional versions)
- Run ``Anaconda Prompt`` in Start Menu, enter and execute ``pip install tensorflow``.

And done.

Full Installation
^^^^^^^^^^^^^^^^^^^^
This part includes more details of installation (e.g. building the conda environment) and guidance of the GPU version of TensorFlow environment installation.

Environment configuration before installation
------------------------------------------------
Before installing TensorFlow, we need to set up a proper environment with the following steps:

1. Check if your computer has an NVIDIA graphics card and install the GPU version of TensorFlow in order to take advantage on its powerful capability of computation acceleration if so or just install CPU version if not so. To be more specific, the CUDA Capability of your graphics card that you can check on `NVIDIA official website <https://developer.nvidia.com/cuda-gpus/>`_ should not be less than 3.0.
2. Install Python environment. Anaconda is recommended. It is an open-source release version of Python that provides a full environment for scientific computation including common ones such as NumPy and SciPy or you can choose your favorite ones of course. Note that TensorFlow only supports Python Ver 3.X under Windows when we write this handbook.

   * You can choose to add the directory of Anaconda into the PATH (though not recommended by the installation wizard) that enables you to call all Anaconda commands under command line or powershell directly. You are always good to call them under the Anaconda Prompt that can be started in the Start Menu.

3. (For GPU version installation) Install the NVIDIA graphics driver, `CUDA Toolkit <https://developer.nvidia.com/cuda-downloads>`_ and `cuDNN <https://developer.nvidia.com/cudnn>`_. You should note that:

   * We recommend you install it through the following order: 1) latest NVIDIA graphics driver 2) CUDA (without overwriting the built-in driver when installing since the built-in ones may be out-of-date) 3) cuDNN;
   * There is a quite simple way to install drivers in Ubuntu. First click "Software & Updates" in "System Setting", then toggle on "Using NVIDIA binary driver" option in "Additional Drivers" and click "Apply Changes" for system to install NVIDIA drivers automatically or it won't be smooth for NVIDIA installation on Linux. You should disable the built-in graphics driver Nouveau and Secure Boot function of the motherboard. You can seek a more detailed guidance `here <https://www.linkedin.com/pulse/installing-nvidia-cuda-80-ubuntu-1604-linux-gpu-new-victor/>`_;
   * The version of CUDA Toolkit and cuDNN must agree with the requirements on TensorFlow official website which does not always require the latest version.
   * You have to copy the downloaded content of cuDNN to the installation directory of CUDA to complete cuDNN installation.

Install
----------------

These are the following steps of TensorFlow installation under Anaconda (taking Windows as example):

1. Create a conda environment named ``tensorflow``

::

    conda create -n tensorflow python=X.X # Substitute "X.X" with your own Python version, e.g. "3.6".

2. Activate the environment

::

    activate tensorflow

3. Use pip to install TensorFlow

Install CPU version
::

    pip install tensorflow

Install GPU version
::

    pip install tensorflow-gpu

You can also choose to install the Nightly version of TensorFlow if you want. This version may include some latest features compared to the official version (e.g. the Eager Execution mode that this handbook focuses on was only supported in the Nightly version before TensorFlow Ver 1.8) yet with some instability. You can do so by running ``pip install tf-nightly`` (CPU version) or ``pip install tf-nightly-gpu`` (GPU version) under a new virtual environment. If you are going to install GPU version, it may require higher versions of CUDA and cuDNN. Fortunately different versions of CUDA and cuDNN can coexist.

If it is slow to install through pip command in China, you may want to try `TensorFlow mirror on TUNA <https://mirrors.tuna.tsinghua.edu.cn/help/tensorflow/>`_.

First Program
^^^^^^^^^^^^^^^

We write a piece of code to verify installation.

Enter ``activate tensorflow`` under command line to enter the previously built conda environment with TensorFlow. Then enter ``python`` to enter Python environment. Input the following codes line by line:

.. code-block:: python

    import tensorflow as tf
    tf.enable_eager_execution()

    A = tf.constant([[1, 2], [3, 4]])
    B = tf.constant([[5, 6], [7, 8]])
    C = tf.matmul(A, B)

    print(C)

If the output is::

    tf.Tensor(
    [[19 22]
    [43 50]], shape=(2, 2), dtype=int32)

We can draw conclusions that TensorFlow was successfully installed. It's normal of the program to output some prompt messages when running.

Here we use Python. You can get Python tutorials on https://docs.python.org/3/tutorial/. From now on we assume that readers are familiar with the basics of Python. Relax, Python is easy to handle and advanced features of Python will be barely involved in TensorFlow. We recommend you to use `PyCharm <http://www.jetbrains.com/pycharm/>`_ as your Python IDE. If you are a student with a mailbox ended with .edu, you can apply for a free license here <http://www.jetbrains.com/student/>`_. You can always download PyCharm Community version whose main functions do not differ that much from the former if you do not meet the aforementioned criteria.

.. [#f1] The effect of GPU acceleration is relative to the GPU performance. It won't be satisfactory if you have a high performance CPU and a beginner level GPU where the acceleration rate will be like 1-2. However the acceleration rate may reach 10 or even higher under specific models if you have a powerful GPU (e.g. NVIDIA GeForce GTX 1080 Ti or NVIDIA GeForce TITAN Series are powerful graphics card types when this handbook was being written). Meanwhile, the acceleration rate is also influenced by the running task itself. The beginner level models of TensorFlow do not require too much performance as the CPU version is adequate. Thus you may determine if you will purchase a higher level graphics card to train faster after you have mastered the basics of TensorFlow.