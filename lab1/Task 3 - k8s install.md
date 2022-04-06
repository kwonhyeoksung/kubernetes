# Task 3 - k8s install

###  kubernetes를 설치

1. kubeadm, kubelet, kubectl 설치
apt패키지 인덱스를 업데이트하고 Kubernetes apt저장소를 사용하는 데 필요한 패키지를 설치

```
sudo apt-get -y update
sudo apt-get install -y apt-transport-https ca-certificates curl
```
Google Cloud 공개 서명 키를 다운로드

```
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg \
https://packages.cloud.google.com/apt/doc/apt-key.gpg
```
Kubernetes apt리포지토리를 추가

```
echo "deb \
[signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] \
https://apt.kubernetes.io/ kubernetes-xenial main" | \
sudo tee /etc/apt/sources.list.d/kubernetes.list
```
apt 패키지 색인을 업데이트하고, kubelet, kubeadm, kubectl을 설치하고 해당 버전을 고정

```
sudo apt-get -y update
```
```
sudo apt-get install -y kubelet kubeadm kubectl
```
```
sudo apt-mark hold kubelet kubeadm kubectl
```
```
systemctl enable --now kubelet
```

2. kubeadm 초기화   Master IP는 master vm 의 private ip

```
kubeadm init --pod-network-cidr=172.16.0.0/16 \
--apiserver-advertise-address=<Master IP>
```
출력결과(kubeadm join 이하 명령어)는 다른 노드를 클러스터에 연동할 때 사용하는 명령어 입니다.(worker node 연동)
![image](https://user-images.githubusercontent.com/92773629/137877948-678049de-4e17-4e11-be31-00daee62ef62.png)

3. Master 노드 설정
사용자에 대해 kubectl이 작동하도록 설정
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
export KUBECONFIG=/etc/kubernetes/admin.conf
```

4. Calico 네트워크 플러그인 설치
```
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
```
![image](https://user-images.githubusercontent.com/92773629/137878112-476a8d5f-9399-46a9-acaa-5be0a5c0af84.png)

5. kubectl 자동완성 적용
```
source <(kubectl completion bash)
echo "source <(kubectl completion bash)" >> ~/.bashrc
source /etc/bash_completion
alias k=kubectl
complete -F __start_kubectl k
```
6. master node에도 pod 를 생성 할 수 있도록 설정
```
kubectl taint nodes --all node-role.kubernetes.io/master-
```

7. node 확인
```
kubectl get nodes
```
