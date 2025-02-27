---
title: Marketplace Merchant Portal Product Offer Management feature overview
description: This document describes product offer management in the Merchant Portal.
template: concept-topic-template
related:
  - title: Managing marketplace product offers
    link: docs/marketplace/user/merchant-portal-user-guides/page.version/offers/managing-product-offers.html
  - title: Managing merchant product offers
    link: docs/marketplace/user/back-office-user-guides/page.version/marketplace/offers/managing-merchant-product-offers.html
---

In a marketplace environment, merchants manage [product offers](/docs/marketplace/user/features/{{page.version}}/marketplace-product-offer-feature-overview.html) in the Merchant Portal.


## Managing product offers

Merchants create product offers based on the products that exist in the marketplace. When creating an offer, they can see full information about products, including the number of existing offers for each of them.

One merchant can create multiple offers for the same product. When creating product offers, the number of product offers for a product includes their own existing product offers.

Merchants define the following settings when creating product offers:

|SETTING|DESCRIPTION|
|---|---|
| Status| Active or Inactive. |
| Merchant SKU | Unique identifier of the offer in the merchants' system. |
| Stores| Spryker Marketplace is a multi-store environment, and merchants can define which stores to display their offers in. |
|Stock | Offer's own stock that's not dependent on the respective product's stock. |
|Prices | Product offers support all types of Spryker Commerce OS prices: [volume](/docs/pbc/all/price-management/prices-feature-overview/volume-prices-overview.html), [default and original](/docs/pbc/all/price-management/prices-feature-overview/prices-feature-overview.html). |
| Validity dates | Defines the period when an offer is displayed on the Storefront. Even if the respective product is no longer available, the offer can still be displayed. |

## Related Business User articles

|MERCHANT PORTAL USER GUIDES  |BACK OFFICE USER GUIDES |
|---------|---------|
| [Managing product offers](/docs/marketplace/user/merchant-portal-user-guides/{{page.version}}/offers/managing-product-offers.html)  |[Managing merchant product offers](/docs/marketplace/user/back-office-user-guides/{{page.version}}/marketplace/offers/managing-merchant-product-offers.html)|

{% info_block warningBox "Developer guides" %}

Are you a developer? See [Marketplace Merchant Portal Product Offer Management feature walkthrough](/docs/marketplace/dev/feature-walkthroughs/{{page.version}}/marketplace-merchant-portal-product-offer-management-feature-walkthrough.html) for developers.

{% endinfo_block %}
