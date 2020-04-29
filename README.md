setelah install kops di aws selesai.

- untuk koneksi
# ssh-keygen -t rsa
- install awscli
# aws configure
- cek versi kubectl dan kops
# kubectl version --client
# kops version
- setting bucket S3 di simpan di .bashrc lalu source .bashrc nya dan cek echo ${KOPS_CLUSTER_NAME}
# export bucket_name=wahid98-store
# export KOPS_CLUSTER_NAME=kube.wahid98.xyz
# export KOPS_STATE_STORE=s3://${bucket_name}
- apply kops cluster menggunakan ssh-keygen
# kops create cluster --zones=ap-southeast-1a --name=${KOPS_CLUSTER_NAME} --ssh-public-key=~/.ssh/id_rsa.pub
- cek kops yang sudah di buat
# kops get cluster
- install kops cluster
# kops update cluster --name ${KOPS_CLUSTER_NAME} --yes
- validate kops
# kops validate cluster
- melihat token kubernetes
# kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')
- akses dashboard kubernetes di local
# http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
- Delete Cluster Kops
# kops delete cluster --name ${KOPS_CLUSTER_NAME} --yes
- Dashboard
# kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc5/aio/deploy/recommended.yaml
