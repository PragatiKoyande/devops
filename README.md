[root@fcuatgateway ~]# kubectl top nodes
NAME                                               CPU(cores)   CPU(%)      MEMORY(bytes)   MEMORY(%)
h06vksuat1cbopscls-9mgb5-mlhwp                     257m         3%          3205Mi          24%
h06vksuat1cbopscls-9mgb5-slt8c                     294m         3%          2592Mi          19%
h06vksuat1cbopscls-9mgb5-v97gx                     223m         2%          3635Mi          27%
h06vksuat1cbopscls-node-pool-1-8qvhf-mjgbk-2fjvd   1033m        6%          16018Mi         56%
h06vksuat1cbopscls-node-pool-1-8qvhf-mjgbk-nf5tk   97m          0%          4851Mi          17%
h06vksuat1cbopscls-node-pool-1-8qvhf-mjgbk-vshc5   362m         2%          15921Mi         56%
h06vksuat1cbopscls-node-pool-1-8qvhf-tvgr4-djgd9   <unknown>    <unknown>   <unknown>       <unknown>
[root@fcuatgateway ~]# kubectl decribe nodes | grep -A5 "Allocated resources"
error: unknown command "decribe" for "kubectl"

Did you mean this?
        describe
[root@fcuatgateway ~]# kubectl describe nodes | grep -A5 "Allocated resources"
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                1690m (21%)  100m (1%)
  memory             598Mi (4%)   298Mi (2%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                1050m (13%)  0 (0%)
  memory             100Mi (0%)   0 (0%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                1050m (13%)  20m (0%)
  memory             132Mi (0%)   32Mi (0%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                1420m (8%)   1600m (10%)
  memory             2802Mi (9%)  4906Mi (17%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                5600m (35%)  9 (56%)
  memory             2560Mi (9%)  5Gi (18%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests      Limits
  --------           --------      ------
  cpu                5100m (32%)   14350m (90%)
  memory             9516Mi (33%)  15760Mi (55%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                5400m (33%)  8 (50%)
  memory             2Gi (7%)     4Gi (14%)
