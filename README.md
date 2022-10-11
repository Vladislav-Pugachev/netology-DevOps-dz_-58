## Развертывание кластера на собственных серверах, лекция 2
Изменен [inventory file](./hosts.yml)

### 1. Результат запуска playbook

```commandline
PLAY RECAP *****************************************************************************************************************************************************************************************************************************
localhost                  : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
master1                    : ok=723  changed=142  unreachable=0    failed=0    skipped=1247 rescued=0    ignored=9   
worker1                    : ok=500  changed=90   unreachable=0    failed=0    skipped=764  rescued=0    ignored=2   
worker2                    : ok=500  changed=90   unreachable=0    failed=0    skipped=763  rescued=0    ignored=2   
worker3                    : ok=500  changed=90   unreachable=0    failed=0    skipped=763  rescued=0    ignored=2   
worker4                    : ok=500  changed=90   unreachable=0    failed=0    skipped=763  rescued=0    ignored=2   
```
### 2. Проверка кластера
```commandline
ubuntu@master1:~/kubespray$ kubectl get nodes
NAME      STATUS   ROLES           AGE     VERSION
master1   Ready    control-plane   7m6s    v1.24.6
worker1   Ready    <none>          5m46s   v1.24.6
worker2   Ready    <none>          5m45s   v1.24.6
worker3   Ready    <none>          5m46s   v1.24.6
worker4   Ready    <none>          5m45s   v1.24.6
```
### 3. Проверка доступа к кластеру извне. Для доступа к кластеру извне была раcкомментирована строчка "supplementary_addresses_in_ssl_keys: [62.84.126.141]" в файле inventory/mycluster/group_vars/k8s_cluster/k8s-cluster.yml и заново запущен playbook

```commandline
vlad@home:~/Documents/Netology/DevOps/dz_№58$ kubectl get nodes
NAME      STATUS   ROLES           AGE   VERSION
master1   Ready    control-plane   44m   v1.24.6
worker1   Ready    <none>          42m   v1.24.6
worker2   Ready    <none>          42m   v1.24.6
worker3   Ready    <none>          42m   v1.24.6
worker4   Ready    <none>          42m   v1.24.6

```
