D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl exec -it loki-6dd797b766-jhxtj -n logging --kubeconfig h06vksuatcbopscls.conf -- df -h
Filesystem                Size      Used Available Use% Mounted on
overlay                  78.2G     57.3G     16.8G  77% /
tmpfs                    64.0M         0     64.0M   0% /dev
/dev/sdc1                78.2G      8.4G     65.8G  11% /etc/loki
/dev/sde                 48.9G    628.7M     45.8G   1% /var/loki
/dev/sdc1                78.2G      8.4G     65.8G  11% /etc/hosts
/dev/sdc1                78.2G      8.4G     65.8G  11% /dev/termination-log
/dev/sdb1                78.2G     57.3G     16.8G  77% /etc/hostname
/dev/sdb1                78.2G     57.3G     16.8G  77% /etc/resolv.conf
shm                      64.0M         0     64.0M   0% /dev/shm
tmpfs                     7.8G         0      7.8G   0% /proc/acpi
tmpfs                    64.0M         0     64.0M   0% /proc/kcore
tmpfs                    64.0M         0     64.0M   0% /proc/keys
tmpfs                    64.0M         0     64.0M   0% /proc/latency_stats
tmpfs                    64.0M         0     64.0M   0% /proc/timer_list
tmpfs                     7.8G         0      7.8G   0% /proc/scsi
tmpfs                     7.8G         0      7.8G   0% /sys/firmware
