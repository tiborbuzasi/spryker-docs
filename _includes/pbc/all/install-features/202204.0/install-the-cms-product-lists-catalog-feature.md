

## Install Feature Core

### Prerequisites

Please overview and install the necessary features before beginning the integration step.

| NAME | VERSION |
| --- | --- |
| Cms | {{site.version}} |
| Product lists | {{site.version}} |
| Catalog | {{site.version}} |
| Customer | {{site.version}} |

### 1) Install the required modules using Composer

Run the following command to install the required modules:

```bash
composer require spryker/customer-catalog:"^1.0.0" --update-with-dependencies
```

{% info_block warningBox "Verification" %}

Make sure that the following modules were installed:

| MODULE | EXPECTED DIRECTORY |
| --- | --- |
| CustomerCatalog | vendor/spryker/customer-catalog |

{% endinfo_block %}

## Set up behavior

#### Configure the catalog search count query

Add the following plugins to your project:

| PLUGIN | SPECIFICATION | PREREQUISITES | NAMESPACE |
| --- | --- | --- | --- |
| ProductListQueryExpanderPlugin | Extends a search query by filtering down results to match the current customer's product restrictions. | None |  \Spryker\Client\CustomerCatalog\Plugin\Search\ProductListQueryExpanderPlugin |

**src/Pyz/Client/Catalog/CatalogDependencyProvider.php**

 ```php
 <?php

namespace Pyz\Client\Catalog;

use Spryker\Client\Catalog\CatalogDependencyProvider as SprykerCatalogDependencyProvider;
use Spryker\Client\CustomerCatalog\Plugin\Search\ProductListQueryExpanderPlugin;

class CatalogDependencyProvider extends SprykerCatalogDependencyProvider
{
        /**
        * @return \Spryker\Client\Search\Dependency\Plugin\QueryExpanderPluginInterface[]
        */
         protected function createCatalogSearchCountQueryExpanderPlugins():             array
                    {
                             return [
                                        new ProductListQueryExpanderPlugin(),
                             ];
                 }
}
 ```

{% info_block warningBox "Verification" %}

Make sure that the number of products on the catalog tab item is correct according to the customer's assigned product lists.

{% endinfo_block %}
