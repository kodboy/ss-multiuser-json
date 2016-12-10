## dependences

* python2.7
* pip
* virtualenv

## setup

1. clone this repo
2. `virtualenv /path/to/repo/`
3. `source /path/to/repo/bin/activate`
4. `pip install -r /path/to/repo/requirements.txt`
5. `python app.py`


## config
1. you can change the hash key in `app.py` as `hashkey` at the first line.if `hashkey` is set to `None`, the hash checking will be off
2. you can set the listener url in `app.py` as `url` at the second line.if `url` is set to `None` this function will be off.
3. you can change the hash string format in `app.py` as `hash_str_format` at the third line.Please make sure you have all the three predefined compoments included.

## usage
#### api
    //add a port
    PUT http://128.0.0.1:3000 HTTP/1.1
    SS-Hash: a87209962d6e79c72f023bbf3178de33
    Content-Type: application/json

    {
        "port": 8821,
        "password": "yes your"
    }

    //remove a port
    DELETE  http://127.0.0.1:3000 HTTP/1.1
    SS-Hash: a87209962d6e79c72f023bbf3178de33
    Content-Type: application/json

    {
        "port": 8821
    }
    //ping
    GET  http://127.0.0.1:3000 HTTP/1.1
    SS-Hash: a87209962d6e79c72f023bbf3178de33
    Content-Type: application/json
#### listener
See https://github.com/shadowsocks/shadowsocks/wiki/Manage-Multiple-Users.

    # when data is transferred on Shadowsocks, you'll receive stat info every 10 seconds

This data will be proxy to the url that set before.

#### hash checking

the hash caculation can be described as

1. put http method, request body and hash key togather with the format like as strings

    method:body-key
2. caculate the md5 value of the string


