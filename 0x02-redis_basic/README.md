0x02. Redis basic
=
How to Use Redis With Python
=
redis-py (which you import as just redis) is one of many Python clients for Redis, but it has the distinction of being billed as “currently the way to go for Python” by the Redis developers themselves. It lets you call Redis commands from Python, and get back familiar Python objects in return.

<h2>Install Redis on Ubuntu 18.04</h2>

      $ sudo apt-get -y install redis-server
      $ pip3 install redis
      $ sed -i "s/bind .*/bind 127.0.0.1/g" /etc/redis/redis.conf

<h2>Quickly connecting to redis</h2>

There are two quick ways to connect to Redis.

* Assuming you run Redis on localhost:6379 (the default)

           import redis
           r = redis.Redis()
           r.ping()

* Running redis on foo.bar.com, port 12345

              import redis
              r = redis.Redis(host='foo.bar.com', port=12345)
              r.ping()

* Another example with foo.bar.com, port 12345

              import redis
              r = redis.from_url('redis://foo.bar.com:12345')
              r.ping()