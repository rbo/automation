# Build execution enviroment

Ansible builder to not support straigt multi-arch build with podman: <https://github.com/ansible/ansible-builder/issues/651>

```shell
export VERSION=$(date +%Y%m%d%H%M)
export IMAGE="quay.io/rbohne/automation:ee-$VERSION"

podman manifest rm $IMAGE
podman rmi $IMAGE

ansible-builder create --verbosity 3
podman build --manifest ${IMAGE} --platform linux/amd64,linux/arm64 context/

podman manifest push ${IMAGE}

```
