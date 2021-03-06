---
title: Workarea 3.2.41
excerpt: Patch release notes for Workarea 3.2.41.
---

# Workarea 3.2.41

Patch release notes for Workarea 3.2.41.

## Display Relevant Flash Message When No Shipping Options Are Available

Improve the user experience when checkout cannot complete due to the
site having no available shipping options for the user's shipping
address.

### Issues

- [ECOMMERCE-6992](https://jira.tools.weblinc.com/browse/ECOMMERCE-6992)

### Pull Requests

- [4166](https://stash.tools.weblinc.com/projects/WL/repos/workarea/pull-requests/4166/overview)

## Disallow Negative Prices in Seed Data

It was formerly possible to generate a `Pricing::Price` that had a
negative value in seeds. The `ProductsSeeds#perform` method now protects
against this.

### Issues

- [ECOMMERCE-7062](https://jira.tools.weblinc.com/browse/ECOMMERCE-7062)

### Pull Requests

- [4167](https://stash.tools.weblinc.com/projects/WL/repos/workarea/pull-requests/4167/overview)

## Fix Order Status Lookup Route

The `/orders/status/:order_id/:postal_code` was being resolved by the
`#show` action of OrdersController, when it really should be served by
`#lookup`. Change the route and add a test ensuring that the route is
being handled properly.

Discovered by **Andy Sides** of BVAccel. Thanks Andy!


### Issues

- [ECOMMERCE-7040](https://jira.tools.weblinc.com/browse/ECOMMERCE-7040)

### Pull Requests

- [4153](https://stash.tools.weblinc.com/projects/WL/repos/workarea/pull-requests/4153/overview)

## Render Shipping Details Append Point On Index

Move the **admin.shipping_details** append point from `shippings#show`
(which is no longer rendered) over to `shippings#index`. Remove the
`shippings#show` partial to reduce confusion since it is no longer being
used.

### Issues

- [ECOMMERCE-7061](https://jira.tools.weblinc.com/browse/ECOMMERCE-7061)

### Pull Requests

- [4160](https://stash.tools.weblinc.com/projects/WL/repos/workarea/pull-requests/4160/overview)

## Fix Internal Server Error Page Not Rendering JSON

When an Internal Server Error is requested via `/500.json`, another
error occurs when attempting to render the view for that request,
because there's no `internal` template. This is not how our error
handler is supposed to work, any format should be acceptable to render a
404 or 500. The syntax of the `respond_to` block in `#render_error_page`
has been altered so that Workarea serves the custom content HTML when an
HTML error occurs (e.g., most user-facing browser errors), and an empty
body with a 500 error in the status code is returned for all other
formats.

### Issues

- [ECOMMERCE-7034](https://jira.tools.weblinc.com/browse/ECOMMERCE-7034)

### Pull Requests

- [4156](https://stash.tools.weblinc.com/projects/WL/repos/workarea/pull-requests/4156/overview)

