
# raw fluent-splunk logs collector

default td-agent config location & files

    bash@~$ ls -l /etc/td-agent/
    total 12
    drwxr-xr-x 2 root root 4096 Feb  7 18:58 plugin
    -rwxrwxrwx 1 root root  865 Jul 30 15:46 td-agent.conf
    -rw-r--r-- 1 root root 2640 Apr 13 14:07 td-agent.conf.bak

other tools that gets installed at the time of td-agent

    bash@~$ ls -l /usr/sbin/td-agent

    -rwxr-xr-x 1 root root 348 Feb  8 20:27 /usr/sbin/td-agent
    bash@~$ ls -l /usr/sbin/td-agent*
    -rwxr-xr-x 1 root root 348 Feb  8 20:27 /usr/sbin/td-agent
    -rwxr-xr-x 1 root root 177 Feb  8 20:27 /usr/sbin/td-agent-gem
    -rwxr-xr-x 1 root root 649 Feb  7 18:58 /usr/sbin/td-agent-ui


searching the installable plugins for our td-agent

    bash@~$ td-agent-gem search splunk
    *** REMOTE GEMS ***
    chef-handler-splunk (2.1.0)
    chef-handler-splunkstorm (1.2.0)
    chef_handler_splunk (0.1.0)
    embulk-input-splunk (0.2.2)
    fluent-plugin-azureeventhubs_splunk (0.0.1)
    fluent-plugin-splunk (0.0.1.1)
    fluent-plugin-splunk-enterprise (0.9.0)
    fluent-plugin-splunk-ex (1.0.2)
    fluent-plugin-splunk-hec (1.0.1)
    fluent-plugin-splunk-http-eventcollector (0.3.0)
    fluent-plugin-splunk-http-eventcollector-memb (0.0.1)
    fluent-plugin-splunk-http-eventcollector-test (0.3.0.1)
    fluent-plugin-splunk-parser (0.1.1)
    fluent-plugin-splunkapi (0.2.0)
    fluent-plugin-splunkapi-ssln (0.0.2)
    fluent-plugin-splunkhec (1.7)
    nagios-splunk (1.1.3)
    rsplunk (0.4.0)
    ruby-splunk (0.0.4)
    sensu-plugins-splunk (1.0.0)
    splunk-client (0.10.0)
    splunk-pickaxe (2.4.0)
    splunk-sdk-ruby (1.0.5)
    splunk_logger (0.0.3)
    splunker (0.0.3)
    splunkman (0.0.1)
    splunky (0.1.0)


    bash@~$ sudo td-agent-gem install fluent-plugin-splunk-http-eventcollector

# controls

    sudo service td-agent start

    sudo service td-agent status # will tell you status and location of td-agent logs

    sudo service td-agent stop

# for simple experiments

    td-agent # will pick from default td-agent etc config

    td-agent --help

# config file

    bash@tmp$ cat /etc/td-agent/td-agent.conf
    <source>
      @type tail
      path  /tmp/sampletest.log
      pos_file /tmp/sampletest.log.pos
      tag sampletest
      format json
    </source>

    <match **>
       type elasticsearch
       log_level info
       include_tag_key true
       host "XXX.XXX.XXX.XXX"
       port "9200"
       scheme "#{ENV['FLUENT_ELASTICSEARCH_SCHEME'] || 'http'}"
       reload_connections "#{ENV['FLUENT_ELASTICSEARCH_RELOAD_CONNECTIONS'] || 'true'}"
       logstash_prefix "#{ENV['FLUENT_ELASTICSEARCH_LOGSTASH_PREFIX'] || 'logstash'}"
       logstash_format true
       buffer_chunk_limit 2M
       buffer_queue_limit 32
       flush_interval 5s
       max_retry_wait 30
       disable_retry_limit
       num_threads 8
    </match>

    <match **>
       type splunk-http-eventcollector
       server mysplunkcloud.com:443
       protocol https
       token 000000-000-000-000-000000000
       auth admin:pass
       sourcetype fluentd
       format json
    </match>

# WARNING

> Remember to do ` sudo rm  /var/log/td-agent/td-agent.log` when doing with simple experiments. As user context changes when running as sudo or simple user, permission to edit log files will keep changing. This leads to collision of or inability to edit log.,
