# Festive Calendar 2025: Crossplane-powered-Platform-Engineering:-

Greetings and Welcome to another amazing Session in __Festive Calendar 2025__

Discover how __Crossplane simplifies cloud infrastructure__.

Join me to learn more!

| <img src="Images/01-Festive-Calendar-2025-Banner.jpg" alt="Festive-Calendar-2025"> | 
| --------- |

| __VIRTUAL SESSION:-__ |
| --------- |
| __LIVE DEMO__ was Recorded as part of my Presentation in __Festive Calendar 2025__ |
| Duration of My Demo = __25 Mins 35 Secs__ |
| [![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/9DMBOyswyLk/0.jpg)](https://www.youtube.com/watch?v=9DMBOyswyLk) |


| Agenda:- |
| --------- |

| __#__ | __Topics__ |
| --------- | --------- |
| 1. | Introduction to Crossplane and its key features. |
| 2. | Visual overview: Integration of Crossplane and Azure. |
| 3. | Crossplane Use case. |
| 4. | Setting up Crossplane with Azure. |
| 5. | Deploying Azure resources using Crossplane - Command-Line. |
| 6. | Delete Azure resources using Crossplane - Command-Line. |

| 01: Introduction to Crossplane and its key features:- |
| --------- |
| <img src="Images/02-Crossplane.jpg" alt="Crossplane"> |

| Definition:- |
| --------- |

Crossplane is a CNCF project that helps you manage cloud resources in a Kubernetes-native way. 
With Kubernetes, we used to manage only application, but with Crossplane, we can now manage cloud infrastructure.
For Ease of understanding, consider like this -
- With Crossplane, we can write a Kubernetes YAML file, and it will create the desired Cloud Resources (For Example - A Resource Group), directly from Kubernetes cluster.

| Reference Links:- |
| --------- |
- https://www.crossplane.io/
- https://docs.crossplane.io/latest/getting-started/introduction/

| Key Features:- |
| --------- |
| <img src="Images/03-Crossplane-Components.jpg" alt="Crossplane-Components"> |

| 02: Visual overview: Integration of Crossplane and Azure:- |
| --------- |
| <img src="Images/04-Crossplane-Azure.jpg" alt="Crossplane-Azure"> |


| 03: Crossplane Use cases:- |
| --------- |

| Primary Use case:- |
| --------- |
| Earlier Kubernetes was used only for Containerization and Deployment. Now with Crossplane, Kubernetes can be used to provision Infrastructure using same YAML file and apply it with kubectl. |

| Additional Use cases:- |
| --------- |

| I. GitOps-Based Infrastructure Management |
| --------- |
| Write YAML to describe cloud resources, push it to any Git repository, A tool like FluxCD or ArgoCD notices the change, informs Crossplane to create those resources |
| <img src="Images/05-Crossplane-GitOps.jpg" alt="Crossplane-GitOps">  |
| __II. Multi-Cloud Abstraction__ |
| One tool and one set of instructions to manage resources (not always true) across different cloud providers (like Azure, AWS, and GCP). |
| <img src="Images/06-Crossplane-MultiCloud.jpg" alt="Crossplane-MultiCloud"> |
| __III. Self-Service Platforms__ |
| The platform team (DevOps/SRE) sets up the rules, templates, and permissions using Crossplane. |
| A developer writes a small YAML file and runs using Kubectl. |
| <img src="Images/07-Crossplane-SS.jpg" alt="Crossplane-SS"> |
| __IV. Policy & Security Governance__ |
| Platform teams (DevOps or SREs) define "Compositions". These are like blueprints. |
| Platform teams also apply "constraints or limits". These are like Azure Policies (No Public IPs, Location is West Europe Only, VM Size... |
| Developer creates a resource using YAML. |
| Crossplane checks against these "constraints or limits". |
| Only allowed and safe resources are actually created in the cloud. |
| <img src="Images/08-Crossplane-Policy-Security.jpg" alt="Crossplane-Policy-Security"> |

| 04: Setting up Crossplane with Azure:- |
| --------- |

| Requirements:- |
| --------- |

1. An AKS Cluster (In Azure Cloud)
2. Kubectl (Installed in your working Notbook/VM)
3. Kubelogin (Installed in your working Notbook/VM)
4. Helm (Installed in your working Notbook/VM)

| AKS Cluster Details:- |
| --------- |
| <img src="Images/09-AKS-Cluster-Details-1.jpg" alt="AKS-Cluster-Details"> |
| <img src="Images/10-AKS-Cluster-Details-2.jpg" alt="AKS-Cluster-Details"> |

- Subscription: __Visual Studio Enterprise Subscription__
- Resource group: __AM-CrossPlane-RG__
- Region: __West Europe__
- Kubernetes cluster name: __AM-Crossplane-AKS__
- SKU: __Base__
- Pricing Tier: __Standard__
- Kubernetes version: __1.32.9__
- Automatic upgrade: __patch__
- Automatic upgrade scheduler: __Every week on Sunday (recommended)__
- Node security channel type: __NodeImage__
- Security channel scheduler: __Every week on Sunday (recommended)__
- Node pools: __2__
- Node Size: __Standard_D2ps_v6__
- Enable virtual nodes: __Disabled__
- Local accounts: __Disabled__
- Authentication and Authorization: __Microsoft Entra ID authentication with Azure RBAC__
- Encryption type: __(Default) Encryption at-rest with a platform-managed key__
- Private cluster: __Not enabled__
- Authorized IP ranges: __Not enabled__
- Application Gateway Ingress Controller: __Not enabled__ 
- Network configuration: __Azure CNI Node Subnet__
- Virtual network: __AM-CrossPlane-AKS-VNet__
- Cluster subnet: __(new) Container-Subnet__
- Kubernetes service address range: __10.0.0.0/16__
- Kubernetes DNS service IP address: __10.0.0.10__
- DNS name prefix: __AM-Crossplane-AKS-dns__
- Network policy: __Azure__
- Load balancer: __Standard__
- Integrations: __Container registry__ 
- resource group: __AM-CrossPlane-RG__
- Container registry location: __West Europe__
- Container registry admin user: __Enabled__
- Container registry SKU: __Standard__
- Container registry: __(new) AMCrossPlaneACR__
- Service mesh: __Disabled__
- Azure Policy: __Disabled__
- Enable Container Logs: __Disabled__
- Enable Prometheus metrics: __Disabled__
- Azure Monitor workspace: __Not Enabled__
- Enable Grafana: __Disabled__
- Alert rules: __2 rules__
- Infrastructure resource group: __AM-CrossPlane-RG_AM-Crossplane-AKS_WestEurope__
- Microsoft Defender for Cloud: __Free__
- OpenID Connect (OIDC): __Enabled__
- Workload Identity: __Enabled__
- Image Cleaner: __Enabled__
- Tags: __None__

| Windows System on which below application was Installed ? |
| --------- |

I. __Install Kubectl on Windows.__

| Reference Link: https://community.chocolatey.org/packages/kubernetes-cli |
| --------- |

```
choco install kubernetes-cli
```

| Kubectl Installation Logs:- |
| --------- |

```
PS C:\Users\amadmin> choco install kubernetes-cli

Chocolatey v2.4.3
Installing the following packages:
kubernetes-cli
By installing, you accept licenses for the packages.
Downloading package from source 'https://community.chocolatey.org/api/v2/'
Progress: Downloading kubernetes-cli 1.33.0... 100%

kubernetes-cli v1.33.0 [Approved]
kubernetes-cli package files install completed. Performing other installation steps.
The package kubernetes-cli wants to run 'chocolateyInstall.ps1'.
Note: If you don't run this script, the installation will fail.
Note: To confirm automatically next time, use '-y' or consider:
choco feature enable -n allowGlobalConfirmation
Do you want to run the script?([Y]es/[A]ll - yes to all/[N]o/[P]rint): A

Extracting 64-bit C:\ProgramData\chocolatey\lib\kubernetes-cli\tools\kubernetes-client-windows-amd64.tar.gz to C:\ProgramData\chocolatey\lib\kubernetes-cli\tools...
C:\ProgramData\chocolatey\lib\kubernetes-cli\tools
Extracting 64-bit C:\ProgramData\chocolatey\lib\kubernetes-cli\tools\kubernetes-client-windows-amd64.tar to C:\ProgramData\chocolatey\lib\kubernetes-cli\tools...
C:\ProgramData\chocolatey\lib\kubernetes-cli\tools
 ShimGen has successfully created a shim for kubectl-convert.exe
 ShimGen has successfully created a shim for kubectl.exe
 The install of kubernetes-cli was successful.
  Deployed to 'C:\ProgramData\chocolatey\lib\kubernetes-cli\tools'

Chocolatey installed 1/1 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).

PS C:\Users\amadmin>

```

| Validate Post Installation:- |
| --------- |

```
PS C:\Users\amadmin> kubectl version --client
Client Version: v1.33.0
Kustomize Version: v5.6.0
PS C:\Users\amadmin>
```

II. __Install kubelogin on Windows.__

| Reference Link: https://community.chocolatey.org/packages/kubelogin  |
| --------- |

```
choco install kubelogin
```

| Kubelogin Installation Logs:- |
| --------- |

```
PS C:\Users\amadmin> choco install kubelogin
Chocolatey v2.4.3
Installing the following packages:
kubelogin
By installing, you accept licenses for the packages.
Downloading package from source 'https://community.chocolatey.org/api/v2/'
Progress: Downloading kubelogin 1.32.4... 100%

kubelogin v1.32.4 [Approved]
kubelogin package files install completed. Performing other installation steps.
The package kubelogin wants to run 'chocolateyInstall.ps1'.
Note: If you don't run this script, the installation will fail.
Note: To confirm automatically next time, use '-y' or consider:
choco feature enable -n allowGlobalConfirmation
Do you want to run the script?([Y]es/[A]ll - yes to all/[N]o/[P]rint): A

Extracting 64-bit C:\ProgramData\chocolatey\lib\kubelogin\tools\kubelogin_windows_amd64.zip to C:\ProgramData\chocolatey\lib\kubelogin\tools...
C:\ProgramData\chocolatey\lib\kubelogin\tools
Added C:\ProgramData\chocolatey\bin\kubectl-oidc_login.exe shim pointed to '..\lib\kubelogin\tools\kubelogin.exe'.
 ShimGen has successfully created a shim for kubelogin.exe
 The install of kubelogin was successful.
  Deployed to 'C:\ProgramData\chocolatey\lib\kubelogin\tools'

Chocolatey installed 1/1 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).
PS C:\Users\amadmin>
```


| Kubelogin ERROR Logs:- |
| --------- |

__AKS uses kubelogin plugin for authentication.__

> kubelogin convert-kubeconfig -l azurecli
```
PS C:\Users\amadmin> kubelogin convert-kubeconfig -l azurecli
error: unknown shorthand flag: 'l' in -l
```

| Troubleshooting:- |
| --------- |

Uninstall kubelogin using choco.
> choco uninstall kubelogin -y
```
PS C:\Users\amadmin> choco uninstall kubelogin -y
Chocolatey v2.4.3
Uninstalling the following packages:
kubelogin

kubelogin v1.32.4
Removing shim C:\ProgramData\chocolatey\bin\kubectl-oidc_login.exe which pointed to ''.
 Skipping auto uninstaller - No registry snapshot.
 kubelogin has been successfully uninstalled.

Chocolatey uninstalled 1/1 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).
PS C:\Users\amadmin>
```

__Install kubelogin using Azure Github: https://azure.github.io/kubelogin/install.html__

> winget install --id=Microsoft.Azure.Kubelogin  -e

```
PS C:\Users\amadmin> winget install --id=Microsoft.Azure.Kubelogin  -e
Found Microsoft Azure Kubelogin [Microsoft.Azure.Kubelogin] Version 0.2.8
This application is licensed to you by its owner.
Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
Downloading https://github.com/Azure/kubelogin/releases/download/v0.2.8/kubelogin-win-amd64.zip
  ██████████████████████████████  23.4 MB / 23.4 MB
Successfully verified installer hash
Extracting archive...
Successfully extracted archive
Starting package install...
Command line alias added: "kubelogin"
Successfully installed
PS C:\Users\amadmin>
```

| Validate Post Installation:- |
| --------- |

> kubelogin --version
```
PS C:\Users\amadmin> kubelogin --version
kubelogin version
git hash: v0.2.8/d7f1c16c95cc0a1a3beb056374def7b744a38b3a
Go version: go1.23.7
Build time: 2025-04-25T17:17:57Z
Platform: windows/amd64
PS C:\Users\amadmin>
```

__Get Credentials:-__

> az aks get-credentials --resource-group AM-CrossPlane-RG --name AM-Crossplane-AKS --overwrite-existing

```
PS C:\Users\amadmin> az aks get-credentials --resource-group AM-CrossPlane-RG --name AM-Crossplane-AKS --overwrite-existing
Merged "AM-Crossplane-AKS" as current context in C:\Users\amadmin\.kube\config
PS C:\Users\amadmin>
```

__Use kubelogin plugin for authentication:-__

> kubelogin convert-kubeconfig -l azurecli
```
PS C:\Users\amadmin> kubelogin convert-kubeconfig -l azurecli
PS C:\Users\amadmin>
```

> kubectl get nodes
```
PS C:\Users\amadmin> kubectl get nodes
NAME                                STATUS   ROLES    AGE     VERSION
aks-agentpool-15473826-vmss000000   Ready    <none>   5m36s   v1.32.9
aks-userpool-15473826-vmss000000    Ready    <none>   5m23s   v1.32.9
PS C:\Users\amadmin>
```

III. __Install Helm on Windows.__

| Reference Link: https://community.chocolatey.org/packages/kubernetes-helm |
| --------- |

```
choco install kubernetes-helm
```

| Helm Installation Logs:- |
| --------- |

```
PS C:\Users\amadmin> choco install kubernetes-helm
Chocolatey v2.4.3
Installing the following packages:
kubernetes-helm
By installing, you accept licenses for the packages.
Downloading package from source 'https://community.chocolatey.org/api/v2/'
Progress: Downloading kubernetes-helm 3.17.3... 100%

kubernetes-helm v3.17.3 [Approved]
kubernetes-helm package files install completed. Performing other installation steps.
The package kubernetes-helm wants to run 'chocolateyInstall.ps1'.
Note: If you don't run this script, the installation will fail.
Note: To confirm automatically next time, use '-y' or consider:
choco feature enable -n allowGlobalConfirmation
Do you want to run the script?([Y]es/[A]ll - yes to all/[N]o/[P]rint): A

Downloading kubernetes-helm 64 bit
  from 'https://get.helm.sh/helm-v3.17.3-windows-amd64.zip'
Progress: 100% - Completed download of C:\Users\amadmin\AppData\Local\Temp\2\chocolatey\kubernetes-helm\3.17.3\helm-v3.17.3-windows-amd64.zip (17.09 MB).
Download of helm-v3.17.3-windows-amd64.zip (17.09 MB) completed.
Hashes match.
Extracting C:\Users\amadmin\AppData\Local\Temp\2\chocolatey\kubernetes-helm\3.17.3\helm-v3.17.3-windows-amd64.zip to C:\ProgramData\chocolatey\lib\kubernetes-helm\tools...
C:\ProgramData\chocolatey\lib\kubernetes-helm\tools
 ShimGen has successfully created a shim for helm.exe
 The install of kubernetes-helm was successful.
  Deployed to 'C:\ProgramData\chocolatey\lib\kubernetes-helm\tools'

Chocolatey installed 1/1 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).
PS C:\Users\amadmin>
PS C:\Users\amadmin>

```

| Validate Post Installation:- |
| --------- |

```
PS C:\Users\amadmin> helm version
version.BuildInfo{Version:"v3.17.3", GitCommit:"e4da49785aa6e6ee2b86efd5dd9e43400318262b", GitTreeState:"clean", GoVersion:"go1.23.7"}
PS C:\Users\amadmin>
```

Step 1: __Install Crossplane into your Kubernetes Cluster:-__

> kubectl create namespace am-crossplane
```
PS C:\Users\amadmin> kubectl create namespace am-crossplane
namespace/am-crossplane created
PS C:\Users\amadmin>
```
> kubectl get namespace
```
PS C:\Users\amadmin> kubectl get namespace
NAME              STATUS   AGE
am-crossplane     Active   5s
default           Active   8m55s
kube-node-lease   Active   8m55s
kube-public       Active   8m55s
kube-system       Active   8m55s
PS C:\Users\amadmin>
```

> helm repo add crossplane-stable https://charts.crossplane.io/stable
```
PS C:\Users\amadmin> helm repo add crossplane-stable https://charts.crossplane.io/stable
"crossplane-stable" has been added to your repositories
PS C:\Users\amadmin>
```

> helm repo update
```
PS C:\Users\amadmin> helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "crossplane-stable" chart repository
Update Complete. ⎈Happy Helming!⎈
PS C:\Users\amadmin>
```

> helm install crossplane crossplane-stable/crossplane --namespace am-crossplane
```
PS C:\Users\amadmin> helm install crossplane crossplane-stable/crossplane --namespace am-crossplane
NAME: crossplane
LAST DEPLOYED: Mon Dec  8 20:49:28 2025
NAMESPACE: am-crossplane
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
Release: crossplane

Chart Name: crossplane
Chart Description: Crossplane is an open source Kubernetes add-on that enables platform teams to assemble infrastructure from multiple vendors, and expose higher level self-service APIs for application teams to consume.
Chart Version: 2.1.3
Chart Application Version: 2.1.3

Kube Version: v1.32.9
PS C:\Users\amadmin>
```

> kubectl get pods -n am-crossplane
```
PS C:\Users\amadmin> kubectl get pods -n am-crossplane
NAME                                       READY   STATUS    RESTARTS   AGE
crossplane-844dd5d9b-jzw4d                 1/1     Running   0          103s
crossplane-rbac-manager-7b4c99b894-jd4lg   1/1     Running   0          103s
PS C:\Users\amadmin>
```

> kubectl get deployments -n am-crossplane
```
PS C:\Users\amadmin> kubectl get deployments -n am-crossplane
NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
crossplane                1/1     1            1           2m3s
crossplane-rbac-manager   1/1     1            1           2m3s
PS C:\Users\amadmin>
```

Step 2: __Install the Azure Provider:-__

__The Crossplane Provider installs the Kubernetes Custom Resource Definitions (CRDs) representing Azure Networking services. These CRDs allow you to create Azure resources directly inside Kubernetes.__

__provider.yaml:-__
```
apiVersion: pkg.crossplane.io/v1
kind: Provider
metadata:
  name: provider-azure-network
spec:
  package: xpkg.crossplane.io/crossplane-contrib/provider-azure-network:v1.11.2
```

> kubectl get providers
```
PS C:\Users\amadmin> kubectl get providers
No resources found
PS C:\Users\amadmin>
```

> kubectl apply -f provider.yaml
```
PS C:\Users\amadmin> cd Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>

PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> kubectl apply -f provider.yaml
provider.pkg.crossplane.io/provider-azure-network created
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>

```

> kubectl get providers
```
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> kubectl get providers
NAME                                       INSTALLED   HEALTHY   PACKAGE                                                                AGE
crossplane-contrib-provider-family-azure   True        True      xpkg.crossplane.io/crossplane-contrib/provider-family-azure:v2.2.0     24s
provider-azure-network                     True        True      xpkg.crossplane.io/crossplane-contrib/provider-azure-network:v1.11.2   31s
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>
```

Step 3: __Create an Azure Service Principal:-__

> az ad sp create-for-rbac --sdk-auth --role Owner --scopes /subscriptions/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> az ad sp create-for-rbac --sdk-auth --role Owner --scopes /subscriptions/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Option '--sdk-auth' has been deprecated and will be removed in a future release.
Creating 'Owner' role assignment under scope '/subscriptions/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
The output includes credentials that you must protect. Be sure that you do not include these credentials in your code or check the credentials into your source control. For more information, see https://aka.ms/azadsp-cli
{
  "clientId": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "clientSecret": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "subscriptionId": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "tenantId": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>
```

Important Note: __Save your Azure JSON output as "azure-credentials.json".__

Step 4: __Create a Kubernetes secret with the Azure credentials:-__ 

__A Kubernetes generic secret has a name and contents. kubectl create secret will generate the secret object named "azure-secret" in the am-crossplane namespace. "--from-file=" argument is used to set the contents of the azure-credentials.json file.__

> kubectl create secret generic azure-secret -n am-crossplane --from-file=creds=./azure-credentials.json
```
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> kubectl create secret generic azure-secret -n am-crossplane --from-file=creds=./azure-credentials.json
secret/azure-secret created
PS C:\Users\amadmin\Desktop\Crossplane>
```

> kubectl describe secret azure-secret -n am-crossplane
```
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> kubectl describe secret azure-secret -n am-crossplane
Name:         azure-secret
Namespace:    am-crossplane
Labels:       <none>
Annotations:  <none>

Type:  Opaque

Data
====
creds:  639 bytes

PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>
```

Step 5: __Create Provider Config:-__ 

__Customize the settings of Azure Provider.__

__providerconfig.yaml:-__
```
apiVersion: azure.upbound.io/v1beta1
metadata:
  name: am-azure-provider-config
kind: ProviderConfig
spec:
  credentials:
    source: Secret
    secretRef:
      namespace: am-crossplane
      name: azure-secret
      key: creds
```

> kubectl apply -f providerconfig.yaml
```
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> kubectl apply -f providerconfig.yaml
providerconfig.azure.upbound.io/am-azure-provider-config created

PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>
```

Step 6: __Ensure CRDs are installed:-__

> kubectl get crds
```
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> kubectl get crds
NAME                                                                            CREATED AT
applicationgateways.network.azure.upbound.io                                    2025-12-08T20:05:36Z
applicationsecuritygroups.network.azure.upbound.io                              2025-12-08T20:05:33Z
bastionhosts.network.azure.upbound.io                                           2025-12-08T20:05:33Z
clusterproviderconfigs.azure.m.upbound.io                                       2025-12-08T20:05:33Z
clusterusages.protection.crossplane.io                                          2025-12-08T19:49:48Z
compositeresourcedefinitions.apiextensions.crossplane.io                        2025-12-08T19:49:47Z
compositionrevisions.apiextensions.crossplane.io                                2025-12-08T19:49:47Z
compositions.apiextensions.crossplane.io                                        2025-12-08T19:49:47Z
configurationrevisions.pkg.crossplane.io                                        2025-12-08T19:49:47Z
configurations.pkg.crossplane.io                                                2025-12-08T19:49:47Z
connectionmonitors.network.azure.upbound.io                                     2025-12-08T20:05:33Z
cronoperations.ops.crossplane.io                                                2025-12-08T19:49:47Z
ddosprotectionplans.network.azure.upbound.io                                    2025-12-08T20:05:33Z
deploymentruntimeconfigs.pkg.crossplane.io                                      2025-12-08T19:49:48Z
dnsaaaarecords.network.azure.upbound.io                                         2025-12-08T20:05:33Z
dnsarecords.network.azure.upbound.io                                            2025-12-08T20:05:33Z
dnscaarecords.network.azure.upbound.io                                          2025-12-08T20:05:33Z
dnscnamerecords.network.azure.upbound.io                                        2025-12-08T20:05:33Z
dnsmxrecords.network.azure.upbound.io                                           2025-12-08T20:05:33Z
dnsnsrecords.network.azure.upbound.io                                           2025-12-08T20:05:33Z
dnsptrrecords.network.azure.upbound.io                                          2025-12-08T20:05:33Z
dnssrvrecords.network.azure.upbound.io                                          2025-12-08T20:05:33Z
dnstxtrecords.network.azure.upbound.io                                          2025-12-08T20:05:33Z
dnszones.network.azure.upbound.io                                               2025-12-08T20:05:33Z
environmentconfigs.apiextensions.crossplane.io                                  2025-12-08T19:49:47Z
expressroutecircuitauthorizations.network.azure.upbound.io                      2025-12-08T20:05:33Z
expressroutecircuitconnections.network.azure.upbound.io                         2025-12-08T20:05:33Z
expressroutecircuitpeerings.network.azure.upbound.io                            2025-12-08T20:05:34Z
expressroutecircuits.network.azure.upbound.io                                   2025-12-08T20:05:33Z
expressrouteconnections.network.azure.upbound.io                                2025-12-08T20:05:34Z
expressroutegateways.network.azure.upbound.io                                   2025-12-08T20:05:33Z
expressrouteports.network.azure.upbound.io                                      2025-12-08T20:05:34Z
firewallapplicationrulecollections.network.azure.upbound.io                     2025-12-08T20:05:33Z
firewallnatrulecollections.network.azure.upbound.io                             2025-12-08T20:05:33Z
firewallnetworkrulecollections.network.azure.upbound.io                         2025-12-08T20:05:34Z
firewallpolicies.network.azure.upbound.io                                       2025-12-08T20:05:35Z
firewallpolicyrulecollectiongroups.network.azure.upbound.io                     2025-12-08T20:05:34Z
firewalls.network.azure.upbound.io                                              2025-12-08T20:05:34Z
frontdoorcustomhttpsconfigurations.network.azure.upbound.io                     2025-12-08T20:05:34Z
frontdoorfirewallpolicies.network.azure.upbound.io                              2025-12-08T20:05:34Z
frontdoorrulesengines.network.azure.upbound.io                                  2025-12-08T20:05:33Z
frontdoors.network.azure.upbound.io                                             2025-12-08T20:05:35Z
functionrevisions.pkg.crossplane.io                                             2025-12-08T19:49:48Z
functions.pkg.crossplane.io                                                     2025-12-08T19:49:48Z
imageconfigs.pkg.crossplane.io                                                  2025-12-08T19:49:48Z
imagejobs.eraser.sh                                                             2025-12-08T19:39:35Z
imagelists.eraser.sh                                                            2025-12-08T19:39:35Z
ipgroups.network.azure.upbound.io                                               2025-12-08T20:05:33Z
loadbalancerbackendaddresspooladdresses.network.azure.upbound.io                2025-12-08T20:05:34Z
loadbalancerbackendaddresspools.network.azure.upbound.io                        2025-12-08T20:05:34Z
loadbalancernatpools.network.azure.upbound.io                                   2025-12-08T20:05:34Z
loadbalancernatrules.network.azure.upbound.io                                   2025-12-08T20:05:34Z
loadbalanceroutboundrules.network.azure.upbound.io                              2025-12-08T20:05:34Z
loadbalancerprobes.network.azure.upbound.io                                     2025-12-08T20:05:33Z
loadbalancerrules.network.azure.upbound.io                                      2025-12-08T20:05:34Z
loadbalancers.network.azure.upbound.io                                          2025-12-08T20:05:35Z
localnetworkgateways.network.azure.upbound.io                                   2025-12-08T20:05:34Z
locks.pkg.crossplane.io                                                         2025-12-08T19:49:48Z
managedresourceactivationpolicies.apiextensions.crossplane.io                   2025-12-08T19:49:47Z
managedresourcedefinitions.apiextensions.crossplane.io                          2025-12-08T19:49:47Z
managermanagementgroupconnections.network.azure.upbound.io                      2025-12-08T20:05:34Z
managernetworkgroups.network.azure.upbound.io                                   2025-12-08T20:05:34Z
managers.network.azure.upbound.io                                               2025-12-08T20:05:34Z
managerstaticmembers.network.azure.upbound.io                                   2025-12-08T20:05:34Z
managersubscriptionconnections.network.azure.upbound.io                         2025-12-08T20:05:34Z
natgatewaypublicipassociations.network.azure.upbound.io                         2025-12-08T20:05:34Z
natgatewaypublicipprefixassociations.network.azure.upbound.io                   2025-12-08T20:05:35Z
natgateways.network.azure.upbound.io                                            2025-12-08T20:05:35Z
networkinterfaceapplicationsecuritygroupassociations.network.azure.upbound.io   2025-12-08T20:05:35Z
networkinterfacebackendaddresspoolassociations.network.azure.upbound.io         2025-12-08T20:05:34Z
networkinterfacenatruleassociations.network.azure.upbound.io                    2025-12-08T20:05:34Z
networkinterfaces.network.azure.upbound.io                                      2025-12-08T20:05:34Z
networkinterfacesecuritygroupassociations.network.azure.upbound.io              2025-12-08T20:05:34Z
operations.ops.crossplane.io                                                    2025-12-08T19:49:47Z
packetcaptures.network.azure.upbound.io                                         2025-12-08T20:05:35Z
pointtositevpngateways.network.azure.upbound.io                                 2025-12-08T20:05:36Z
privatednsaaaarecords.network.azure.upbound.io                                  2025-12-08T20:05:34Z
privatednsarecords.network.azure.upbound.io                                     2025-12-08T20:05:34Z
privatednscnamerecords.network.azure.upbound.io                                 2025-12-08T20:05:34Z
privatednsmxrecords.network.azure.upbound.io                                    2025-12-08T20:05:36Z
privatednsptrrecords.network.azure.upbound.io                                   2025-12-08T20:05:35Z
privatednsresolverinboundendpoints.network.azure.upbound.io                     2025-12-08T20:05:35Z
privatednsresolveroutboundendpoints.network.azure.upbound.io                    2025-12-08T20:05:35Z
privatednsresolvers.network.azure.upbound.io                                    2025-12-08T20:05:36Z
privatednssrvrecords.network.azure.upbound.io                                   2025-12-08T20:05:36Z
privatednstxtrecords.network.azure.upbound.io                                   2025-12-08T20:05:36Z
privatednszones.network.azure.upbound.io                                        2025-12-08T20:05:35Z
privatednszonevirtualnetworklinks.network.azure.upbound.io                      2025-12-08T20:05:35Z
privateendpointapplicationsecuritygroupassociations.network.azure.upbound.io    2025-12-08T20:05:35Z
privateendpoints.network.azure.upbound.io                                       2025-12-08T20:05:37Z
privatelinkservices.network.azure.upbound.io                                    2025-12-08T20:05:36Z
profiles.network.azure.upbound.io                                               2025-12-08T20:05:36Z
providerconfigs.azure.m.upbound.io                                              2025-12-08T20:05:33Z
providerconfigs.azure.upbound.io                                                2025-12-08T20:05:33Z
providerconfigusages.azure.m.upbound.io                                         2025-12-08T20:05:33Z
providerconfigusages.azure.upbound.io                                           2025-12-08T20:05:33Z
providerrevisions.pkg.crossplane.io                                             2025-12-08T19:49:48Z
providers.pkg.crossplane.io                                                     2025-12-08T19:49:48Z
publicipprefixes.network.azure.upbound.io                                       2025-12-08T20:05:36Z
publicips.network.azure.upbound.io                                              2025-12-08T20:05:36Z
resourcegroups.azure.m.upbound.io                                               2025-12-08T20:05:34Z
resourcegroups.azure.upbound.io                                                 2025-12-08T20:05:33Z
resourceproviderregistrations.azure.m.upbound.io                                2025-12-08T20:05:33Z
resourceproviderregistrations.azure.upbound.io                                  2025-12-08T20:05:34Z
routefilters.network.azure.upbound.io                                           2025-12-08T20:05:37Z
routemaps.network.azure.upbound.io                                              2025-12-08T20:05:37Z
routes.network.azure.upbound.io                                                 2025-12-08T20:05:36Z
routeserverbgpconnections.network.azure.upbound.io                              2025-12-08T20:05:37Z
routeservers.network.azure.upbound.io                                           2025-12-08T20:05:37Z
routetables.network.azure.upbound.io                                            2025-12-08T20:05:36Z
secretproviderclasses.secrets-store.csi.x-k8s.io                                2025-12-08T19:40:14Z
secretproviderclasspodstatuses.secrets-store.csi.x-k8s.io                       2025-12-08T19:40:15Z
securitygroups.network.azure.upbound.io                                         2025-12-08T20:05:37Z
securityrules.network.azure.upbound.io                                          2025-12-08T20:05:36Z
subnetnatgatewayassociations.network.azure.upbound.io                           2025-12-08T20:05:36Z
subnetnetworksecuritygroupassociations.network.azure.upbound.io                 2025-12-08T20:05:38Z
subnetroutetableassociations.network.azure.upbound.io                           2025-12-08T20:05:37Z
subnets.network.azure.upbound.io                                                2025-12-08T20:05:39Z
subnetserviceendpointstoragepolicies.network.azure.upbound.io                   2025-12-08T20:05:37Z
subscriptions.azure.m.upbound.io                                                2025-12-08T20:05:33Z
subscriptions.azure.upbound.io                                                  2025-12-08T20:05:33Z
trafficmanagerazureendpoints.network.azure.upbound.io                           2025-12-08T20:05:37Z
trafficmanagerexternalendpoints.network.azure.upbound.io                        2025-12-08T20:05:37Z
trafficmanagernestedendpoints.network.azure.upbound.io                          2025-12-08T20:05:37Z
trafficmanagerprofiles.network.azure.upbound.io                                 2025-12-08T20:05:39Z
usages.apiextensions.crossplane.io                                              2025-12-08T19:49:47Z
usages.protection.crossplane.io                                                 2025-12-08T19:49:48Z
virtualhubconnections.network.azure.upbound.io                                  2025-12-08T20:05:38Z
virtualhubips.network.azure.upbound.io                                          2025-12-08T20:05:38Z
virtualhubroutetableroutes.network.azure.upbound.io                             2025-12-08T20:05:37Z
virtualhubroutetables.network.azure.upbound.io                                  2025-12-08T20:05:39Z
virtualhubs.network.azure.upbound.io                                            2025-12-08T20:05:39Z
virtualhubsecuritypartnerproviders.network.azure.upbound.io                     2025-12-08T20:05:37Z
virtualnetworkgatewayconnections.network.azure.upbound.io                       2025-12-08T20:05:41Z
virtualnetworkgateways.network.azure.upbound.io                                 2025-12-08T20:05:40Z
virtualnetworkpeerings.network.azure.upbound.io                                 2025-12-08T20:05:39Z
virtualnetworks.network.azure.upbound.io                                        2025-12-08T20:05:38Z
virtualwans.network.azure.upbound.io                                            2025-12-08T20:05:39Z
volumesnapshotclasses.snapshot.storage.k8s.io                                   2025-12-08T19:39:46Z
volumesnapshotcontents.snapshot.storage.k8s.io                                  2025-12-08T19:39:46Z
volumesnapshots.snapshot.storage.k8s.io                                         2025-12-08T19:39:46Z
vpngatewayconnections.network.azure.upbound.io                                  2025-12-08T20:05:40Z
vpngateways.network.azure.upbound.io                                            2025-12-08T20:05:39Z
vpnserverconfigurationpolicygroups.network.azure.upbound.io                     2025-12-08T20:05:38Z
vpnserverconfigurations.network.azure.upbound.io                                2025-12-08T20:05:38Z
vpnsites.network.azure.upbound.io                                               2025-12-08T20:05:38Z
watcherflowlogs.network.azure.upbound.io                                        2025-12-08T20:05:40Z
watchers.network.azure.upbound.io                                               2025-12-08T20:05:38Z
watchoperations.ops.crossplane.io                                               2025-12-08T19:49:47Z
webapplicationfirewallpolicies.network.azure.upbound.io                         2025-12-08T20:05:39Z

PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>
```

| 05: Deploying Azure resources using Crossplane:- |
| --------- |

__rg.yaml:-__

```
apiVersion: azure.upbound.io/v1beta1
kind: ResourceGroup
metadata:
  name: am-100
spec:
  forProvider:
    location: West Europe
  providerConfigRef:
    name: am-azure-provider-config
```

> kubectl apply -f rg.yaml
```
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> kubectl apply -f rg.yaml
resourcegroup.azure.upbound.io/am-100 created

PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>
```

__Resource group "am-100" was successfully created.__

| <img src="Images/11-Crossplane-rg.jpg" alt="Crossplane-rg"> |
| --------- |

| 06: Delete Azure resources using Crossplane - Command-Line:- |
| --------- |

> kubectl delete resourcegroup.azure.upbound.io am-100
```
PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg> kubectl delete resourcegroup.azure.upbound.io am-100
resourcegroup.azure.upbound.io "am-100" deleted

PS C:\Users\amadmin\Desktop\AM-12042025\Festive-Calendar-2025\Crossplane-Powered-Platform-Engg>
```

__Hope You Enjoyed the Session!!!__

__Stay Safe | Keep Learning | Spread Knowledge__

