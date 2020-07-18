# Prometheus Solr Exporter

[Prometheus Solr Exporter](https://lucene.apache.org/solr/guide/7_5/monitoring-solr-with-prometheus-and-grafana.html) is an open source for Solr that return Solr's metrics into Prometheus server.
You can easily use it to visualize through Grafana or any related applications.

## TL;DR;

```bash
$ helm install --name prometheus-solr-exporter ./prometheus-solr-exporter  # to install with helm chart
$ helm upgrade prometheus-solr-exporter ./prometheus-solr-exporter         # to upgrade with any changes
```

## Result
```bash
# Using kubernetes port fowarding to forward service port to localhost
$ curl 127.0.0.1:8080/metrics

# HELP solrmaster_filtered_metrics_node_core_root_fs_bytes See following URL: https://lucene.apache.org/solrtopic/guide/7_1/metrics-reporting.html
# TYPE solrmaster_filtered_metrics_node_core_root_fs_bytes gauge
solrtopic_filtered_metrics_node_core_root_fs_bytes{base_url="http://node01:8080/solr",category="CONTAINER",item="totalSpace",} 9.44993685504E11
solrtopic_filtered_metrics_node_core_root_fs_bytes{base_url="http://node01:8080/solr",category="CONTAINER",item="usableSpace",} 1.50457090048E11
# HELP solr_exporter_duration_seconds Time this Solr exporter took, in seconds.
# TYPE solr_exporter_duration_seconds gauge
solr_exporter_duration_seconds 0.792496262
# HELP solr_exporter_scrape_error_total Number of scrape error.
# TYPE solr_exporter_scrape_error_total counter
solr_exporter_scrape_error_total 0.0

```

### Visualize Solr's metrics on Grafana
![solr_grafana](https://lucene.apache.org/solr/guide/7_5/images/monitoring-solr-with-prometheus-and-grafana/grafana-solr-dashboard.png)


Tested on Helm chart v2.0

You can define more metrics by editing file `templates/configmap.yaml` in `solrtopic.xml`. Find out more available metric report [here](https://lucene.apache.org/solr/guide/7_5/metrics-reporting.html)
