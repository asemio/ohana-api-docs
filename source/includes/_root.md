# Root Endpoint

Sending a `GET` request to the root endpoint will return all endpoint categories that the API supports.

`GET https://ohana-api-211.herokuapp.com/api`

> The root endpoint returns JSON structured like this:

```json
{
  "organizations_url": "https://ohana-api-211.herokuapp.com/api/organizations{?page,per_page}",
  "organization_url": "https://ohana-api-211.herokuapp.com/api/organizations/{organization}",
  "organization_locations_url": "https://ohana-api-211.herokuapp.com/api/organizations/{organization}/locations{?page,per_page}",
  "locations_url": "https://ohana-api-211.herokuapp.com/api/locations{?page,per_page}",
  "location_url": "https://ohana-api-211.herokuapp.com/api/locations/{location}",
  "location_search_url": "https://ohana-api-211.herokuapp.com/api/search{?category,email,keyword,language,lat_lng,org_name,radius,service_area,status,page,per_page}"
}
```

All URLs are expected to be proper [RFC 6570](http://tools.ietf.org/html/rfc6570) URI templates.

You can then expand these templates using something like the [uri_template](https://github.com/hannesg/uri_template) Ruby gem. See example code in the Ruby tab on the right.

```ruby
# Example usage of the uri_template gem
>> tmpl = URITemplate.new('/search{?keyword,location,language}')
>> tmpl.expand
=> "/search"

>> tmpl.expand keyword: 'food'
=> "/search?keyword=food"

>> tmpl.expand keyword: 'food', location: '94403'
=> "/search?keyword=food&location=94403"
```