---
title: ConfigurableProduct
description: N/A
---

# Magento_ConfigurableProduct module

The Magento_ConfigurableProduct module introduces new product type in the Magento application called Configurable Product.
This module is designed to extend existing functionality of Magento_Catalog module by adding new product type.

Configurable Products let the customers select the variant they desire by choosing options.
For example, store owner sells t-shirts in two colors and three sizes.

## Structure

`ConfigurableProduct/` - the directory that declares ConfigurableProduct metadata used by the module.

For information about a typical file structure of a module in Magento 2, see [Module file structure](https://developer.adobe.com/commerce/php/development/build/component-file-structure/#module-file-structure).

## Extensibility

Extension developers can interact with the Magento_ConfigurableProduct module. For more information about the Magento extension mechanism, see [Magento plug-ins](https://developer.adobe.com/commerce/php/development/components/plugins/).

[The Magento dependency injection mechanism](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) enables you to override the functionality of the Magento_ConfigurableProduct module.

## Additional information

### Configurable variables through the theme view.xml

Modify the value of the `gallery_switch_strategy` variable in the theme view.xml file to configure how gallery images should be updated when a user switches between product configurations.

Learn how to [configure variables](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#configure-variables) in the view.xml file.

There are two available values for the `gallery_switch_strategy` variable:

Value | Description
--- | ---
`replace` | In replace mode, images of the parent configurable product will be replaced by the simple product images upon a configuration change
`prepend` | In prepend mode, the simple product images will be added in front of the parent configurable product upon a configuration change

If the `gallery_switch_strategy` variable is not defined, the default value `replace` will be used.

For example, adding these lines of code to the theme view.xml file will set the gallery behavior to `replace` mode.

```xml
<vars module="Magento_ConfigurableProduct">
    <var name="gallery_switch_strategy">replace</var>
</vars>
```

<InlineAlert slots="text" />
The version of this module is 100.4.8.
