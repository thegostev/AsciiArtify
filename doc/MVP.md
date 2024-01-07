# Demo of the product output

The purpose of this document is to provide a demo of the resulting output for AsciiArtify minimum viable product (MVP).

## Infrastructure

As the infrastructure k3s (lightweight Kubernetes distribution) and ArgoCD (Kubernetes controller for monitoring and deployment) are used.

## Steps

1. Creating application in ArgoCD

2. Enabling port forwarding

`k port-forward -n demo svc/ambassador 8088:80`

3. Downloading an input file from an open source

`wget -O /tmp/g.png https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png`

4. Upload uploading the file into converter

`curl -F 'image=@/tmp/g.png' localhost:8088/img/`

## Result

5. The resulting output in CLI

<img width="1009" alt="Screenshot 2024-01-07 at 18 34 56" src="https://github.com/thegostev/AsciiArtify/assets/25153729/1e92d4a1-0720-46ca-a914-7211f96c760a">
