# Kubernetes tinkering 
*(Based on Stephen Grider Docker & Kubernetes course)*

### Notes (Running hyper-v / Docker on Win Home)
* Hyper-V requires abit of hacking on Win 10 Home too, check Docker on Win10 Home folder for scripts that let you enable hyper-v there.

### Notes (Running k8s on Win & hyper-v)
* Running minikube based on Hyper-V requires additional config passed, best approach is to set them pernament with `minikube config set`.
    * `hyperv-virtual-switch=Minikube_VSwitch` // *your name on vswitch*
    * `vm-driver=hyperv` // *sets driver from default virtualbox to hyperv*
* Accessing minikube virtual machine requires ssh which basic PowerShell terminal doesn't have, thus may cause issues (occurred randomly to me).
OpenSSH which resolves them can be done by chocolatey pkg manager `choco install openssh`.
* Adding virtual switch outer network (based on physical network adapter) causes lags in internet connection (still unresolved).
  [Reddit: some idea on how that might be resolved](https://www.reddit.com/r/sysadmin/comments/2k7jn5/after_2_years_i_have_finally_solved_my_slow/)
### Notes on passing configs with kubectl
minikube installation setup kubectl client version different than on virtual machine (server) thus it might be a reason for `kubectl create` command to not work. 
You can skip verification by passing additional `--validate=false` - with that your configs are passed properly and creates what config demands w/o any issues.

### Author
Dariusz Kobuszewski