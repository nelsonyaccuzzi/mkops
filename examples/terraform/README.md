# Como instalar


```
wget https://releases.hashicorp.com/terraform/1.3.4/terraform_1.3.4_linux_amd64.zip
podman run -it -v $(pwd):/tmp alpine sh
    apk add unzip
    cd /tmp
    unzip terraform_1.3.4_linux_amd64.zip
    exit
sudo mv terraform /usr/local/bin

```
