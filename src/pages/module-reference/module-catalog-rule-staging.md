---
title: CatalogRuleStaging
description: N/A
---

# Magento_CatalogRuleStaging module

The Magento_CatalogRuleStaging module is a part of the staging functionality in Magento EE. It enables you to create new catalog rule updates or add new changes to the existing store updates. In other words, you can modify the catalog rules in updates. These updates are shown on the content dashboard.

## Implementation details

The Magento_CatalogRuleStaging module changes a catalog rule creation page and the catalog rule related database tables to make them compatible with the Magento Staging Framework. This module depends on the Magento_CatalogRule module and extends its functionality. It changes the database structure of the Magento_CatalogRule module and the way in which catalog rules are managed. The Magento_CatalogRule module must be enabled.

The Magento_CatalogRuleStaging module enables you to stage the following catalog rule attributes:

- Rule Name
- Description
- Websites
- Customer Groups
- Priority
- Product Apply
- Product Discount Amount
- Subproduct Discounts
- Subproduct Apply
- Subproduct Discount Amount
- Discard Subsequent Rules

These attributes cannot be modified and are a part of the static Magento Catalog Rule form.

### Installation details

The Magento_CatalogRuleStaging module makes irreversible changes in a database during installation. You cannot uninstall this module.

## Dependencies

You can find the list of modules that have dependencies on the Magento_CatalogRuleStaging module in the `require` section of the `composer.json` file. The file is located in the root directory of the module.

## Extension points

Extension points enable extension developers to interact with the Magento_CatalogRuleStaging module. You can interact with the Magento_CatalogRuleStaging module using the Magento extension mechanism, see [Magento plug-ins](https://developer.adobe.com/commerce/php/development/components/plugins/).

[The Magento dependency injection mechanism](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) enables you to override the functionality of the Magento_CatalogRuleStaging module.

### Layouts

You can extend and override layouts in the `app/code/Magento/CatalogRuleStaging/view/adminhtml/layout` directory.
For more information about layouts, see the [Layout documentation](https://developer.adobe.com/commerce/frontend-core/guide/layouts/).

<InlineAlert slots="text" />
The version of this module is 100.4.8.
