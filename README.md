# grafana-dashboard-sonarr
A Sonarr dashboard implemented using Grafana Infinity datasource


The intent here is to add Grafana dashboard features for a Sonarr v3 API, using Grafana Infinity as a datasource.

Grafana Infinity has been selected for its JSON support, query caching, and the fact that it doesn't require a datasource + exporter to function.

Grafana Infinity runs the queries from the Grafana instance, rather than using an exporter application to query Sonarr, transform the data, store it in a separate database or metrics gathering instance, and retrieving these metrics with Grafana.

Documenttation will improve, this is just scratching details down while I work.

To Install the Grafana Infinity plugin:
- log into Grafana
- Add New Connection from hamburger menu on left
- search Grafana Infinity
- Select plugin
- click Install

To add the Sonarr API data source:
- log into Grafana
- Data sources
- Add New Data source
- Name: Sonarr v3 JSON API ((OR your own name. This datasource will only work with this Sonarr instance, as the API auth is required in a header.))
- Search/select Grafana Infinity
- Ignore Main tab w/ Setup Authentication button
- Autnetication tab; No auth
- Headers & URL params
--- Add Custom HTTP Header; Key: `X-Api-Key`  Value: ((Your Sonarr API Key))
- Security
--- Add your Sonarr URL under Allowed Hosts. Include protocol, IP/hostname, and port. Ex: `http://192.168.33.33:8989`
- Health check
--- Add your Sonarr URL with the path `/api/v3/health` appended. Ex: `http://192.168.33.33:8989/api/v3/health`
- Save & Test

