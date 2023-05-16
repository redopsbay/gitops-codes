# My Hugo Site 😎

[https://alfredvalderrama.gitops.codes](https://alfredvalderrama.gitops.codes)

# Hugo Development 🚧 ##


### Creating the site 
```bash
docker run --rm -it \
    -v "$(pwd)":/src \
    klakegg/hugo:0.107.0-ext-ubuntu new site hugo
```

### Downloading the theme
```bash
cd hugo/
git submodule add https://github.com/kaapiandcode/hugo-goa themes/hugo-goa 
```


### Starting hugo server
```bash
docker run --rm -it \
    -v "$(pwd)":/src \
    -p 1313:1313 \
    klakegg/hugo:0.107.0-ext-ubuntu \
  server --disableFastRender --navigateToChanged
```


### Compiling the hugo site
```bash
docker run --rm -it \
    -v $(pwd):/src \
    klakegg/hugo:0.107.0-ext-ubuntu \
    --gc \
    --minify \
    --baseURL "https://alfredvalderrama.gitops.codes"
```

### Running the static site
```bash
pushd public/
docker run --rm \
    -it \
    -p 8080:80 \
    --name nginx-server \
    -v $(pwd):/usr/share/nginx/html nginx:1.23.4
popd
```