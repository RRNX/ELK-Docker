# Funktionsweise
Ein ELK-Cluster besteht wie der Name bereits sagt aus Elasticsearch, Logstash und Kibana. Logstash ist ein Tool, mit dem verschieden Logs oder andere Daten in z.B. JSON kompatible Formate gewandelt werden können. Insbesondere ist es nützlich für Monitoring Zwecke. Elasticsearch ist eine Art Datenbank, die anders als z.B. MySQL auf JSON-Dokumente basiert. Sie arbeitet mithilfe der Lucene Engine von Apache und ist somit auch mit größeren Datenmengen sehr performant. Kibana ergänzt Elasticsearch um ein UI, was sonst nicht in ES enhalten ist. Kibana bietet zudem seit ein paar Jahren die Möglichkeit Daten von Elasticsearch zu visualisieren. 

Zusammenfassend kann man sagen, dass die Kombination eines ELK Clusters mit z.B. [Beats](https://www.elastic.co/de/beats) eine wunderbare Möglichkeit bietet, verschiedenste Daten eines oder mehrerer Systeme zu Monitoren.

# Umsetzung
Zur Umsetzung meiner Aufgabe nutze ich 2 Dockercontainer. Einer davon enthält das ELK-Cluster, der andere einen Metricbeat, der für die bereitstellung demonstrativer Daten zuständig ist. Für eine einfacherere Bedienung habe ich eine docker-compose.yml erstellt, um die beiden Container besser zu verwalten.

Die Einstellungen für die Container sind im configs Ordner. Eine weitere Einstellung die ich vorgenommen habe ist die Deaktivierung von SSL. Leider musste ich besonders im ELK Docker Image feststellen, dass die SSL Einstellung nicht so funktionierte, wie ich es bereits von dediziierten Servern kannte. Für eine Demo sollte das allerdings reichen. Andere wichtige Einstellung sind die Heap Sizes von ES und LS. Bei beiden Instanzen sollte man besonders darauf aufpassen, das beide Tools genügend Heap zur Verfügung haben, insbesondere wenn man größere Mengen an Daten verarbeiten muss. Besonders für Zeitlich relevante Daten ist die Einstellung der TimeZone ebenfalls von großer Bedeutung.

# Dashboards
Wie bereits zuvor erwähnt bietet Kibana die Möglichkeit Dashboards für die Daten zu erstellen. Ein einfaches Beispiel sieht man [hier](https://www.elastic.co/guide/en/kibana/current/images/lens_logsDashboard_8.4.0.png). Hier kommt es sehr darauf an, welche Daten genau visualisiert werden sollen.

Mehr über [Elasticsearch](https://www.elastic.co/de/elasticsearch), [Logstash](https://www.elastic.co/de/logstash), [Kibana](https://www.elastic.co/de/kibana) und dem [ELK Image](https://elk-docker.readthedocs.io/).