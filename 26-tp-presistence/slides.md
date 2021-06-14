%title: Helm
%author: xavki
%Vidéos: [Helm]()
%blog: [Xavki Blog](https://xavki.blog)

# HELM : TP Projet API - Persistence Data

<br>

		0 - création d'un répertoire servi par nfs

		1 - création d'un pv & storageClass

		2 - adaptation de la chart redis (values, pvc, deployment)

--------------------------------------------------------------------

# HELM : TP Projet API - Persistence Data

<br>

Création et mise à jour NFS

```
sudo mkdir -p /srv/redis
sudo chmod 777 /srv/redis
sudo vim /etc/exports 
sudo exportfs -a
```

--------------------------------------------------------------------

# HELM : TP Projet API - Persistence Data

<br>

Création d'un PV

```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: redis-pv
spec:
  storageClassName: redis
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  nfs:
    server: 192.168.12.20
    path: "/srv/redis/"
```

--------------------------------------------------------------------

# HELM : TP Projet API - Persistence Data

<br>

Création d'une StorageClass

```
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: redis
provisioner: kubernetes.io/no-provisioner
volumeBindingMode: WaitForFirstConsumer
```

--------------------------------------------------------------------

# HELM : TP Projet API - Persistence Data

<br>

Adaptation chart - values

```
redis_PersistentVolumeClaim:
  enabled: true
  name: redis
  storageClassName: redis
  size: "1Gi"
```

--------------------------------------------------------------------

# HELM : TP Projet API - Persistence Data

<br>

Adaptation chart - template PVC

```
{{- if eq .Values.redis_PersistentVolumeClaim.enabled true}}
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: {{ .Values.redis_PersistentVolumeClaim.name }}
spec:
  storageClassName: {{ .Values.redis_PersistentVolumeClaim.storageClassName }}
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: {{ .Values.redis_PersistentVolumeClaim.size }}
{{- end }}
```

--------------------------------------------------------------------

# HELM : TP Projet API - Persistence Data

<br>

Adaptation chart - template deployment

```
      volumes:
        {{- if eq .Values.redis_PersistentVolumeClaim.enabled true }}
        - name: data
          persistentVolumeClaim:
            claimName: {{ .Values.redis_PersistentVolumeClaim.name }} 
        {{- else }}
        - name: data
          emptyDir: {}
        {{- end }}
```

Notes : path /data et --appendonly yes
