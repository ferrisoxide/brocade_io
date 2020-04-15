# BrocadeIo

Ruby client for [Brocade.io](https://www.brocade.io/) - a free and open product database

## Get Started

Add this line to your application’s Gemfile:

```ruby
gem 'brocade_io'
```

Create a client

```ruby
brocade_io = BrocadeIo.new
```

Get an item

```ruby
item = brocade_io.item("013562610020") # or nil if not found
item.gtin14
item.brand_name
item.name
item.size
```

Create or update an item

```ruby
brocade_io.update_item("000000000000", {name: "Test"})
```

List items

```ruby
brocade_io.items
```

Returns the first 100 items.

To get all items, use:

```ruby
brocade_io.paginated_items do |item|
  item.gtin14
end
```

Search items

```ruby
brocade_io.items(query: "peanut butter")
```

Add an image (NB not currently supported)

```ruby
image = Faraday::UploadIO.new("ice_cream.jpg", "image/jpeg")
image_type = "scan" # or "photo"
brocade_io.add_image("000000000000", image, image_type)
```

## Contributing

Everyone is encouraged to help improve this project. Here are a few ways you can help:

- [Report bugs](https://github.com/ferrisoxide/brocade_io/issues)
- Fix bugs and [submit pull requests](https://github.com/ferrisoxide/brocade_io/pulls)
- Write, clarify, or fix documentation
- Suggest or add new features
