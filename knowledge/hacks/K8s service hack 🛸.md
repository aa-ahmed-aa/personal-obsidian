the `selector` on the service is selecting pods or labeled podds on the deployment to create a list of pods later to round robin requests to 

SO [[devspace]] uses this hack to develop on the remote cluster by cloning replica owner and scalling down the main replica owner to 0 so this way the selected pdos list will contain the newly deployed one  😤