# hncr

A Hacker News API wrapper for Crystal

## Installation

Add this to your application's `shard.yml`:

```yaml
dependencies:
  hncr:
    github: aretrace/hncr
    branch: main
```

## Usage

```crystal
require "hncr"

# Get ten stories of the 'top' category and print them
HN::Item.new(type: "top", count: 10) do |item|
  puts "#{ item["title"] }, by #{ item["by"] }\n#{ item["url"]? }\n\n"
end

# Get user by id and print the 'about' field
HN::User.new(id: "jl") do |user|
  puts user["about"]
end

```
## API
##### NOTE:
The API returns items concurrently.

##### Items constructor:
`HN::Item(type, count, &block)`

* `type : String` One of the following strings for the type of story:
`new`, `top`, `best`, `ask`, `show`, or `job`.

* `count : Int32` The number of stories to return.

* `&block` Block takes one argument that returns a JSON::Any struct
containing the item's json fields.

##### User constructor:
`HN::User(id, &block)`

* `id : String` The id of the user.

* `&block` Block takes one argument that returns a JSON::Any struct
containing the user's json fields.