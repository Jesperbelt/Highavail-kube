## Add gpu-operator helm chart
# Install helm
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 \
   && chmod 700 get_helm.sh \
   && ./get_helm.sh

# Add nvidia helm repo
helm repo add nvidia https://helm.ngc.nvidia.com/nvidia \
   && helm repo update

# Install the gpu-operator helm chart, be sure to have installed the runtimeclass.
helm install --wait --generate-name \
     -n gpu-operator --create-namespace \
     nvidia/gpu-operator