[root@fcprodkubjump ~]# kubectl describe nodes | grep -A5 "Allocated resources"
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests       Limits
  --------           --------       ------
  cpu                11 (69%)       13 (81%)
  memory             12900Mi (45%)  21Gi (75%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests       Limits
  --------           --------       ------
  cpu                10600m (66%)   12500m (78%)
  memory             12800Mi (45%)  21Gi (75%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests      Limits
  --------           --------      ------
  cpu                10900m (68%)  14 (87%)
  memory             13Gi (46%)    23Gi (82%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests    Limits
  --------           --------    ------
  cpu                1400m (8%)  4 (25%)
  memory             3Gi (10%)   6Gi (21%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests    Limits
  --------           --------    ------
  cpu                600m (3%)   500m (3%)
  memory             256Mi (0%)  512Mi (1%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests      Limits
  --------           --------      ------
  cpu                1700m (10%)   5850m (36%)
  memory             3628Mi (12%)  11152Mi (39%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests       Limits
  --------           --------       ------
  cpu                10100m (63%)   19 (119%)
  memory             11776Mi (41%)  29Gi (104%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests      Limits
  --------           --------      ------
  cpu                5700m (35%)   6800m (42%)
  memory             6528Mi (22%)  11008Mi (38%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests      Limits
  --------           --------      ------
  cpu                5600m (35%)   6500m (40%)
  memory             6400Mi (22%)  10752Mi (37%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                5900m (37%)  8 (50%)
  memory             8Gi (28%)    14Gi (50%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests      Limits
  --------           --------      ------
  cpu                5600m (35%)   6500m (40%)
  memory             6400Mi (22%)  10752Mi (37%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests    Limits
  --------           --------    ------
  cpu                650m (4%)   500m (3%)
  memory             512Mi (1%)  1Gi (3%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                7400m (46%)  10 (62%)
  memory             26Gi (93%)   34Gi (122%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests      Limits
  --------           --------      ------
  cpu                10600m (66%)  16500m (103%)
  memory             3328Mi (11%)  6656Mi (23%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                3400m (21%)  5 (31%)
  memory             4Gi (14%)    8Gi (28%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests       Limits
  --------           --------       ------
  cpu                7500m (47%)    15300m (96%)
  memory             11392Mi (40%)  27136Mi (95%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                1470m (18%)  100m (1%)
  memory             598Mi (4%)   298Mi (2%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                1490m (18%)  120m (1%)
  memory             530Mi (3%)   330Mi (2%)
--
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests     Limits
  --------           --------     ------
  cpu                1050m (13%)  0 (0%)
  memory             100Mi (0%)   0 (0%)
[root@fcprodkubjump ~]# kubectl top nodes
NAME                                             CPU(cores)   CPU(%)   MEMORY(bytes)   MEMORY(%)
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-4822w   2765m        17%      11520Mi         40%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-4crls   1818m        11%      12369Mi         43%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-5frcp   2443m        15%      8645Mi          30%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-7n45g   276m         1%       3835Mi          13%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-9j7ff   49m          0%       2751Mi          9%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-9l9lv   76m          0%       3669Mi          12%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-c5wq5   2123m        13%      17025Mi         59%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-c7c5w   1896m        11%      7275Mi          25%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-g4ljf   1324m        8%       6848Mi          24%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-gj5jj   1356m        8%       8391Mi          29%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-h4cdl   1163m        7%       6039Mi          21%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-nlzz2   57m          0%       3032Mi          10%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-pz6lh   1087m        6%       10557Mi         37%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-tv8ql   189m         1%       5190Mi          18%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-wcvnn   69m          0%       3061Mi          10%
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-xzvvj   1825m        11%      9209Mi          32%
a2p05vkscbopscls-ql4d8-6jkrl                     160m         2%       2991Mi          22%
a2p05vkscbopscls-ql4d8-gms9p                     307m         3%       3263Mi          24%
a2p05vkscbopscls-ql4d8-tq8pq                     236m         2%       3554Mi          26%
[root@fcprodkubjump ~]# kubectl get nodes -o custom-columns=NAME:.metadata.name,CPU:.status.allocatable.cpu,MEMORY:.status.allocatable.memory
NAME                                             CPU      MEMORY
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-4822w   15915m   29112528Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-4crls   15915m   29112536Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-5frcp   15915m   29112532Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-7n45g   15915m   29112532Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-9j7ff   15915m   29112536Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-9l9lv   15915m   29112532Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-c5wq5   15915m   29112536Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-c7c5w   15915m   29112540Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-g4ljf   15915m   29112536Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-gj5jj   15915m   29112536Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-h4cdl   15915m   29112532Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-nlzz2   15915m   29112536Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-pz6lh   15915m   29112536Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-tv8ql   15915m   29112540Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-wcvnn   15915m   29112536Ki
a2p05vkscbopscls-node-pool-0-48lq6-p4sgq-xzvvj   15915m   29112520Ki
a2p05vkscbopscls-ql4d8-6jkrl                     7915m    13583896Ki
a2p05vkscbopscls-ql4d8-gms9p                     7915m    13583904Ki
a2p05vkscbopscls-ql4d8-tq8pq                     7915m    13583904Ki
