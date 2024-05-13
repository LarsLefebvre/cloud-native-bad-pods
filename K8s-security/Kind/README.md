# Install Kind

### Installing With A Package Manager
The kind community has enabled installation via the following package managers.

#### On macOS via Homebrew:

brew install kind

#### On macOS via MacPorts:

sudo port selfupdate && sudo port install kind

#### On Windows via Chocolatey (https://chocolatey.org/packages/kind)

choco install kind

### Installing From Release Binaries
Pre-built binaries are available on our releases page.

To install, download the binary for your platform from “Assets”, then rename it to kind (or perhaps kind.exe on Windows) and place this into your $PATH at your preferred binary installation directory.

#### On Linux:

##### For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-linux-amd64

##### For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

##### For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-linux-amd64
##### For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

#### On macOS:

##### For Intel Macs
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-darwin-amd64

##### For M1 / ARM Macs
[ $(uname -m) = arm64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-darwin-arm64
chmod +x ./kind
mv ./kind /some-dir-in-your-PATH/kind

##### For Intel Macs
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-darwin-amd64
##### For M1 / ARM Macs
[ $(uname -m) = arm64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-darwin-arm64
chmod +x ./kind
mv ./kind /some-dir-in-your-PATH/kind

#### On Windows in PowerShell:

curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.22.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe

### Installing From Source
In addition to the pre-built binary + package manager installation options listed above you can install kind from source with go install sigs.k8s.io/kind@v0.22.0 or clone this repo and run make build from the repository.

#### Installing With make

Using make build does not require installing Go and will build kind reproducibly, the binary will be in bin/kind inside your clone of the repo.

You should only need make and standard userspace utilities to run this build, it will automatically obtain the correct go version with our vendored copy of gimme.

You can then call ./bin/kind to use it, or copy bin/kind into some directory in your system PATH to use it as kind from the command line.

make install will attempt to mimic go install and has the same path requirements as go install below.

#### Installing with go install

When installing with Go please use the latest stable Go release. At least go1.16 or greater is required.

To install use: go install sigs.k8s.io/kind@v0.22.0.

If you are building from a local source clone, use go install . from the top-level directory of the clone.

go install will typically put the kind binary inside the bin directory under go env GOPATH, see Go’s “Compile and install packages and dependencies” for more on this. You may need to add that directory to your $PATH if you encounter the error kind: command not found after installation, you can find a guide for adding a directory to your PATH at https://gist.github.com/nex3/c395b2f8fd4b02068be37c961301caa7#file-path-md.

## Setup the Kind Cluster

kind create cluster --config=cluster-setup.yml

## Make sure to have the correct kube context

kubectl cluster-info --context kind-kind

## Verify that your nodes are running

kubectl get nodes