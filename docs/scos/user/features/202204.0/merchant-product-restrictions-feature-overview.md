---
title: Merchant Product Restrictions feature overview
description: Merchant Product Restrictions lets merchants define the products that are available to each of their B2B customers.
last_updated: Jul 22, 2021
template: concept-topic-template
originalLink: https://documentation.spryker.com/2021080/docs/merchant-product-restrictions-feature-overview
originalArticleId: 9d02b7ac-0e20-47bf-8f5b-656279a8278d
redirect_from:
  - /2021080/docs/merchant-product-restrictions-feature-overview
  - /2021080/docs/en/merchant-product-restrictions-feature-overview
  - /docs/merchant-product-restrictions-feature-overview
  - /docs/en/merchant-product-restrictions-feature-overview
---

The _Product Restrictions_ feature lets merchants define the products that are available to each of their B2B customers.

In terms of the [Merchant concept](/docs/scos/user/features/{{page.version}}/merchant-b2b-contracts-feature-overview.html), a *merchant* is the one who sells products on a marketplace and can set prices.

Product Restrictions from a merchant to a buyer give merchants [another layer](/docs/scos/user/features/{{page.version}}/customer-access-feature-overview.html) of control over the information a customer can see in the shop application. Based on product restrictions, you can do the following actions:

* Create a list of products.
* Hide the product information for the products (pricing, appearance in the search/filters).
* Limit access to a product details page.

Product Restriction works on the basis of allowlist and excludelist lists. That means that products that are added to an allowlist are always shown to a customer while products from an excludelist are hidden from the customer view.

To restrict the products, a shop administrator needs to create a product list, include the necessary products to the list and excludelist them for a specific merchant relationship. All other products will be available for that merchant relationship.

To create product lists, follow [Create product lists](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/product-lists/create-product-lists.html).

You can check more cases of product restrictions workflow on the [Restricted Products Behavior](/docs/scos/dev/feature-walkthroughs/{{page.version}}/merchant-product-restrictions-feature-walkthrough/restricted-products-behavior.html) page.

## Current constraints

- When a single product from the product set is added to an excludelist, the other items are displayed in the shop. We are going to update the logic in a way that in case any of the items in the product set is added to the excludelist, all relevant product sets containing this item will be added to the excludelist too.
-  The current functionality allows displaying the whole product bundle even if it contains the customer-specific products from the excludelist. We are working on updating the logic so that if the bundle product includes an item from the excludelist, the whole bundle will also also be hidden from a customer.

## Related Business User articles

|BACK OFFICE USER GUIDES|
|---|
| [Create product lists](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/product-lists/create-product-lists.html)  |
| [Edit product lists](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/product-lists/edit-product-lists.html) |
| [Create merchant relations](/docs/scos/user/back-office-user-guides/{{page.version}}/marketplace/merchant-relations/create-merchant-relations.html) |
| [Edit merchant relations](/docs/scos/user/back-office-user-guides/{{page.version}}/marketplace/merchant-relations/edit-merchant-relations.html) |

{% info_block warningBox "Developer guides" %}

Are you a developer? See [Merchant Product Restrictions feature walkthrough](/docs/scos/dev/feature-walkthroughs/{{page.version}}/merchant-product-restrictions-feature-walkthrough/merchant-product-restrictions-feature-walkthrough.html) for developers.

{% endinfo_block %}
