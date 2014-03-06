## How To - Data Import to SPHERE.IO

The following steps are using [cURL](http://curl.haxx.se/) as HTTP client.

### Authentication
* First you need to authenticate to get an access token ("bearer token")
* use the returned access token further HTTP API calls

```bash
curl https://clientID:clientSecret@auth.sphere.io/oauth/token \
	-X POST \
    -d "grant_type=client_credentials&scope=manage_project:redbull"
```

See [HTTP API Tutorial](http://www.commercetools.de/dev/http-api-tutorial.html) for further information.

### Create Product Types
* generate product types files in JSON format using [sphere-product-type-json-generator](https://github.com/svenmueller/sphere-product-type-json-generator)
* use HTTP API to create types

```bash
curl -X POST -H "Authorization: Bearer [token]" https://api.sphere.io/redbull/product-types \
	-d @product-type-clothing.json
```

### Import Products
* import products from CSV using [sphere-node-product-csv-sync
](https://github.com/sphereio/sphere-node-product-csv-sync)
```bash
node lib/run.js import --projectKey KEY --clientId ID --clientSecret secret -l de --csv products.csv
```