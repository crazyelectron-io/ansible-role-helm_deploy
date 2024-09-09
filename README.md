# Ansible Role: Helm_deploy

This role can be included to install the specified [Helm](https://helm.sh) repository in the specified namespace.

## Requirements

N/A

## Role Variables

Required variables are listed below, which have no default value (see also `defaults/main.yml`):

`helm_chart_chart_name` - the name of the Helm chart to install.

`helm_chart_release_name` - the name of the Helm release to install.

`helm_chart_version` - the version of the Helm chart to install.

`helm_chart_url` - the Helm chart URL.

`helm_chart_repository` - the Helm repository name.

`helm_chart_namespace` - the namespacr to install the Helm chart in. Will be created if it does not exist.

`helm_chart_wait` - wait for thr Helm chart resources to be deployed if `true`.

`helm_chart_values_file` - relative path  (for the calling rolr) and name of the `values.yaml` file that holds the Helm chart varaiables.

## Dependencies

The role requireds the Helm binary to be installed.

## Example Role

```yaml
- ansible.builtin.include_role:
    name: helm-deploy
  vars:
    helm_chart_chart_name: "{{authentik_chart_name}}"
    helm_chart_release_name: "{{authentik_release_name}}"
    helm_chart_version: "{{authentik_chart_version}}"
    helm_chart_url: "{{authentik_chart_url}}"
    helm_chart_repository: "{{authentik_repo_name}}"
    helm_chart_namespace: "{{authentik_namespace}}"
    helm_chart_wait: false
    helm_chart_values_file: "templates/authentik_values.yaml.j2"
```

## License

MIT / BSD
