## Skydive for OCP and Grafana with skydive DataSource plugin

Use the following instructions to deploy the full stack, Skydive + Grafana with Skydive plugin. Note that the Skydive Agent is configured to get information from the SDN using ovs-multitenant plugin:

      # oc new-project skydive
      # oc create -f https://raw.githubusercontent.com/makentenza/grafana-skydive/master/kube/skydive-template.json
      # oc new-app skydive
        --> Deploying template skydive

        --> Creating resources with label app=skydive ...
            service "skydive-analyzer" created
            deploymentconfig "skydive-analyzer" created
            daemonset "skydive-agent" created
            route "skydive-analyzer" created
        --> Success
            Run 'oc status' to view your app.

      In order to deploy all the skydive agents across your Nodes, label them accordingly:

      # oc label nodes --all skydive=true

As soon as the agent Pods are running, you will see all your Cluster topology in your Skydive Analyzer wen interface.

![Topology](img/skydive01.png)


      # oc create -f https://raw.githubusercontent.com/makentenza/grafana-skydive/master/kube/grafana-skydive.json
      # oc adm policy add-scc-to-user anyuid system:serviceaccount:skydive:grafana
