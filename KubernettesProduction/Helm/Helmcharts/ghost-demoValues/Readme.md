helm install -n ghost-demo .
helm del --purge ghost-demo


# template Call

{{.Release.Name}} insert a release name in to YAML template

# Test template before rendering and intall
helm install --debug --dry-run ./mychart

helm create
helm fetch - download and  unpack a chart from a repo
    helm fetch -d . stable/kibana
helm rollback [flags] [RELEASE] [REVISION]
helm status - release status
helm upgrade


helm status
  494  helm list
  495  helm create -h
  496  helm create quick-demo
  497  cd quick-demo/
  498  ls
  499  vi
  500  vim

   501  helm fetch -d . stable/kibana
  502  helm fetch -d . stable/kibana --untar
  503  history
  501  helm install -n kibana-demo .
  502  helm status kibana
  503  helm status kibana-demo
PASML-335382:Helmcharts jjacob151$ helm history kibana-demo
REVISION        UPDATED                         STATUS          CHART           DESCRIPTION     
1               Thu May  2 19:28:25 2019        DEPLOYED        kibana-2.3.0    Install complete

helm upgrade  kibana-demo

pip fix

 python3 -m pip install --user --upgrade pip==9.0.3
 pip install --disable-pip-version-check --user --upgrade pip

vagrant status
vagrant ssh-config
 /Users/jjacob151/.vagrant.d/insecure_private_key
  IdentityFile /Users/jjacob151/.vagrant.d/insecure_private_key
pip install --disable-pip-version-check --user --upgrade pip