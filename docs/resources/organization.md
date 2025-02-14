---
layout: "auth0"
page_title: "Auth0: auth0_organization"
description: |-
  The Organizations feature represents a broad update to the Auth0 platform that
  allows our business-to-business (B2B) customers to better manage their partners
  and customers, and to customize the ways that end-users access their
  applications. Auth0 customers can use Organizations to:

  - Represent their business customers and partners in Auth0 and manage their
      membership.
  - Configure branded, federated login flows for each business.
  - Build administration capabilities into their products, using Organizations
      APIs, so that those businesses can manage their own organizations.
---

# auth0_organization

The Organizations feature represents a broad update to the Auth0 platform that
allows our business-to-business (B2B) customers to better manage their partners
and customers, and to customize the ways that end-users access their
applications. Auth0 customers can use Organizations to:

  - Represent their business customers and partners in Auth0 and manage their
    membership.
  - Configure branded, federated login flows for each business.
  - Build administration capabilities into their products, using Organizations
    APIs, so that those businesses can manage their own organizations.

## Example Usage

```hcl
resource auth0_organization acme {
	name = "acme"
	display_name = "Acme Inc."
	branding {
		logo_url = "https://acme.com/logo.svg"
		colors = {
			primary = "#e3e2f0"
			page_background = "#e3e2ff"
		}
	}
  connections {
		connection_id = auth0_connection.acme.id
		assign_membership_on_login = true
	}
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of this organization
* `display_name` – (Optional) Friendly name of this organization
* `branding` – (Optional) Defines how to style the login pages. For details, see
  [Branding](#branding)
* `metadata` - (Optional) Metadata associated with the organization, Maximum of
  10 metadata properties allowed
* `connections` – (Optional) Connections assigned to the organization. For
  details, see [Connections](#connections)

### Branding

* `logo_url` - (Optional) URL of logo to display on login page
* `colors` - (Optional) Color scheme used to customize the login pages

### Connections

* `connection_id` – (Required) The connection ID of the connection to add to the
  organization
* `assign_membership_on_login` – (Optional) When true, all users that log in
  with this connection will be automatically granted membership in the
  organization. When false, users must be granted membership in the organization
  before logging in with this connection.
