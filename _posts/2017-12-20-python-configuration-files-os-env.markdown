---
author: guidedmissile
comments: true
date: 2017-12-20 14:32:13+00:00
excerpt: Python Configuration files that uses OS variables.
layout: post
link: https://inlovewithcode.wordpress.com/2017/12/20/python-configuration-files-os-env/
slug: python-configuration-files-os-env
title: Python Configuration Files - OS ENV
wordpress_id: 2595
categories:
- Python
---

# Python Configuraton Files





## Configuration w.r.t System Env Variable



In this example, we shall explore how set a configuration variable that uses env values



##### Define Local variable



[code lang="bash"]
bash3.2$ export THIS_IS_A_TEST_VARIABLE='/TMP/A/B/123'
[/code]



##### Define App Config File



Check config file

[code lang="bash"]
bash3.2$ cat config.ini
[/code]

Output

[code lang="python"]
[DEFAULT]
test_home=%(THIS_IS_A_TEST_VARIABLE)s

[test]
test_1=%(test_home)s/foo.csv
test_2=%(THIS_IS_A_TEST_VARIABLE)s/bar.csv
[/code]



##### Define Python Config parser file



[code lang="bash"]
bash3.2$ cat env_config_test.py
[/code]

Content of env_config_test files.

[code lang="python"]
import os
from ConfigParser import SafeConfigParser

config = SafeConfigParser(os.environ)
config.readfp(open('config.ini'))

print(config.get('test', 'test_1'))
[/code]

Test

[code lang="bash"]
bash3.2$ python env_config_test.py                                                                                                                   
/TMP/A/B/123/foo.csv
[/code]

As you can see, this above config value is used for `test_2` config variable.
