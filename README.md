cuid
====

Collision-resistant ids optimized for horizontal scaling and sequential lookup performance,
written in Elixir.

For full rationale behind CUIDs refer to the [main project site](http://usecuid.org).


### Usage

Add Cuid as a dependency in your `mix.exs` file:

```elixir
defp deps do:
    [{:cuid, "~> 0.1.0"}]
end

```elixir
{:ok, pid} = Cuid.start_link
Cuid.create_cuid(pid)  # => ch72gsb320000udocl363eofy
Cuid.create_slug(pid)  # => xi0033t1jo
```

Each CUID is made by the following groups: `c - h72gsb32 - 0000 - udoc - l363eofy`

* `c` identifies this as a cuid, and allows you to use it in html entity ids. The fixed value helps keep the ids sequential.
* `h72gsb32` is a timestamp
* `0000` is a counter
* `udoc` is a fingerprint. The first two characters are based on the process ID and the next two are based on the hostname. This is the same method used in the [Node implementation](https://github.com/ericelliott/cuid/blob/master/src/node-fingerprint.js)
* `l363eofy` random (uses `:rand.uniform`)

Each SLUG is made by the following groups: `xi - 0033 - t - 1 - jo`

* `xi` are the last two characters of the stringified date
* `0033` is the counter
* `t` is the first character of the above described fingerprint
* `i` is the last character of the above described fingerprint
* `jo` random (uses `:rand.uniform`)

### TODOs

* Optimize (it takes 15s to run 200000 generations in my MBP)


### Credit

* Eric Elliott (author of [original JavaScript version](http://github.com/ericelliott/cuid))
* Lucas Duailibe
* Jonathan Lin
