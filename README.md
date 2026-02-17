Fluent Bit v2.2.2
* Copyright (C) 2015-2024 The Fluent Bit Authors
* Fluent Bit is a CNCF sub-project under the umbrella of Fluentd
* https://fluentbit.io

____________________
< Fluent Bit v2.2.2 >
 -------------------
          \
           \
            \          __---__
                    _-       /--______
               __--( /     \ )XXXXXXXXXXX\v.
             .-XXX(   O   O  )XXXXXXXXXXXXXXX-
            /XXX(       U     )        XXXXXXX\
          /XXXXX(              )--_  XXXXXXXXXXX\
         /XXXXX/ (      O     )   XXXXXX   \XXXXX\
         XXXXX/   /            XXXXXX   \__ \XXXXX
         XXXXXX__/          XXXXXX         \__---->
 ---___  XXX__/          XXXXXX      \__         /
   \-  --__/   ___/\  XXXXXX            /  ___--/=
    \-\    ___/    XXXXXX              '--- XXXXXX
       \-\/XXX\ XXXXXX                      /XXXXX
         \XXXXXXXXX   \                    /XXXXX/
          \XXXXXX      >                 _/XXXXX/
            \XXXXX--__/              __-- XXXX/
             -XXXXXXXX---------------  XXXXXX-
                \XXXXXXXXXXXXXXXXXXXXXXXXXX/
                  ""VXXXXXXXXXXXXXXXXXXV""

[2026/02/17 09:02:29] [ info] [fluent bit] version=2.2.2, commit=eeea396e88, pid=1
[2026/02/17 09:02:29] [ info] [storage] ver=1.5.1, type=memory, sync=normal, checksum=off, max_chunks_up=128
[2026/02/17 09:02:29] [ info] [cmetrics] version=0.6.6
[2026/02/17 09:02:29] [ info] [ctraces ] version=0.4.0
[2026/02/17 09:02:29] [ info] [input:tail:tail.0] initializing
[2026/02/17 09:02:29] [ info] [input:tail:tail.0] storage_strategy='memory' (memory only)
[2026/02/17 09:02:29] [ info] [filter:kubernetes:kubernetes.0] https=1 host=kubernetes.default.svc port=443
[2026/02/17 09:02:29] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 09:02:29] [ info] [filter:kubernetes:kubernetes.0] local POD info OK
[2026/02/17 09:02:29] [ info] [filter:kubernetes:kubernetes.0] testing connectivity with API server...
[2026/02/17 09:02:29] [ info] [filter:kubernetes:kubernetes.0] connectivity OK
[2026/02/17 09:02:29] [error] [config] loki: unknown configuration property 'lineformat'. The following properties are allowed: uri, tenant_id, tenant_id_key, labels, auto_kubernetes_labels, drop_single_key, label_keys, remove_keys, line_format, label_map_path, http_user, http_passwd, bearer_token, header, and compress.
[2026/02/17 09:02:29] [error] [lib] backend failed
[2026/02/17 09:02:29] [ help] try the command: /fluent-bit/bin/fluent-bit -o loki -h

[2026/02/17 09:02:29] [error] [engine] output initialization failed
[2026/02/17 09:02:30] [ info] [input] pausing tail.0
