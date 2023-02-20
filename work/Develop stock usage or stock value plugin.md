stockvalue and stock usage uses [[Cumulio]] plugins so you will need to change the env variable to point to your local dataset(okteto service ds) instead of the staging dataset

So continue with these steps

1. find the env name by searching for stoackvalue or stockplugin foloowed by PLUGIN_BASE_URL for example 👇
2. set env on deployment  
`kubectl set env deploy/cumulio CUMULIO_STOCKUSAGE_PLUGIN_BASE_URL=``[https://cumulio-aa-ahmed-aa.katana.okteto.dev/api/stockusage](https://cumulio-aa-ahmed-aa.katana.okteto.dev/api/stockusage)`
3. scale to 0 then 1 again to reflect the change for the `katana-insights` service