Komenda [![Build Status](https://travis-ci.org/cargomedia/komenda.svg)](https://travis-ci.org/cargomedia/komenda)
=======
Komenda is a convenience wrapper around `Open3` to run shell commands in Ruby.

Usage
-----
Run a command:
```ruby
Komenda.run("date")
```

The `run()` method will block until the sub process finished.

It will expose the output and exit status as a `Komenda::Result` value:
```ruby
result = Komenda.run("date")
result.stdout   # => "Tue Nov 26 14:45:03 EST 2013\n"
result.stderr   # => ""
result.output   # => "Tue Nov 26 14:45:03 EST 2013\n" (combined stdout + stderr)
result.status   # => 0
result.success? # => true
result.pid      # => 32157
```

The `run()` method has a second argument `options`, which expects these keys:
- **`env`** (Hash): The environment variables to use. Defaults to the current process' environment.

Development
-----------
Install dependencies:
```
bundle install
```

Run the tests:
```
bundle exec rake spec
```

TODO
----
Add options for:
- Passing STDIN
- Making `run()` fail when exit status is not "0"
