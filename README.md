[root@fcsitgateway SIT-Microservice]# kubectl get pods -n logging -o wide --kubeconfig h06vkssitcbopscls.conf | grep fluent
fluent-bit-4xz9z        1/1     Running   0          19h   192.168.2.195   h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-sb28w   <none>           <none>
fluent-bit-fxvvw        1/1     Running   0          19h   192.168.4.227   h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-bc5v4   <none>           <none>
fluent-bit-nnl6z        1/1     Running   0          19h   192.168.1.166   h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-xk62q   <none>           <none>
[root@fcsitgateway SIT-Microservice]# kubectl logs fluent-bit-4xz9z -n logging --kubeconfig h06vkssitcbopscls.conf
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

[2026/02/17 10:03:14] [ info] [fluent bit] version=2.2.2, commit=eeea396e88, pid=1
[2026/02/17 10:03:14] [ info] [storage] ver=1.5.1, type=memory, sync=normal, checksum=off, max_chunks_up=128
[2026/02/17 10:03:14] [ info] [cmetrics] version=0.6.6
[2026/02/17 10:03:14] [ info] [ctraces ] version=0.4.0
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] initializing
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] storage_strategy='memory' (memory only)
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] https=1 host=kubernetes.default.svc port=443
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] local POD info OK
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] testing connectivity with API server...
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] connectivity OK
[2026/02/17 10:03:14] [ info] [output:loki:loki.0] configured, hostname=loki.logging.svc.cluster.local:3100
[2026/02/17 10:03:14] [ info] [sp] stream processor started
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917710 watch_fd=1 name=/var/log/containers/antrea-agent-2x8gc_kube-system_antrea-agent-tweaker-fbe5c401488f8907be5a5aac811e2688b0d47682fd1472400feb365d86df022a.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917720 watch_fd=2 name=/var/log/containers/antrea-agent-2x8gc_kube-system_antrea-ovs-a3959ad34ab27588e2068f11e0f51264cb2d111816e39be8ac492e540e4660d6.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917713 watch_fd=3 name=/var/log/containers/antrea-agent-2x8gc_kube-system_install-cni-de7b4f744aaa04a56357c3972e6517a2049e5c6935f0e30902c87097b0b9d32b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917906 watch_fd=4 name=/var/log/containers/cbs-app-092d299be5dc2a60-driver_cbops_spark-kubernetes-driver-8e63c47962c34c751ae06a886aa633b1ed5133ae8c118adcb5486b98ce7ad1af.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917892 watch_fd=5 name=/var/log/containers/cbs-app-0adc689be5aa0ff0-driver_cbops_spark-kubernetes-driver-8ea4fb7367bbb17d3f8a442752784faa8334feda06773dbf98c089f10b094acf.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917902 watch_fd=6 name=/var/log/containers/cbs-app-0d99699be5cb494d-driver_cbops_spark-kubernetes-driver-b36310bc5efc4ae71f5e59141e2335993ad45956d1fc1aaf403d96004a5f4674.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917944 watch_fd=7 name=/var/log/containers/cbs-app-71e5919bf3cc8c4d-driver_cbops_spark-kubernetes-driver-b2016fd0e30f1198d212a49fa4bed3e7b0f6d7a27a07623c35471a5a68d2981a.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917914 watch_fd=8 name=/var/log/containers/cbs-app-cbcb8f9be6396624-driver_cbops_spark-kubernetes-driver-8240a14dc95e347fb79af0e333433399f0e424552301de95cd4cd0832de6d234.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917910 watch_fd=9 name=/var/log/containers/cbs-app-d667d59be60a14cc-driver_cbops_spark-kubernetes-driver-db23a3c9d1f19aef1441da3bfb453a339eab0c3e604630f3174591bf43f53ad1.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917898 watch_fd=10 name=/var/log/containers/cbs-app-f18f949be5a1cf90-driver_cbops_spark-kubernetes-driver-b62d487f6d27afe8717c160ba763a6bc7d30ea2f34aeadc4ed4a18b10e47673b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917894 watch_fd=11 name=/var/log/containers/cbs-app-fe14439be58d00e6-driver_cbops_spark-kubernetes-driver-316c2a53fcb918b148f9437c54de8df193f36b65df4dc8288d1d78339b40a167.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917744 watch_fd=12 name=/var/log/containers/cert-manager-cainjector-69896f7559-2r5rt_cert-manager_cert-manager-cainjector-8e8196ef3517d1d31918146ef3dec6abc19302c9562d8b6348aca25352d48a5b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917863 watch_fd=13 name=/var/log/containers/common-master-deployment-7b7557cf4f-fgqv8_cbops_common-master-container-44309829c8d2b54397993f800e8553938ecaa99703dcf24c0605cd44eead9e51.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917848 watch_fd=14 name=/var/log/containers/common-request-deployment-6b95fbdb56-q8mb9_cbops_common-request-container-a3a8e6f4a44b32e7377f1aff0934d97714bcaf9aeba36746493f56f6477bc1d7.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917858 watch_fd=15 name=/var/log/containers/delete-oracle-connector-cr5jb_cbops_delete-f1a07a2e635e3423fc11a1c93c7bd6cf7790a14c18f2d90939a3159c512b69e6.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917872 watch_fd=16 name=/var/log/containers/difference-app-143b609bea47f8fd-driver_cbops_spark-kubernetes-driver-6414f1bb214ba19f7db32f53096fc46c15ad672eece0ac175e154170fffe96cd.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917692 watch_fd=17 name=/var/log/containers/docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-sb28w_kube-system_docker-registry-d36fec07401992616ade0aadc87771b946d6848899cfa65d2f9ba7e6e24f04c6.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917930 watch_fd=18 name=/var/log/containers/glif-app-7dc20a9be91ad791-driver_cbops_spark-kubernetes-driver-6ad3d74660776aa7d400edc0f0de9148710783557c4edcf4f300e44af09679f0.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917917 watch_fd=19 name=/var/log/containers/glif-app-93442c9be651089d-driver_cbops_spark-kubernetes-driver-2c39f50468a6506563f04c7c037c97e930ef26c4143c11c92e68c3cb2a63eb64.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917925 watch_fd=20 name=/var/log/containers/glif-app-cdb3fd9be65f17e9-driver_cbops_spark-kubernetes-driver-45f094b33a078e18d06c38ed7bcc2e44baf12df91d0c4885e6e007835f876b98.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917923 watch_fd=21 name=/var/log/containers/glif-app-de3d249be913fd4e-driver_cbops_spark-kubernetes-driver-bfac6437229ae08b9757d90215e333168ec6341ddb47610172ca61bdbb50fc3b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917861 watch_fd=22 name=/var/log/containers/kafka-0_cbops_fix-kafka-permissions-f2a504a4266637ed035d674ac6a26b8a0c372ebda82a06957723355b405f704a.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917788 watch_fd=23 name=/var/log/containers/kafka-0_cbops_kafka-ddb672d1d73be1fcf2d508827675f49e21b7729471c04688a741a3de5fec8ff5.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917934 watch_fd=24 name=/var/log/containers/kafkahit-lg5vf_cbops_kafkacheck-f24a4ef661d2d14d1d3273d11a4b9b5cd215fea8dc74af9433a8a491783a2cea.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917966 watch_fd=25 name=/var/log/containers/kong-6dd5746646-wttch_kong-system_kong-b8544b6d451defe3a519fc0d1b1cbb39b13196477883459f33ac8a5179f08dde.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917699 watch_fd=26 name=/var/log/containers/kube-proxy-22gdj_kube-system_kube-proxy-ee12cc3298df3db57e40878b45329e90ca75b88f8aa3e7658f82e3697ff189d1.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917939 watch_fd=27 name=/var/log/containers/loki-6f676bfbc7-j7hcl_logging_loki-74f80c497c3515edbbd14249d7c0c72cb79b4e6a12296968cb93964f71f5c02d.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917818 watch_fd=28 name=/var/log/containers/postgres-db-7b865dd6fc-gcnv9_cbops_postgres-db-a0974c0dbcd1ab6cfec3e394399b6f60c6461aa760e66d1f71558ec470ba0d9d.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917832 watch_fd=29 name=/var/log/containers/process-status-deployment-7dddfbcddd-sldjx_cbops_process-status-container-e4a2a3dc0afc34cafdb11f22013c20a715106352ef8fcc8938f6358d4f69658b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917887 watch_fd=30 name=/var/log/containers/redis-deployment-59ddbb9b85-7bzwg_cbops_redis-container-5f63ccfb56efcec0bb52e3f676360b4618158cca74a1f5bf161ed9c16f701fb8.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917871 watch_fd=31 name=/var/log/containers/register-oracle-connector-b2qps_cbops_register-fb93392367e57212d44991000c552e61bafef933ab4f29aa3f5cee4811bcbda6.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917933 watch_fd=32 name=/var/log/containers/report-deployment-6846f77ff6-4l7fc_cbops_report-container-33184fdf3432b9a7c5561cbcbfe584570991aab09e7cc68a1addbde751abffa0.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917823 watch_fd=33 name=/var/log/containers/report-deployment-6846f77ff6-4l7fc_cbops_report-container-bee5d314cf518d95b56c404716d8bb08cb492eb6cb98f58e8be4d3994a57a0db.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917851 watch_fd=34 name=/var/log/containers/template-config-deployment-77545dd89d-5khgd_cbops_template-config-container-842eabbe2e905a08de68b19b35a056ae817eceed4a3572a4bc7696814ea2b234.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917733 watch_fd=35 name=/var/log/containers/vsphere-csi-node-6p769_vmware-system-csi_liveness-probe-6749c5f5d3b6ff134581db6b055e320a5e00baecbe9002c2872ba14fa37c3247.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917702 watch_fd=36 name=/var/log/containers/vsphere-csi-node-6p769_vmware-system-csi_node-driver-registrar-c671e7f69f1755b8086816f66c37f6d81e971a4a3f04c82a20c8662d2ab5a9b9.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917819 watch_fd=37 name=/var/log/containers/vsphere-csi-node-6p769_vmware-system-csi_vsphere-csi-node-5d53693280ee6229b9b0ee60abb6ad1b84d86d0bf6b1cab94a703f9a4cedd46a.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917716 watch_fd=38 name=/var/log/containers/antrea-agent-2x8gc_kube-system_antrea-agent-87aa634d2ecfe4c302fdf2289d1f2594afe6cf1ce45151147e0ff1e65d0a45d5.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917753 watch_fd=39 name=/var/log/containers/fluent-bit-4xz9z_logging_fluent-bit-d47544ec55a216c529c3b9d317334880a17e11b3e8b5a0d1fd3c1f25d7c86928.log
[2026/02/17 10:03:34] [error] [output:loki:loki.0] loki.logging.svc.cluster.local:3100, HTTP status=500
empty ring

[2026/02/17 10:03:34] [ warn] [engine] failed to flush chunk '1-1771322613.385241067.flb', retry in 6 seconds: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 10:03:34] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917785 watch_fd=40 name=/var/log/containers/loki-6f676bfbc7-986kw_logging_loki-d57fa8cf736233683da338a39afe3024dbf68b3534b8616b9159564e4c8ddba4.log
[2026/02/17 10:03:34] [error] [output:loki:loki.0] loki.logging.svc.cluster.local:3100, HTTP status=500
empty ring

[2026/02/17 10:03:34] [ warn] [engine] failed to flush chunk '1-1771322613.389446620.flb', retry in 7 seconds: task_id=1, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 10:03:35] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917939 watch_fd=27
[2026/02/17 10:03:40] [ info] [engine] flush chunk '1-1771322613.385241067.flb' succeeded at retry 1: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 10:03:41] [ info] [engine] flush chunk '1-1771322613.389446620.flb' succeeded at retry 1: task_id=1, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 10:46:13] [ info] [input:tail:tail.0] inode=917785 handle rotation(): /var/log/containers/loki-6f676bfbc7-986kw_logging_loki-d57fa8cf736233683da338a39afe3024dbf68b3534b8616b9159564e4c8ddba4.log => /var/log/pods/logging_loki-6f676bfbc7-986kw_f00468c4-1e95-41a4-986a-b15de0207c95/loki/0.log.20260217-104613
[2026/02/17 10:46:13] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917785 watch_fd=40
[2026/02/17 10:46:13] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917785 watch_fd=41 name=/var/log/pods/logging_loki-6f676bfbc7-986kw_f00468c4-1e95-41a4-986a-b15de0207c95/loki/0.log.20260217-104613
[2026/02/17 10:46:13] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917749 watch_fd=42 name=/var/log/containers/loki-6f676bfbc7-986kw_logging_loki-d57fa8cf736233683da338a39afe3024dbf68b3534b8616b9159564e4c8ddba4.log
[2026/02/17 10:46:44] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917785 watch_fd=41
[2026/02/17 11:11:02] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 11:11:02] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917920 watch_fd=43 name=/var/log/containers/react-app-deployment-65b658dd59-fhjtz_cbops_reactive-container-e1c8080d966b4259636a17a6f3cdb3e35ccf036e2818954e2e1e1d98685ba9a7.log
[2026/02/17 12:32:04] [ info] [input:tail:tail.0] inode=917749 handle rotation(): /var/log/containers/loki-6f676bfbc7-986kw_logging_loki-d57fa8cf736233683da338a39afe3024dbf68b3534b8616b9159564e4c8ddba4.log => /var/log/pods/logging_loki-6f676bfbc7-986kw_f00468c4-1e95-41a4-986a-b15de0207c95/loki/0.log.20260217-123204
[2026/02/17 12:32:04] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917749 watch_fd=42
[2026/02/17 12:32:04] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917749 watch_fd=44 name=/var/log/pods/logging_loki-6f676bfbc7-986kw_f00468c4-1e95-41a4-986a-b15de0207c95/loki/0.log.20260217-123204
[2026/02/17 12:32:05] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917785 watch_fd=45 name=/var/log/containers/loki-6f676bfbc7-986kw_logging_loki-d57fa8cf736233683da338a39afe3024dbf68b3534b8616b9159564e4c8ddba4.log
[2026/02/17 12:32:44] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917749 watch_fd=44
[2026/02/17 12:43:19] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 20:53:29] [ info] [input:tail:tail.0] inode=917785 handle rotation(): /var/log/containers/loki-6f676bfbc7-986kw_logging_loki-d57fa8cf736233683da338a39afe3024dbf68b3534b8616b9159564e4c8ddba4.log => /var/log/pods/logging_loki-6f676bfbc7-986kw_f00468c4-1e95-41a4-986a-b15de0207c95/loki/0.log.20260217-205329
[2026/02/17 20:53:29] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917785 watch_fd=45
[2026/02/17 20:53:29] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917785 watch_fd=46 name=/var/log/pods/logging_loki-6f676bfbc7-986kw_f00468c4-1e95-41a4-986a-b15de0207c95/loki/0.log.20260217-205329
[2026/02/17 20:53:29] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917749 watch_fd=47 name=/var/log/containers/loki-6f676bfbc7-986kw_logging_loki-d57fa8cf736233683da338a39afe3024dbf68b3534b8616b9159564e4c8ddba4.log
[2026/02/17 20:54:14] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917785 watch_fd=46
[root@fcsitgateway SIT-Microservice]# kubectl logs fluent-bit-fxvvw -n logging --kubeconfig h06vkssitcbopscls.conf
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

[2026/02/17 10:03:14] [ info] [fluent bit] version=2.2.2, commit=eeea396e88, pid=1
[2026/02/17 10:03:14] [ info] [storage] ver=1.5.1, type=memory, sync=normal, checksum=off, max_chunks_up=128
[2026/02/17 10:03:14] [ info] [cmetrics] version=0.6.6
[2026/02/17 10:03:14] [ info] [ctraces ] version=0.4.0
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] initializing
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] storage_strategy='memory' (memory only)
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] https=1 host=kubernetes.default.svc port=443
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] local POD info OK
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] testing connectivity with API server...
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] connectivity OK
[2026/02/17 10:03:14] [ info] [output:loki:loki.0] configured, hostname=loki.logging.svc.cluster.local:3100
[2026/02/17 10:03:14] [ info] [sp] stream processor started
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917790 watch_fd=1 name=/var/log/containers/ako-0_avi-system_ako-2c9a98f9113a2dde0b34675b75758c34947edfaa965e4eae03af9c5e452afdf2.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917710 watch_fd=2 name=/var/log/containers/antrea-agent-k7dm2_kube-system_antrea-agent-tweaker-cdf5ddccdfe7c23998c86618d2ee84b5d642ff0014b8911a951b304914069721.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917720 watch_fd=3 name=/var/log/containers/antrea-agent-k7dm2_kube-system_antrea-ovs-a68990dce37a1e64f5654ad8695f8907e3cfdc669f09a66e5073b0e61a390304.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917713 watch_fd=4 name=/var/log/containers/antrea-agent-k7dm2_kube-system_install-cni-65188e139d826426d2659280e5d0d5a5a2d72fe9ab4537fa5b39edbb3e4c5996.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917938 watch_fd=5 name=/var/log/containers/cbs-app-203ff79bf3cf9590-driver_cbops_spark-kubernetes-driver-758c86aa75ea8a230bf841afe4b9e8b7401603fc62d17b65ebf96b17e0fd8d4a.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917887 watch_fd=6 name=/var/log/containers/cbs-app-fc0a6b9be5c79988-driver_cbops_spark-kubernetes-driver-2d0d837ea45372a19813a0ec0310687daeba1485acf2c123ad13d67ab3edd49a.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917744 watch_fd=7 name=/var/log/containers/cert-manager-74f66c9bf8-84786_cert-manager_cert-manager-controller-42683ced167ba4eb64762b3b3e5868fe623e935b94dc87c63a45792ce5d242a6.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917830 watch_fd=8 name=/var/log/containers/dashboard-deployment-5469bc4df5-fnjbk_cbops_dashboard-container-0c46621a74c12ab33b1ae72d3668b9c9e81620cb22333313270d8a6bc099aa43.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917874 watch_fd=9 name=/var/log/containers/delta-table-register-zrkht_cbops_spark-thrift-st-15b8d66fff655815d64c6269a47188d62e8025d809d92c3c7fa5ea37f747e7a5.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917926 watch_fd=10 name=/var/log/containers/difference-app-f9d8ae9bea404bd7-driver_cbops_spark-kubernetes-driver-97c38c2783dc6a6e65792a9f51dff0236b2bf1184d27454239335aede4b669f3.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917692 watch_fd=11 name=/var/log/containers/docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-bc5v4_kube-system_docker-registry-198e02f49537c480989f0df7179b8194b05f657f888e7988781de51505edc5bc.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917934 watch_fd=12 name=/var/log/containers/glcheck1-vtght_cbops_glcheck1-a153648a94ed54e530923b5fd135f4f3661c29ce3d123e06c48ad6e46efbd77f.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917922 watch_fd=13 name=/var/log/containers/glif-app-1aeb5e9be6438352-driver_cbops_spark-kubernetes-driver-014ab071b8c428057738e5cba7942a8c030d55ffc2fe05eff0f1d31a97e9a5a7.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917918 watch_fd=14 name=/var/log/containers/glif-app-641a569be9bede3e-driver_cbops_spark-kubernetes-driver-bd8a94c818fc249c14e8230759c7b0b063f3eb973ce2a7f2f42c71c325dcc966.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917913 watch_fd=15 name=/var/log/containers/glif-app-6658f39be9634fb3-driver_cbops_spark-kubernetes-driver-d212a925bb562e944e7e515acac88b3dab1382d52424584a0c19063c8ca71992.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917931 watch_fd=16 name=/var/log/containers/glif-app-7222479be64b238b-driver_cbops_spark-kubernetes-driver-d3d5d760cc104de0519d98db554f1a429d9d49008e5d089ef93ba80a503c6f5a.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917912 watch_fd=17 name=/var/log/containers/glif-app-8f386c9be6649f83-driver_cbops_spark-kubernetes-driver-2f77fdae4830b9f3430cb4ec4a69f7de930fd72ceccd5ec0f4f0a08431980854.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917944 watch_fd=18 name=/var/log/containers/glif-app-9a90a19bf033b1c2-driver_cbops_spark-kubernetes-driver-61fd7d153a72e9f8bad434ee1043afc64505c3f38afba8f53082858907dedb9b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917905 watch_fd=19 name=/var/log/containers/glif-app-bcf28c9be5ea845e-driver_cbops_spark-kubernetes-driver-02a0cdd98bae58f165eb7ee1adba407b1b1293f87604eac7922c3f976d6c3a91.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917899 watch_fd=20 name=/var/log/containers/glif-app-c950879be659f16d-driver_cbops_spark-kubernetes-driver-7b81fc0b0bd79bfc0f5a770bedff62b7a63c0607793624c6ae78c81dfec282cd.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917973 watch_fd=21 name=/var/log/containers/grafana-864f87c5c4-xkswq_cbops_grafana-2df089120046eb4a87ca88f9312e4654f57dc80e218a5fdf52c89fbda2c76274.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917873 watch_fd=22 name=/var/log/containers/hive-schematool-init-nnd98_cbops_schematool-39f8a160594ecec92f4d0d351540f4c026de271f6627e48d10a66f3ed9f2fd42.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917855 watch_fd=23 name=/var/log/containers/hive-schematool-init-rb6wv_cbops_schematool-51a103591906a56cb9c4b2c1f159b94dccfe1e976bf82ac5beb3c1fffc0e4396.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917859 watch_fd=24 name=/var/log/containers/hive-schematool-init-vs2wb_cbops_schematool-f798e26874bd913faf34b7fe3a31905ba51109cf7c0ff5d5c2f3333fe3cbc739.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917844 watch_fd=25 name=/var/log/containers/hive-schematool-init-wwvmh_cbops_schematool-3231b4ce5287d85af706fe85fa2ff7cadd5eef9598e0f714b0ddff8fd39cf015.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917961 watch_fd=26 name=/var/log/containers/kong-6dd5746646-rfb6v_kong-system_kong-575e482c561d6b9d20a7316c1077a09d61f19e0a12010ddd7873f7e167ca1cc1.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917948 watch_fd=27 name=/var/log/containers/kong-ingress-controller-7659c56b89-j47l5_kong-system_controller-890080f65e8d6c0640fbcbcd44006f7111187a5360be578d36168ffc65a3f63b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917699 watch_fd=28 name=/var/log/containers/kube-proxy-n9gkd_kube-system_kube-proxy-82046c7548f69fd998e8ad4fee7cb15273f47c1ee4bd8056c25f645fd6d17430.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917825 watch_fd=29 name=/var/log/containers/login-deployment-59cb59df5c-mnz77_cbops_login-backend-container-31fd013516f01aa16c13317a1dc8e69a9af418faeeb2913320c8584b5993f6e6.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917955 watch_fd=30 name=/var/log/containers/react-app-deployment-686d77cf76-ngp2p_cbops_reactive-container-700f5c164163108cd02cdfa106f6316997cfddf1dab1b00fe54ab8dcebaaecf4.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917840 watch_fd=31 name=/var/log/containers/transactions-deployment-b658c746b-qtv29_cbops_transactions-container-6cb08e5f742dd492caf974ae4f135e5f2df6d20608f0dac0b9f7ffb458b320a6.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917894 watch_fd=32 name=/var/log/containers/user-deployment-5675849454-wbrw6_cbops_user-container-1c2703900d0d0707c01679f503be986ddfd0fbdd172d055f40756f2760f524e1.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917732 watch_fd=33 name=/var/log/containers/vsphere-csi-node-jss4t_vmware-system-csi_liveness-probe-b980e05961ce99c24a07794eaaea6fda90e1917931d63b8c911cbbb36b1c6d6b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917702 watch_fd=34 name=/var/log/containers/vsphere-csi-node-jss4t_vmware-system-csi_node-driver-registrar-39854a5689afa750d9108f480e45dd8a2fb093b8c838bcd751ed190c5dc20027.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917729 watch_fd=35 name=/var/log/containers/vsphere-csi-node-jss4t_vmware-system-csi_vsphere-csi-node-ac62c4ea3a42ce8aed2ce5ad15b74fb9dd67fc093303f0a8c9df7a831581ec1f.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917808 watch_fd=36 name=/var/log/containers/ako-0_avi-system_ako-4d4ec8a39ba2edbcfba83077e3560e5e41d4b0759daaf70722d58dbdf35868e4.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917716 watch_fd=37 name=/var/log/containers/antrea-agent-k7dm2_kube-system_antrea-agent-f9c120ccf21ce4af08ee75c5308e1a2d3896d93eb13b3301b97176f3f8f8f047.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917805 watch_fd=38 name=/var/log/containers/connect-c87c7c494-wc2ml_cbops_connect-fe52a22425501d10751317a4559c4c4e022309276dfe8259131ae18fec4e8e0c.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917750 watch_fd=39 name=/var/log/containers/fluent-bit-fxvvw_logging_fluent-bit-7a636e36c235460c5320f7d5b9a8ec30190b7054246ac55a1e72865dae1f9c97.log
[2026/02/17 10:03:34] [error] [output:loki:loki.0] loki.logging.svc.cluster.local:3100, HTTP status=500
empty ring

[2026/02/17 10:03:34] [error] [output:loki:loki.0] loki.logging.svc.cluster.local:3100, HTTP status=500
empty ring

[2026/02/17 10:03:34] [ warn] [engine] failed to flush chunk '1-1771322613.372670605.flb', retry in 6 seconds: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 10:03:34] [ warn] [engine] failed to flush chunk '1-1771322613.541404798.flb', retry in 7 seconds: task_id=1, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 10:03:40] [ info] [engine] flush chunk '1-1771322613.372670605.flb' succeeded at retry 1: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 10:03:41] [ info] [engine] flush chunk '1-1771322613.541404798.flb' succeeded at retry 1: task_id=1, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 10:46:29] [ info] [input:tail:tail.0] inode=917973 handle rotation(): /var/log/containers/grafana-864f87c5c4-xkswq_cbops_grafana-2df089120046eb4a87ca88f9312e4654f57dc80e218a5fdf52c89fbda2c76274.log => /var/log/pods/cbops_grafana-864f87c5c4-xkswq_0173e724-be79-42d6-85f6-1c675a6a264a/grafana/0.log.20260217-104629
[2026/02/17 10:46:29] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917973 watch_fd=21
[2026/02/17 10:46:29] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917973 watch_fd=40 name=/var/log/pods/cbops_grafana-864f87c5c4-xkswq_0173e724-be79-42d6-85f6-1c675a6a264a/grafana/0.log.20260217-104629
[2026/02/17 10:46:30] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917749 watch_fd=41 name=/var/log/containers/grafana-864f87c5c4-xkswq_cbops_grafana-2df089120046eb4a87ca88f9312e4654f57dc80e218a5fdf52c89fbda2c76274.log
[2026/02/17 10:47:14] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917973 watch_fd=40
[2026/02/17 11:11:02] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917955 watch_fd=30
[2026/02/17 11:57:43] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 11:57:43] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 11:57:43] [ warn] [engine] failed to flush chunk '1-1771329453.929241883.flb', retry in 7 seconds: task_id=2, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:50] [ info] [engine] flush chunk '1-1771329453.929241883.flb' succeeded at retry 1: task_id=2, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:51] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917790 watch_fd=1
[2026/02/17 11:57:52] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917746 watch_fd=42 name=/var/log/containers/ako-0_avi-system_ako-4030adf740111fa99382e4ec3865a9d5d84063d67f330e033566905794db2cd6.log
[2026/02/17 12:50:45] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917790 watch_fd=43 name=/var/log/containers/report-builder-deployment-6d6c8568b8-tt7g5_cbops_report-builder-container-885bd705edb7d2988aa1afdf0d3d200d169057809820a71ea2c50e6680aff31c.log
[2026/02/17 12:50:45] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 12:51:32] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917864 watch_fd=44 name=/var/log/containers/report-builder-deployment-6b6f59fb57-ntxtl_cbops_report-builder-container-ee22ec90f79dc49c94e325a86f20f3055c1bf5c8297105311411a1dccebb74d9.log
[2026/02/17 12:51:33] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917790 watch_fd=43
[2026/02/17 17:35:37] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917808 watch_fd=36
[2026/02/17 17:35:38] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917761 watch_fd=45 name=/var/log/containers/ako-0_avi-system_ako-332821c3bd0ee1fec679d6fefa47dd9d91ce4e41a94d61634abac2b29ab07c26.log
[root@fcsitgateway SIT-Microservice]# kubectl logs fluent-bit-nnl6z -n logging --kubeconfig h06vkssitcbopscls.conf
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

[2026/02/17 10:03:14] [ info] [fluent bit] version=2.2.2, commit=eeea396e88, pid=1
[2026/02/17 10:03:14] [ info] [storage] ver=1.5.1, type=memory, sync=normal, checksum=off, max_chunks_up=128
[2026/02/17 10:03:14] [ info] [cmetrics] version=0.6.6
[2026/02/17 10:03:14] [ info] [ctraces ] version=0.4.0
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] initializing
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] storage_strategy='memory' (memory only)
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] https=1 host=kubernetes.default.svc port=443
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] local POD info OK
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] testing connectivity with API server...
[2026/02/17 10:03:14] [ info] [filter:kubernetes:kubernetes.0] connectivity OK
[2026/02/17 10:03:14] [ info] [output:loki:loki.0] configured, hostname=loki.logging.svc.cluster.local:3100
[2026/02/17 10:03:14] [ info] [sp] stream processor started
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917702 watch_fd=1 name=/var/log/containers/antrea-agent-jtf58_kube-system_antrea-agent-tweaker-6b4506ca26fed85c3d56671afac2aec297810a85e870be0520eb32ff9bb1291b.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917720 watch_fd=2 name=/var/log/containers/antrea-agent-jtf58_kube-system_antrea-ovs-4d7cd2c3b34e28f0e09480e823738b991e1f56b7bd7e8323c6569640f3bc9b18.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917713 watch_fd=3 name=/var/log/containers/antrea-agent-jtf58_kube-system_install-cni-7e75b1093ca83b526be479f01da80c92fa96cbfb8f90ea1c34bfb079872d1615.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917744 watch_fd=4 name=/var/log/containers/cert-manager-webhook-6d9c4fd5b8-stbsf_cert-manager_cert-manager-webhook-06d3f4b63dab88bf2d1beee468b8fe1e062590bfe7c37a4202ce3b5a7b5ff4cf.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917692 watch_fd=5 name=/var/log/containers/docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-xk62q_kube-system_docker-registry-eede5e11cc6b3ac52c07bc7107cc7db46f7f1660a1fb38f00562f627b49c6978.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917748 watch_fd=6 name=/var/log/containers/fluent-bit-nnl6z_logging_fluent-bit-97bd18985faab2ebe8332229b5719b584a2147bdf17dcade3c243850e039c4a9.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917854 watch_fd=7 name=/var/log/containers/hdfs-st-app-dd3aca9b9c8b874b-driver_cbops_spark-kubernetes-driver-18e4a400233f5c02ad515c03a597ac5a929ac14280a389b4aa2d66875af41446.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917815 watch_fd=8 name=/var/log/containers/hive-schematool-2mqb2_cbops_schematool-2adaae59d778d6c7d8ed448bc979c75508ec7e0a104417c2a2b03de05aaee5e5.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917836 watch_fd=9 name=/var/log/containers/journal-deployment-7fc4c9cf87-d9m7q_cbops_journal-app-container-c9948d74a1fbc2e3144a3bd384e3f296093af581b96d07e0991565daf1edefa1.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917699 watch_fd=10 name=/var/log/containers/kube-proxy-bxpvq_kube-system_kube-proxy-9d2246157e97623991cf0d732bd6dfff96457118e1b5cd2c5e8f6ab603403b90.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917795 watch_fd=11 name=/var/log/containers/notification-deployment-769bcd99cd-p9qmh_cbops_notification-container-7873837351be66bf5f221faa16ba33105259d779f6ffd4a112976be0898f320a.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917842 watch_fd=12 name=/var/log/containers/report-builder-deployment-67df7f7549-tkltx_cbops_template-config-container-85cbfc2eb99494022e8390ecf8f2ae8b5cdcbc6cc79fccd2148a0b3963d977c0.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917884 watch_fd=13 name=/var/log/containers/spark-thrift-7f856c7c74-4f7xj_cbops_spark-thrift-2a4c8632a1305ca8a758bd4665d5531cbe39bca44935b6ea646d630d31bceeea.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917733 watch_fd=14 name=/var/log/containers/vsphere-csi-node-9rhmk_vmware-system-csi_liveness-probe-987337c92de975c68bf0808ce1d44c45200d66fff31f4d1976b45ec6b26f8c58.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917710 watch_fd=15 name=/var/log/containers/vsphere-csi-node-9rhmk_vmware-system-csi_node-driver-registrar-022b9eb7bdea595cf5d393e919478f90671bbaf7df0608b69313231c2b8fa7ef.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917730 watch_fd=16 name=/var/log/containers/vsphere-csi-node-9rhmk_vmware-system-csi_vsphere-csi-node-ddb1bb81f0982fb8a50f8e9807896cb7d1df49a329924f35129b141e4882d2d6.log
[2026/02/17 10:03:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917716 watch_fd=17 name=/var/log/containers/antrea-agent-jtf58_kube-system_antrea-agent-314b72d43b99a70dcdbc78ff3f0de7573e1115e8a61d76a77c8412cd738e394a.log
[2026/02/17 11:57:36] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 11:57:36] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 11:57:36] [ warn] [engine] failed to flush chunk '1-1771329447.50557947.flb', retry in 8 seconds: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:37] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 11:57:37] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 11:57:37] [ warn] [engine] failed to flush chunk '1-1771329447.872233223.flb', retry in 7 seconds: task_id=1, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:44] [ info] [engine] flush chunk '1-1771329447.50557947.flb' succeeded at retry 1: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:44] [ info] [engine] flush chunk '1-1771329447.872233223.flb' succeeded at retry 1: task_id=1, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:46] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 11:57:46] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 11:57:46] [ warn] [engine] failed to flush chunk '1-1771329456.187417282.flb', retry in 8 seconds: task_id=2, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:47] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 11:57:47] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 11:57:47] [ warn] [engine] failed to flush chunk '1-1771329457.187864775.flb', retry in 6 seconds: task_id=3, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:53] [ info] [engine] flush chunk '1-1771329457.187864775.flb' succeeded at retry 1: task_id=3, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 11:57:54] [ info] [engine] flush chunk '1-1771329456.187417282.flb' succeeded at retry 1: task_id=2, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 12:50:45] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 12:50:46] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917842 watch_fd=12
[2026/02/17 17:35:23] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 17:35:23] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 17:35:23] [ warn] [engine] failed to flush chunk '1-1771349714.50214346.flb', retry in 8 seconds: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:24] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 17:35:24] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 17:35:24] [ warn] [engine] failed to flush chunk '1-1771349715.112684510.flb', retry in 6 seconds: task_id=1, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:30] [ info] [engine] flush chunk '1-1771349715.112684510.flb' succeeded at retry 1: task_id=1, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:31] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 17:35:31] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 17:35:31] [ warn] [engine] failed to flush chunk '1-1771349722.168120779.flb', retry in 10 seconds: task_id=2, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:31] [ info] [engine] flush chunk '1-1771349714.50214346.flb' succeeded at retry 1: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:33] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 17:35:33] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 17:35:33] [ warn] [engine] failed to flush chunk '1-1771349723.187245275.flb', retry in 10 seconds: task_id=3, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:34] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/17 17:35:34] [error] [output:loki:loki.0] no upstream connections available
[2026/02/17 17:35:34] [ warn] [engine] failed to flush chunk '1-1771349724.187842327.flb', retry in 11 seconds: task_id=4, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:41] [ info] [engine] flush chunk '1-1771349722.168120779.flb' succeeded at retry 1: task_id=2, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:43] [ info] [engine] flush chunk '1-1771349723.187245275.flb' succeeded at retry 1: task_id=3, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/17 17:35:45] [ info] [engine] flush chunk '1-1771349724.187842327.flb' succeeded at retry 1: task_id=4, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/18 03:53:26] [ warn] [net] getaddrinfo(host='loki.logging.svc.cluster.local', err=12): Timeout while contacting DNS servers
[2026/02/18 03:53:26] [error] [output:loki:loki.0] no upstream connections available
[2026/02/18 03:53:26] [ warn] [engine] failed to flush chunk '1-1771386796.398901236.flb', retry in 10 seconds: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
[2026/02/18 03:53:36] [ info] [engine] flush chunk '1-1771386796.398901236.flb' succeeded at retry 1: task_id=0, input=tail.0 > output=loki.0 (out_id=0)
