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
[root@fcuatgateway ~]# kubectl describe nodes | egrep "Name:|cpu:|memory:"
Name:               h06vksuat1cbopscls-9mgb5-mlhwp
  cpu:                8
  memory:             16371240Ki
  cpu:                7910m
  memory:             13581864Ki
Name:               h06vksuat1cbopscls-9mgb5-slt8c
  cpu:                8
  memory:             16371236Ki
  cpu:                7910m
  memory:             13581860Ki
Name:               h06vksuat1cbopscls-9mgb5-v97gx
  cpu:                8
  memory:             16371240Ki
  cpu:                7910m
  memory:             13581864Ki
Name:               h06vksuat1cbopscls-node-pool-1-8qvhf-mjgbk-2fjvd
  cpu:                16
  memory:             32908684Ki
  cpu:                15890m
  memory:             29109644Ki
Name:               h06vksuat1cbopscls-node-pool-1-8qvhf-mjgbk-nf5tk
  cpu:                16
  memory:             32908680Ki
  cpu:                15890m
  memory:             29109640Ki
Name:               h06vksuat1cbopscls-node-pool-1-8qvhf-mjgbk-vshc5
  cpu:                16
  memory:             32908680Ki
  cpu:                15890m
  memory:             29109640Ki
Name:               h06vksuat1cbopscls-node-pool-1-8qvhf-tvgr4-djgd9
  cpu:                16
  memory:             32908680Ki
  cpu:                15890m
  memory:             29109640Ki
