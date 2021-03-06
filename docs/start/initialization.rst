.. _initialization:
====================
Qlib Initialization
====================

.. currentmodule:: qlib


Initialize ``qlib`` Package
=========================

Please execute the following process to initialize ``Qlib``.

- Download and prepare the Data: execute the following command to download the stock data.
    .. code-block:: bash
    
        python scripts/get_data.py qlib_data_cn --target_dir ~/.qlib/qlib_data/cn_data

    Know more about how to use get_data.py, refer to `Raw Data  <../advanced/data.html#raw-data>`_.


- Run the initialization code: run the following code in python:

    .. code-block:: Python

        import qlib
        # region in [REG_CN, REG_US]
        from qlib.config import REG_CN
        mount_path = "~/.qlib/qlib_data/cn_data"  # target_dir
        qlib.init(mount_path=mount_path, region=REG_CN)
    


Parameters
===============================

In fact, in addition to'mount_path' and 'region', qlib.init has other parameters. The following are all the parameters of qlib.init:

- `mount_path`
    Type: str. The local directory where the data loaded by 'get_data.py' is stored.
- `region`
    Type: str, optional parameter(default: `qlib.config.REG_CN`/'cn'>). If region == `qlib.config.REG_CN`, 'qlib' will be initialized in US stock mode. If region == `qlib.config.REG_US`, 'qlib' will be initialized in A-share mode.
- `redis_host`
    Type: str, optional parameter(default: "127.0.0.1"), host of `redis`
- `redis_port`
    Type: int, optional parameter(default: 6379), port of `redis`

    .. note:: 
        
        The value of'region' should be consistent with the data stored in'mount_path'. Currently,'scripts/get_data.py' only supports downloading A-share data. If users need to use the US stock mode, they need to prepare their own US stock data and store it in'mount_path'.

    .. note::
        
        If redis connection failed with `redis_host` and `redis_port`, cache will not be used! Please refer to `Cache <../advanced/cache.rst>`_.


Api
==========

.. automodule:: mlib.base
    :members: