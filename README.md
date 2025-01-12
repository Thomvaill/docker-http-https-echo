Docker image which echoes various HTTP request properties back to client, as well as in docker logs. 

![browser](https://raw.githubusercontent.com/mendhak/docker-http-https-echo/master/screenshots/screenshot.png)

## Usage

    docker run -p 8080:8080 -e HTTP_PORT=8080 -p 8443:8443 -e HTTPS_PORT=8443 --rm -t mendhak/http-https-echo

Then issue a request via your browser or curl -

    curl -k -X PUT -H "Arbitrary:Header" -d aaa=bbb https://localhost:8443/hello-world



## Docker Compose

You can substitute the certificate and private key with your own. This example uses the snakeoil cert.

    my-http-listener:
        image: mendhak/http-https-echo
        ports:
            - "8080:80"
            - "8443:443"
        volumes:
            - /etc/ssl/certs/ssl-cert-snakeoil.pem:/app/fullchain.pem
            - /etc/ssl/private/ssl-cert-snakeoil.key:/app/privkey.pem



## Output

#### Curl output

![curl](https://raw.githubusercontent.com/mendhak/docker-http-https-echo/master/screenshots/screenshot2.png)

#### `docker logs` output

![dockerlogs](https://raw.githubusercontent.com/mendhak/docker-http-https-echo/master/screenshots/screenshot3.png)



## Building

    docker build -t mendhak/http-https-echo .


