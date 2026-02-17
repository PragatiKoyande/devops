kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
error: Internal error occurred: error executing command in container: failed to exec in container: failed to start exec "0139eda634c79bfcbcc9c0bb5aaeb09b7c76a4e891ceb901fe5b25d65ab4a41d": OCI runtime exec failed: exec failed: unable to start container process: exec: "sh": executable file not found in $PATH: unknown
[root@fcsitgateway SIT-Grafana]# kubectl logs fluent-bit-bhx4f -n logging --kubeconfig h06vkssitcbopscls.conf
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

[2026/02/17 05:57:14] [ info] [fluent bit] version=2.2.2, commit=eeea396e88, pid=1
[2026/02/17 05:57:14] [ info] [storage] ver=1.5.1, type=memory, sync=normal, checksum=off, max_chunks_up=128
[2026/02/17 05:57:14] [ info] [cmetrics] version=0.6.6
[2026/02/17 05:57:14] [ info] [ctraces ] version=0.4.0
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] initializing
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] storage_strategy='memory' (memory only)
[2026/02/17 05:57:14] [ info] [filter:kubernetes:kubernetes.0] https=1 host=kubernetes.default.svc port=443
[2026/02/17 05:57:14] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 05:57:14] [ info] [filter:kubernetes:kubernetes.0] local POD info OK
[2026/02/17 05:57:14] [ info] [filter:kubernetes:kubernetes.0] testing connectivity with API server...
[2026/02/17 05:57:14] [ info] [filter:kubernetes:kubernetes.0] connectivity OK
[2026/02/17 05:57:14] [ info] [output:loki:loki.0] configured, hostname=loki.logging.svc.cluster.local:3100
[2026/02/17 05:57:14] [ info] [sp] stream processor started
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917716 watch_fd=1 name=/var/log/containers/antrea-agent-2x8gc_kube-system_antrea-agent-87aa634d2ecfe4c302fdf2289d1f2594afe6cf1ce45151147e0ff1e65d0a45d5.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917710 watch_fd=2 name=/var/log/containers/antrea-agent-2x8gc_kube-system_antrea-agent-tweaker-fbe5c401488f8907be5a5aac811e2688b0d47682fd1472400feb365d86df022a.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917720 watch_fd=3 name=/var/log/containers/antrea-agent-2x8gc_kube-system_antrea-ovs-a3959ad34ab27588e2068f11e0f51264cb2d111816e39be8ac492e540e4660d6.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917713 watch_fd=4 name=/var/log/containers/antrea-agent-2x8gc_kube-system_install-cni-de7b4f744aaa04a56357c3972e6517a2049e5c6935f0e30902c87097b0b9d32b.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917906 watch_fd=5 name=/var/log/containers/cbs-app-092d299be5dc2a60-driver_cbops_spark-kubernetes-driver-8e63c47962c34c751ae06a886aa633b1ed5133ae8c118adcb5486b98ce7ad1af.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917892 watch_fd=6 name=/var/log/containers/cbs-app-0adc689be5aa0ff0-driver_cbops_spark-kubernetes-driver-8ea4fb7367bbb17d3f8a442752784faa8334feda06773dbf98c089f10b094acf.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917902 watch_fd=7 name=/var/log/containers/cbs-app-0d99699be5cb494d-driver_cbops_spark-kubernetes-driver-b36310bc5efc4ae71f5e59141e2335993ad45956d1fc1aaf403d96004a5f4674.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917944 watch_fd=8 name=/var/log/containers/cbs-app-71e5919bf3cc8c4d-driver_cbops_spark-kubernetes-driver-b2016fd0e30f1198d212a49fa4bed3e7b0f6d7a27a07623c35471a5a68d2981a.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917914 watch_fd=9 name=/var/log/containers/cbs-app-cbcb8f9be6396624-driver_cbops_spark-kubernetes-driver-8240a14dc95e347fb79af0e333433399f0e424552301de95cd4cd0832de6d234.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917910 watch_fd=10 name=/var/log/containers/cbs-app-d667d59be60a14cc-driver_cbops_spark-kubernetes-driver-db23a3c9d1f19aef1441da3bfb453a339eab0c3e604630f3174591bf43f53ad1.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917898 watch_fd=11 name=/var/log/containers/cbs-app-f18f949be5a1cf90-driver_cbops_spark-kubernetes-driver-b62d487f6d27afe8717c160ba763a6bc7d30ea2f34aeadc4ed4a18b10e47673b.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917894 watch_fd=12 name=/var/log/containers/cbs-app-fe14439be58d00e6-driver_cbops_spark-kubernetes-driver-316c2a53fcb918b148f9437c54de8df193f36b65df4dc8288d1d78339b40a167.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917744 watch_fd=13 name=/var/log/containers/cert-manager-cainjector-69896f7559-2r5rt_cert-manager_cert-manager-cainjector-8e8196ef3517d1d31918146ef3dec6abc19302c9562d8b6348aca25352d48a5b.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917863 watch_fd=14 name=/var/log/containers/common-master-deployment-7b7557cf4f-fgqv8_cbops_common-master-container-44309829c8d2b54397993f800e8553938ecaa99703dcf24c0605cd44eead9e51.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917848 watch_fd=15 name=/var/log/containers/common-request-deployment-6b95fbdb56-q8mb9_cbops_common-request-container-a3a8e6f4a44b32e7377f1aff0934d97714bcaf9aeba36746493f56f6477bc1d7.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917858 watch_fd=16 name=/var/log/containers/delete-oracle-connector-cr5jb_cbops_delete-f1a07a2e635e3423fc11a1c93c7bd6cf7790a14c18f2d90939a3159c512b69e6.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917872 watch_fd=17 name=/var/log/containers/difference-app-143b609bea47f8fd-driver_cbops_spark-kubernetes-driver-6414f1bb214ba19f7db32f53096fc46c15ad672eece0ac175e154170fffe96cd.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917692 watch_fd=18 name=/var/log/containers/docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-sb28w_kube-system_docker-registry-d36fec07401992616ade0aadc87771b946d6848899cfa65d2f9ba7e6e24f04c6.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917837 watch_fd=19 name=/var/log/containers/fluent-bit-l7tq4_tanzu-system-logging_fluent-bit-573314b2000ae1c70bd7ffdb23d62817cb5232edc87ec0b98fb741b68de507cc.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917930 watch_fd=20 name=/var/log/containers/glif-app-7dc20a9be91ad791-driver_cbops_spark-kubernetes-driver-6ad3d74660776aa7d400edc0f0de9148710783557c4edcf4f300e44af09679f0.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917917 watch_fd=21 name=/var/log/containers/glif-app-93442c9be651089d-driver_cbops_spark-kubernetes-driver-2c39f50468a6506563f04c7c037c97e930ef26c4143c11c92e68c3cb2a63eb64.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917925 watch_fd=22 name=/var/log/containers/glif-app-cdb3fd9be65f17e9-driver_cbops_spark-kubernetes-driver-45f094b33a078e18d06c38ed7bcc2e44baf12df91d0c4885e6e007835f876b98.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917923 watch_fd=23 name=/var/log/containers/glif-app-de3d249be913fd4e-driver_cbops_spark-kubernetes-driver-bfac6437229ae08b9757d90215e333168ec6341ddb47610172ca61bdbb50fc3b.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917861 watch_fd=24 name=/var/log/containers/kafka-0_cbops_fix-kafka-permissions-f2a504a4266637ed035d674ac6a26b8a0c372ebda82a06957723355b405f704a.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917788 watch_fd=25 name=/var/log/containers/kafka-0_cbops_kafka-ddb672d1d73be1fcf2d508827675f49e21b7729471c04688a741a3de5fec8ff5.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917934 watch_fd=26 name=/var/log/containers/kafkahit-lg5vf_cbops_kafkacheck-f24a4ef661d2d14d1d3273d11a4b9b5cd215fea8dc74af9433a8a491783a2cea.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917966 watch_fd=27 name=/var/log/containers/kong-6dd5746646-wttch_kong-system_kong-b8544b6d451defe3a519fc0d1b1cbb39b13196477883459f33ac8a5179f08dde.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917699 watch_fd=28 name=/var/log/containers/kube-proxy-22gdj_kube-system_kube-proxy-ee12cc3298df3db57e40878b45329e90ca75b88f8aa3e7658f82e3697ff189d1.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917875 watch_fd=29 name=/var/log/containers/loki-5859bf4d49-lsmlc_logging_loki-82d5a62dda48b690bc35a63073d10b499128a44961f314bb3e267bc06c12db39.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917818 watch_fd=30 name=/var/log/containers/postgres-db-7b865dd6fc-gcnv9_cbops_postgres-db-a0974c0dbcd1ab6cfec3e394399b6f60c6461aa760e66d1f71558ec470ba0d9d.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917832 watch_fd=31 name=/var/log/containers/process-status-deployment-7dddfbcddd-sldjx_cbops_process-status-container-e4a2a3dc0afc34cafdb11f22013c20a715106352ef8fcc8938f6358d4f69658b.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917887 watch_fd=32 name=/var/log/containers/redis-deployment-59ddbb9b85-7bzwg_cbops_redis-container-5f63ccfb56efcec0bb52e3f676360b4618158cca74a1f5bf161ed9c16f701fb8.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917871 watch_fd=33 name=/var/log/containers/register-oracle-connector-b2qps_cbops_register-fb93392367e57212d44991000c552e61bafef933ab4f29aa3f5cee4811bcbda6.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917933 watch_fd=34 name=/var/log/containers/report-deployment-6846f77ff6-4l7fc_cbops_report-container-33184fdf3432b9a7c5561cbcbfe584570991aab09e7cc68a1addbde751abffa0.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917823 watch_fd=35 name=/var/log/containers/report-deployment-6846f77ff6-4l7fc_cbops_report-container-bee5d314cf518d95b56c404716d8bb08cb492eb6cb98f58e8be4d3994a57a0db.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917851 watch_fd=36 name=/var/log/containers/template-config-deployment-77545dd89d-5khgd_cbops_template-config-container-842eabbe2e905a08de68b19b35a056ae817eceed4a3572a4bc7696814ea2b234.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917733 watch_fd=37 name=/var/log/containers/vsphere-csi-node-6p769_vmware-system-csi_liveness-probe-6749c5f5d3b6ff134581db6b055e320a5e00baecbe9002c2872ba14fa37c3247.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917702 watch_fd=38 name=/var/log/containers/vsphere-csi-node-6p769_vmware-system-csi_node-driver-registrar-c671e7f69f1755b8086816f66c37f6d81e971a4a3f04c82a20c8662d2ab5a9b9.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917819 watch_fd=39 name=/var/log/containers/vsphere-csi-node-6p769_vmware-system-csi_vsphere-csi-node-5d53693280ee6229b9b0ee60abb6ad1b84d86d0bf6b1cab94a703f9a4cedd46a.log
[2026/02/17 05:57:14] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917962 watch_fd=40 name=/var/log/containers/fluent-bit-bhx4f_logging_fluent-bit-072fbc0be36dc379d2b13d979e3d5ff61131253e4779b7d4288365e0161cd7ed.log
[2026/02/17 05:57:15] [ warn] [filter:kubernetes:kubernetes.0] annotation 'fluentbit.io/exclude' not allowed (ns='tanzu-system-logging' pod_name='fluent-bit-l7tq4')
[2026/02/17 06:35:52] [ info] [filter:kubernetes:kubernetes.0]  token updated
[2026/02/17 06:53:21] [ info] [input:tail:tail.0] inode=917837 handle rotation(): /var/log/containers/fluent-bit-l7tq4_tanzu-system-logging_fluent-bit-573314b2000ae1c70bd7ffdb23d62817cb5232edc87ec0b98fb741b68de507cc.log => /var/log/pods/tanzu-system-logging_fluent-bit-l7tq4_5a44e901-45cc-4cda-b846-418c9fa8a659/fluent-bit/0.log.20260217-065321
[2026/02/17 06:53:21] [error] [input:tail:tail.0] could not rotate file /var/log/pods/tanzu-system-logging_fluent-bit-l7tq4_5a44e901-45cc-4cda-b846-418c9fa8a659/fluent-bit/0.log.20260217-065321->/var/log/pods/tanzu-system-logging_fluent-bit-l7tq4_5a44e901-45cc-4cda-b846-418c9fa8a659/fluent-bit/0.log.20260217-065321 in database
[2026/02/17 06:53:21] [ info] [input:tail:tail.0] inotify_fs_remove(): inode=917837 watch_fd=19
[2026/02/17 06:53:21] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917837 watch_fd=41 name=/var/log/pods/tanzu-system-logging_fluent-bit-l7tq4_5a44e901-45cc-4cda-b846-418c9fa8a659/fluent-bit/0.log.20260217-065321
[2026/02/17 06:53:22] [ info] [input:tail:tail.0] inotify_fs_add(): inode=917847 watch_fd=42 name=/var/log/containers/fluent-bit-l7tq4_tanzu-system-logging_fluent-bit-573314b2000ae1c70bd7ffdb23d62817cb5232edc87ec0b98fb741b68de507cc.log
