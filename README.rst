WAF-Brain
=========

**WAF-Brain: the clever and efficient Firewall for the Web**

+----------------+-------------------------------------------------------+
|Project site    | https://github.com/bbva/waf-brain                     |
+----------------+-------------------------------------------------------+
|Issues          | https://github.com/bbva/waf-brain/issues/             |
+----------------+-------------------------------------------------------+
|Latest Version  | 1.0.0-alpha                                           |
+----------------+-------------------------------------------------------+
|Python versions | 3.6 or above                                          |
+----------------+-------------------------------------------------------+
|License         | Apache 2                                              |
+----------------+-------------------------------------------------------+


Overview
========

This project was born to try to create a WAF(Web Application Firewall) with Deep Learning way.

Link to the article

This library allow:

- Launch a web-server with a Machine Learning model for stop SQL Injection Attacks
- Use your custom machine-learning model.

How install
-----------
.. highlight:: bash
pip install -e .

How use
-------
1. Launch the waf server and the application server
---------------------------------------------------
`This is a example repo for launch modsecurity server with express server <https://github.com/theonemule/docker-waf>`

2. Launch waf-benchmark over the waf server address
---------------------------------------------------
You have multiples kind of benchmarking

- For launch a server in **test mode** with our model on **localhost**, and collect partial results, launch this command

.. highlight:: bash
python -m waf_brain -T --dump-file logs.txt -l 0.0.0.0

- Use **custom model**

.. highlight:: bash
python -m waf_brain -T --dump-file logs.txt -l 0.0.0.0 -M custom_model.h5

**NOTE**: Default port 8000

Research
========
**Contribute to the project**, get our Notebooks and datasets for train new models.

For **more info** `go to this link: <https://github.com/BBVA/waf-brain/blob/master/research/RESEARCH.md>`

Other Options
=============

usage: __main__.py [-h] [-v] [--backend-timeout BACKEND_TIMEOUT]
                   [-A PROTECTED_URL] [-l LISTEN] [-p PORT] [-b BACKLOG]
                   [--blocking-mode] [--blocking-threshold BLOCKING_THRESHOLD]
                   [-M MODEL] [-T] [--dump-file DUMP_FILE] [-a]

WAF-brain: the clever and efficient Firewall for the Web

optional arguments:
  -h, --help            show this help message and exit
  -v                    log level

Server Options:
  --backend-timeout BACKEND_TIMEOUT
                        timeout to connect to the backend
  -A PROTECTED_URL, --protected-url PROTECTED_URL
                        address service to protect with the WAF
  -l LISTEN, --listen LISTEN
                        listen address. Default: 127.0.0.1
  -p PORT, --port PORT  listen port for service. Default: 8000
  -b BACKLOG, --backlog BACKLOG
                        maximum concurrent connections

WAF Behavior:
  --blocking-mode       enables active blocking of dangerous request
  --blocking-threshold BLOCKING_THRESHOLD
                        if the dangerous levels is upper this number, and
                        blocking mode is enabled, WAF will block a request
  -M MODEL, --model MODEL
                        model used for WAF

Enable testing mode:
  -T, --enable-testing  enable testing mode
  --dump-file DUMP_FILE
                        dump file to track each request
  -a, --access-log      enable access log for each request


