---
title: Product Options
last_updated: Jun 16, 2021
template: data-import-template
originalLink: https://documentation.spryker.com/2021080/docs/product-options-import
originalArticleId: 07d8b5ee-b4c6-4538-a21c-5a7a8b16837c
redirect_from:
  - /2021080/docs/product-options-import
  - /2021080/docs/en/product-options-import
  - /docs/product-options-import
  - /docs/en/product-options-import
---

The **Product Options** category contains all data you need to manage product options in your online store. We have structured this section according to the following CSV files that you will have to use to import the data:

* [product_option.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/special-product-types/product-options/file-details-product-option.csv.html): allows you to define product options, like insurance, warranty or gift wrapping, and its abstract products.
* [product_option_price.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/special-product-types/product-options/file-details-product-option-price.csv.html): allows you to define the net and gross prices for each product option.  

The table below provides details on Product Options data importers, their purpose, CSV files, dependencies, and other details. Each data importer contains links to CSV files used to import the corresponding data, including specifications of mandatory and unique fields, dependencies, detailed explanations, recommendations, templates, and content examples.

| DATA IMPORTER | PURPOSE | CONSOLE COMMAND | FILES | DEPENDENCIES |
| --- | --- | --- | --- |--- |
| Product Option | Imports information about product options, like insurance, warranty or gift wrapping, and the list of Abstract Product SKUs to which the Product Option is available. |`data:import:product-option` | [product_option.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/special-product-types/product-options/file-details-product-option.csv.html) |None |
| Product Option Price | Imports information to set the prices net and gross for each of Product Option, per store and per currency.  |`data:import:product-option-price` |[product_option_price.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/special-product-types/product-options/file-details-product-option-price.csv.html)| [product_option.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/special-product-types/product-options/file-details-product-option.csv.html) |

