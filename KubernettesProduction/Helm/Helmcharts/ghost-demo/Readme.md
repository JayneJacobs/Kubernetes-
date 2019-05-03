helm install -n ghost-demo .
helm del --purge ghost-demo


# template Call

{{.Release.Name}} insert a release name in to YAML template

# Test template before rendering and intall
helm install --debug --dry-run ./mychart


