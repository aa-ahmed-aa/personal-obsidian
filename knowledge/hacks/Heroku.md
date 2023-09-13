list all service names with domains attached to it

```
#!/bin/bash

# Get a list of Heroku app names in JSON format
heroku_apps=$(heroku apps -A --json)

# Loop through the app names and retrieve their domain names
for site in $(echo "$heroku_apps" | jq -r '.[] | .["name"]'); do
  domain=$(heroku domains --app "$site" --json | jq -r '.[0] | .["hostname"]')
  printf "%s: %s\n" "$site" "$domain"
done
```