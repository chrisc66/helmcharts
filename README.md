# helmcharts

This is a test repo to verify `index.yaml` can include absolute url to github releases.

#### `index.yaml`

This file contains a URL to the binary helm chart. This URL needs to be updated once the chart in included in an OpenJ9 release.
```
...
    name: openj9-jitserver-chart
    urls:
    - https://github.com/chrisc66/helmcharts/releases/download/v0.0.1/openj9-jitserver-chart-0.24.0.tgz
...
```

#### Helm CLI configuration

The `helm` CLI can be configured using below steps. The last step (`helm fetch`) downloads the binary helm chart to my local storage, which indicates `helm` CLI is able to fetch this helm chart from GitHub release URL.
```
$ helm repo add test-openj9 https://raw.githubusercontent.com/chrisc66/helmcharts/master/
"test-openj9" has been added to your repositories

$ helm repo list
NAME       	URL
ibm-charts 	https://raw.githubusercontent.com/IBM/charts/master/repo/stable/
test-openj9	https://raw.githubusercontent.com/chrisc66/helmcharts/master/

$ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "ibm-charts" chart repository
...Successfully got an update from the "test-openj9" chart repository
Update Complete. ⎈ Happy Helming!⎈

$ helm fetch test-openj9/openj9-jitserver-chart
```

