# API Ops Deep Dive

## Inso
### Generate Kong Deck config from swagger file
```
inso generate config api/petstore_swagger.yaml -o deck/kong_deck_config_petstore.yaml
``` 

## Deck 
### convert 2.x to 3.x gateway config
```
deck convert --from kong-gateway-2.x --to kong-gateway-3.x --input-file deck/kong_deck_config_petstore.yaml --output-file deck/kong_deck_config_petstore_3x.yaml
```

### tags with meta.yaml file
```
deck sync --headers 'Kong-Admin-Token:heyho' --kong-addr https://adminapi.km.kong-cx.com:8444 -s deck/kong_deck_config_petstore_3x.yaml -s meta/meta.yaml
```

### tags via cli
```
deck sync --headers 'Kong-Admin-Token:heyho' --kong-addr https://adminapi.km.kong-cx.com:8444 -s deck/kong_deck_config_petstore_3x.yaml --select-tag test1,test2
```

### deploy with plugin as folder
```
deck sync --headers 'Kong-Admin-Token:heyho' --kong-addr https://adminapi.km.kong-cx.com:8444 -s deck/kong_deck_config_petstore_3x.yaml -s plugins/
```