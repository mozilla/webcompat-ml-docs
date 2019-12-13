**************
Elasticsearch
**************

Currently our source of truth for data related to webcompat ML is our Elasticsearch database.
It's purpose is both to allow the webcompat team query and visualize webcompat data,
but also to be a source for building the model datasets.

The indexing of new data is handled by a cron-job that fetches new issues and events using
the GitHub API.

The Kibana web UI is available `here <https://webcompat-kibana.herokuapp.com/>`_ and is secured
using Mozilla IAM.

For more information: `mozilla/webcompat-search <https://github.com/mozilla/webcompat-search>`_
