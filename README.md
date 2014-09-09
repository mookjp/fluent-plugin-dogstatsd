# fluent-plugin-dogstatsd

Fluend plugin for Dogstatsd, that is statsd server for Datadog.

## Installation

    $ gem install fluent-plugin-dogstatsd

## Usage

```
$ echo '{"type": "increment", "key": "apache.requests", "tags": {"url", "/"}}' | fluent-cat dogstatsd.hello
$ echo '{"type": "histogram", "key": "apache.response_time", "value": 10.5, "tags": {"url": "/hello"}}' | fluent-cat dogstatsd.hello
$ echo '{"type": "event", "title": "Deploy", "text": "New revision"}' | fluent-cat dogstatsd.hello
```

Supported types are `increment`, `decrement`, `count`, `gauge`, `histogram`, `timing`, `set` and `event`.

## Configuration

```
<match dogstatsd.*>
  type dogstatsd

  # Dogstatsd host
  host localhost

  # Dogstatsd port
  port 8125

  # Use tag of fluentd record as key sent to Dogstatsd
  use_tag_as_key false
</match>
```

## Contributing

1. Fork it ( https://github.com/ryotarai/fluent-plugin-dogstatsd/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
