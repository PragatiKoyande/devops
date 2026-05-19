2603:    kind: Deployment
2604:    name: user-deployment
2606:  minReplicas: 1
2607:  maxReplicas: 5
2609:  behavior:
2610:    scaleUp:
2611:      stabilizationWindowSeconds: 60
2612:    scaleDown:
2613:      stabilizationWindowSeconds: 300
2615:  metrics:
2616:    - type: Resource
2617:      resource:
2618:        name: cpu
2619:        target:
2620:          type: Utilization
2621:          averageUtilization: 70
2622:---
2623:# Source: umbrella-chart/charts/template-config/templates/pdb.yaml
2624:apiVersion: policy/v1
2625:kind: PodDisruptionBudget
2626:metadata:
2627:  name: template-config-pdb
2628:  namespace: backend
2630:spec:
2631:  minAvailable: 1
2632:  selector:
2633:    matchLabels:
2634:      app: template-app
2635:---
2636:# Source: umbrella-chart/charts/report-service/templates/service.yaml
2637:apiVersion: v1
2638:kind: Service
2639:metadata:
2640:  name: report-service
2641:  namespace: backend
2643:spec:
2644:  type: ClusterIP
2645:  selector:
2646:    app: report-backend
2648:  ports:
2649:    - protocol: TCP
2650:      port: 80
2651:      targetPort: 9005
2652:---
2653:# Source: umbrella-chart/charts/journal/templates/service.yaml
2654:apiVersion: v1
2655:kind: Service
2656:metadata:
2657:  name: journal-service
2658:  namespace: backend
2660:spec:
2661:  selector:
2662:    app: journal-app
2664:  ports:
2665:    - name: http
2666:      protocol: TCP
2667:      port: 80
2668:      targetPort: 9999
2670:  type: ClusterIP
2671:---
2672:# Source: umbrella-chart/charts/journal/templates/deployment.yaml
2673:apiVersion: apps/v1
2674:kind: Deployment
2675:metadata:
2676:  name: journal-deployment
2677:  namespace: backend
2679:spec:
2680:  replicas: 1
2682:  strategy:
2683:    type: RollingUpdate
2684:    rollingUpdate:
2685:      maxUnavailable: 0
2686:      maxSurge: 1
2688:  selector:
2689:    matchLabels:
2690:      app: journal-app
2692:  template:
2693:    metadata:
2694:      labels:
2695:        app: journal-app
2697:    spec:
2698:      serviceAccountName: journal-sa
2699:      terminationGracePeriodSeconds: 30
2701:      securityContext:
2702:        runAsNonRoot: true
2703:        runAsUser: 10001
2704:        fsGroup: 10001
2706:      topologySpreadConstraints:
2707:        - maxSkew: 1
2708:          topologyKey: kubernetes.io/hostname
2709:          whenUnsatisfiable: ScheduleAnyway
2710:          labelSelector:
2711:            matchLabels:
2712:              app: journal-app
2714:      containers:
2715:        - name: journal-app-container
2716:          image: h06vksharbor.corp.ad.sbi/cbops/journal-service:DEV04
2717:          imagePullPolicy: Always
2719:          envFrom:
2720:            - configMapRef:
2721:                name: redis-config
2722:            - configMapRef:
2723:                name: oracle-config
2724:            - secretRef:
2725:                name: oracle-secret
2727:          env:
2728:            null
2730:          ports:
2731:            - containerPort: 9999
2733:          resources:
2734:            limits:
2735:              cpu: 500m
2736:              memory: 1Gi
2737:            requests:
2738:              cpu: 250m
2739:              memory: 512Mi
2741:          startupProbe:
2742:            tcpSocket:
2743:              port: 9999
2744:            failureThreshold: 60
2745:            periodSeconds: 10
2747:          livenessProbe:
2748:            tcpSocket:
2749:              port: 9999
2750:            initialDelaySeconds: 90
2751:            periodSeconds: 15
2752:            timeoutSeconds: 5
2753:            failureThreshold: 5
2755:          readinessProbe:
2756:            tcpSocket:
2757:              port: 9999
2758:            initialDelaySeconds: 30
2759:            periodSeconds: 10
2760:            timeoutSeconds: 5
2761:            failureThreshold: 5
2763:          lifecycle:
2764:            preStop:
2765:              exec:
2766:                command: ["/bin/sh", "-c", "sleep 10"]
2768:          securityContext:
2769:            allowPrivilegeEscalation: false
2770:            capabilities:
2771:              drop:
2772:              - ALL
2773:            readOnlyRootFilesystem: false
2774:Error: YAML parse error on umbrella-chart/charts/user-service/templates/deployment.yaml: error converting YAML to JSON: yaml: line 81: mapping values are not allowed in this contexts
