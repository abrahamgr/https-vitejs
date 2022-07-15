# HTTPS Vitejs

This example show you how to use HTTPS and Vitejs

## Generate certificates
We need to make sure `mkcert` and `nss` are installed if not you can installit running the following:

``` bash
# Step: 1
# Install mkcert tool - macOS; you can see the mkcert repo for details
brew install mkcert

# Step: 2
# Install nss (only needed if you use Firefox)
brew install nss

# Step: 3
# Setup mkcert on your machine (creates a CA)
mkcert -install
```

It will save the certificates in the project folder but you can change it if needed, just change the command `cert` in the `package.json`

Generates the certificates locally

`npm run cert`


## Configure Vite
Now we have the certificates generated we need to add the following configuration

``` js
// vite.config.js
server: {
  https: {
    key: fs.readFileSync('./key.pem'),
    cert: fs.readFileSync('./localhost.pem')
  }
}
```

Install modules

`npm i`

Run the app

`npm run dev`