---
title: CMS Extension Points
description: The CMS module provides an extension point for post activation and deactivation of CMS pages.
last_updated: Jan 24, 2020
template: feature-walkthrough-template
originalLink: https://documentation.spryker.com/v1/docs/cms-extension-points
originalArticleId: 9e994f24-1266-4344-9373-13502dfa1a04
redirect_from:
  - /v1/docs/cms-extension-points
  - /v1/docs/en/cms-extension-points
related:
  - title: CMS Page
    link: docs/scos/user/features/page.version/cms-feature-overview/cms-pages-overview.html
  - title: Migration Guide - CMS
    link: docs/pbc/all/content-management-system/{{page.version}}/install-and-upgrade/upgrade-modules/upgrade-the-cms-module.html
  - title: Migration Guide - CMS Collector
    link: docs/pbc/all/content-management-system/{{page.version}}/install-and-upgrade/upgrade-modules/upgrade-the-cmscollector-module.html
---

The CMS module provides an extension point for post activation and deactivation of CMS pages. The plugin interface set for this extension point is as follows:

```php
<?php

namespace Spryker\Zed\Cms\Communication\Plugin;

use Generated\Shared\Transfer\CmsPageTransfer;

interface PostCmsPageActivatorPluginInterface
{
    /**
     * Specification:
     * - Runs after the CMS activator class functions (activate and deactivate)
     *
     * @api
     *
     * @param \Generated\Shared\Transfer\CmsPageTransfer $cmsPageTransfer
     *
     * @return void
     */
    public function execute(CmsPageTransfer $cmsPageTransfer);
}
```

For example, Navigation is connected with activation and deactivation of CMS pages, so there is a plugin in the `CmsNavigationConnector` module that is called `PostCmsPageActivatorNavigationPlugin`.

It implements the interface as follows:

```php
<?php

namespace Spryker\Zed\CmsNavigationConnector\Communication\Plugin;

use Generated\Shared\Transfer\CmsPageTransfer;
use Spryker\Zed\Cms\Communication\Plugin\PostCmsPageActivatorPluginInterface;
use Spryker\Zed\Kernel\Communication\AbstractPlugin;

/**
 * @method \Spryker\Zed\CmsNavigationConnector\Business\CmsNavigationConnectorFacadeInterface getFacade()
 * @method \Spryker\Zed\CmsNavigationConnector\Communication\CmsNavigationConnectorCommunicationFactory getFactory()
 */
class PostCmsPageActivatorNavigationPlugin extends AbstractPlugin implements PostCmsPageActivatorPluginInterface
{
    /**
     * @param \Generated\Shared\Transfer\CmsPageTransfer $cmsPageTransfer
     *
     * @return void
     */
    public function execute(CmsPageTransfer $cmsPageTransfer)
    {
        $this->getFacade()->updateCmsPageNavigationNodesIsActive($cmsPageTransfer);
    }
}
```

And then in the `CmsDependencyProvider`, in the function `getCmsPagePostActivatorPlugins`, you can register this plugin (or any plugin implementing the above interface) for it to execute post activation or deactivation of CMS pages.

