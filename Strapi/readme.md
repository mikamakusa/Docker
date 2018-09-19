# To build it

Execute the following command :  

- If you use Docker behind a proxy :  
```bash
docker build . -t <i>image_name</i> --build-arg URL_PROXY=<i>proxy_address</i> --build-arg LOGIN_PROXY=<i>login_proxy</i> --build-arg PASS_PROXY=<i>proxy_password</i> --build-arg STRAPI_SCRIPT=<i>startup_script</i> --build-arg STRAPI_VERSION=<i>strapi_version</i>
```

- If you are not behind a proxy : 
```bash
docker build . -t <i>image_name</i> --build-arg STRAPI_SCRIPT=<i>startup_script</i> --build-arg STRAPI_VERSION=<i>strapi_version</i>
```