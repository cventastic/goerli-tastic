#### Hardware Requirements 

For [Erigon](https://github.com/ledgerwatch/erigon#system-requirements)

As of 7th Nov 2022 goerli archive database size is 340 GB

#### Instructions:

Copy default.env to .env

```
cp default.env .env
```

Fill out .env \
For example:
```
# put your Domain in here
DOMAIN=my.domain.com

# put the speed you want to download/upload with here (mb/s)
DOWNLOAD_SPEED=1000mb
UPLOAD_SPEED=1000mb

# put the IPs you want to access the RPC from (comma seperated)
WHITELIST=192.168.1.1,192.168.1.2

# put the e-mail you want to use for LetsEncrypt notifications about your certificate here:
MAIL=mail@my.domain.com
```

Create a JWT-Token for authentication between consensus- and execution-client:
```
openssl rand -hex 32 | tr -d "\n" > .jwtsecret
```

Start container:

```
docker-compose -f goerli.yml up -d
```

Depending on the Domain used in .env-File earlier. \
RPC is available at 

```https://my.domain.com/erigon-goerli```

(But only from the IPs in .env WHITELIST defined earlier)

RPC is also locally available at:

```http://127.0.0.1:8545/```
