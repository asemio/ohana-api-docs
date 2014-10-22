## Update an existing location

```ruby
# Update location whose id is 1
Ohanakapa.update_location(1, { name: 'Updated Name' })
```

```shell
curl -X PATCH "https://ohana-api-demo.herokuapp.com/api/locations/1" -d '{"name":"Updated name"}' -H "X-Api-Token: test" -H "Content-Type: application/json"
```

> When successful, the above command returns a `200` HTTP status code and JSON
> structured like this:

```json
{
  "id": 14,
  "accessibility": [ ],
  "admin_emails": [ ],
  "alternate_name": null,
  "coordinates": [
    -122.2586432,
    37.5304228
  ],
  "description": "Provides general reading materials, including large-type books, videos, music cassettes and CDs, and books on tape. Offers children's programs and a Summer Reading Club. Meeting room is available to nonprofit groups. Participates in the Peninsula Library System.",
  "emails": [ ],
  "hours": null,
  "languages": [ ],
  "latitude": 37.5304228,
  "longitude": -122.2586432,
  "name": "Updated Name",
  "short_desc": "Provides general reading materials and reference services.",
  "slug": "redwood-shores-branch",
  "transportation": null,
  "updated_at": "2014-09-09T07:54:08.641-07:00",
  "urls": [
    "http://www.redwoodcity.org/library"
  ],
  "url": "https://ohana-api-demo.herokuapp.com/api/locations/redwood-shores-branch",
  "address": {
    "id": 14,
    "street_1": "399 Marine Parkway",
    "street_2": null,
    "city": "Redwood City",
    "state": "CA",
    "postal_code": "94065"
  },
  "contacts": [
    {
      "email": null,
      "id": 22,
      "name": "Dave Genesy",
      "phones": [],
      "title": "Library Director",
      "department": null
    }
  ],
  "mail_address": {
    "id": 14,
    "attention": "Redwood Shores Branch",
    "street_1": "399 Marine Parkway",
    "street_2": null,
    "city": "Redwood City",
    "state": "CA",
    "postal_code": "94065"
  },
  "phones": [
    {
      "id": 15,
      "department": null,
      "extension": null,
      "number": "650 780-5740",
      "number_type": "voice",
      "vanity_number": null
    }
  ],
  "services": [
    {
      "id": 15,
      "audience": null,
      "description": null,
      "eligibility": "Resident of California to obtain a library card",
      "fees": "None.",
      "funding_sources": [
        "City"
      ],
      "how_to_apply": "Walk in. Proof of California residency required to receive a library card.",
      "keywords": [
        "EDUCATION SERVICES",
        "Library",
        "Libraries",
        "Public Libraries"
      ],
      "name": null,
      "service_areas": [
        "San Mateo County"
      ],
      "short_desc": null,
      "urls": [ ],
      "wait": "No wait.",
      "updated_at": "2014-04-16T19:51:28.610-07:00",
      "categories": [ ]
    }
  ],
  "organization": {
    "id": 8,
      "alternate_name": null,
      "date_incorporated": null,
      "description": "Test description",
      "email": null,
      "name": "Admin Test Org",
      "slug": "admin-test-org",
      "website": null,
      "url": "https://ohana-api-demo.herokuapp.com/api/organizations/admin-test-org",
      "locations_url": "https://ohana-api-demo.herokuapp.com/api/organizations/admin-test-org/locations"
  }
}
```

This endpoint updates an existing location.

### HTTP Request

`PATCH https://ohana-api-demo.herokuapp.com/api/locations/1`

### JSON Parameters

| Name | Type | Requirement | Details |
|:-----|:-----|:---------|:-------|
| accessibility | array of strings | optional | Accessibility options available at the location. Accepted values are `cd`, `deaf_interpreter`, `disabled_parking`, `elevator`, `ramp`, `restroom`, `tape_braille`, `tty`, `wheelchair`, and `wheelchair_van`. |
| admin_emails | array of strings | optional | Email address for a person allowed to administer the location (via the Ohana API Admin interface for example). |
| alternate_name | String | optional | Another name this location might be known by. |
| latitude | float | optional | Latitude portion of the location's coordinates. Note that the app automatically geocodes addresses if the data doesn't include coordinates |
| longitude | float | optional | Longitude portion of the location's coordinates. Note that the app automatically geocodes addresses if the data doesn't include coordinates |
| description | string | required | Description of services provided at the location |
| emails | array of strings | optional | General Email addresses for location. Emails that belong to contacts should go in the Contact object. |
| hours | string | optional | Hours of operation for the location |
| languages | array of strings | optional | Languages spoken at the location |
| name | string | required | Name of the location |
| short_desc | string | optional | Succinct description of services provided at the location. |
| transportation | string | optional | Public transportation options near the location |
| urls | array of strings | optional | The location's website URLs. Must include "http://" or "https://" |
| virtual | boolean | required if the location does not have a physical address | Whether or not the location has a physical address. If `false`, it must have an address associated with it. The default value is `false`. |

<aside class="warning">All PATCH requests require a valid token passed via the
`X-Api-Token` HTTP header</aside>
