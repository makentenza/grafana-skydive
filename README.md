# grafana-skydive
Skydive for OCP and Grafana with skydive DataSource plugin

      # oc new-project skydive
      # oc create -f https://raw.githubusercontent.com/makentenza/grafana-skydive/master/kube/grafana-skydive.json
      # oc adm policy add-scc-to-user anyuid system:serviceaccount:skydive:grafana
