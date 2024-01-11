copy env from service to another

```
heroku config:set $(heroku config -s -a [source-app] |grep -v '^HEROKU_') -a [destination-app]
```