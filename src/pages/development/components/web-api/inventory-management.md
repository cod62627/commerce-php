---
title: Inventory Management API Reference | Commerce PHP Extensions
description: Manage Adobe Commerce and Magento Open Source invtory with the Inventory Management modules.
keywords:
  - Extensions
  - Inventory
---

# Inventory Management API reference

Inventory Management provides new modules, interfaces, and classes to manage inventory quantities, sources, stocks, etc. This reference details deprecated modules and new services available for managing inventory for single and multi source merchants.

## Deprecated modules

Inventory Management deprecates `ScalableInventory` and `CatalogInventory` modules.

The `ScalableInventory` module is part of Adobe Commerce. Its original purpose was to perform inventory processing asynchronously, moving the computation of quantities to a worker that processed the calculations later. This functionality was limited in that the asynchronous processing could be performed on backordered products only.

Inventory Management creates reservations for all orders, not just those on backorder. All quantities are calculated asynchronously.

The `CatalogInventory` module is part of Magento Open Source. Its original purpose was to retrieve and update stock attributes, including status, quantity, and backorders. Inventory Management architecture replaces and expands these capabilities to support multiple stocks and sources, salable quantities, stock quantities, etc.

The following interfaces and classes have been deprecated. They cannot be mapped to new interfaces. The Inventory Management architecture eliminates the need for this functionality.

`ScalableInventory` interfaces:

-  `ItemInterface`
-  `ItemsInterface`

`CatalogInventory` interfaces:

-  `QueryProcessorInterface`
-  `RegisterProductSaleInterface`
-  `RevertProductSaleInterface`
-  `StockCollectionInterface`
-  `StockConfigurationInterface`
-  `StockCriteriaInterface`
-  `StockIndexInterface`
-  `StockInterface` (indexer)
-  `StockInterface`
-  `StockItemCollectionInterface`
-  `StockItemCriteriaInterface`
-  `StockItemInterface`
-  `StockItemRepositoryInterface`
-  `StockManagementInterface`
-  `StockRegistryInterface`
-  `StockRepositoryInterface`
-  `StockStateInterface`
-  `StockStatusCollectionInterface`
-  `StockStatusCriteriaInterface`
-  `StockStatusInterface`
-  `StockStatusRepositoryInterface`

`CatalogInventory` classes:

-  `Backorders`
-  `DefaultStock`
-  `DefaultStockqty`
-  `Item`
-  `Minsaleqty`
-  `Qtyincrements`
-  `QuantityValidator`
-  `Status`
-  `Stock` (Helper)
-  `Stock` (model/source)
-  `Stock`
-  `StockFactory`

## Inventory Management API

The following services reside under the [`Magento/InventoryApi/Api`](https://github.com/magento/inventory/tree/1.2.4/InventoryApi/Api) namespace, replacing deprecated services and APIs.

Service | Description | Deprecated API
--- | --- | ---
[`SourceRepositoryInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/SourceRepositoryInterface.php) | Retrieves, saves or finds (`getList` method) Source entities | -
[`StockRepositoryInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/StockRepositoryInterface.php) | Retrieves, saves, finds (`getList` method) or deletes Stock entities) |  -
[`StockSourceLinksSaveInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/StockSourceLinksSaveInterface.php) | Saves sources to stocks assignments | -
[`StockSourceLinksDeleteInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/StockSourceLinksDeleteInterface.php) | Removes sources to stocks assignments |  -
[`GetStockSourceLinksInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/GetStockSourceLinksInterface.php) | Retrieves source to stock links according to provided `SearchCriteria` | -
[`GetSourcesAssignedToStockOrderedByPriorityInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/GetSourcesAssignedToStockOrderedByPriorityInterface.php) | Retrieves sources assigned to provided stock sorted by priority | -
[`SourceItemRepositoryInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/SourceItemRepositoryInterface.php) | Finds `SourceItems` (products assigned to sources with Quantity per Source) by provided `SearchCriteria` | [`StockItemRepositoryInterface::getList`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockItemRepositoryInterface.php#L41)
[`SourceItemsSaveInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/SourceItemsSaveInterface.php) | Saves `SourceItems` (quantites and stock statuses of products on sources) | [`StockItemRepositoryInterface::save`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockItemRepositoryInterface.php#L25)
[`SourceItemsDeleteInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryApi/Api/SourceItemsDeleteInterface.php) | Deletes `SourceItems` (quantites and stock statuses of products on sources) | [`StockItemRepositoryInterface::delete`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockItemRepositoryInterface.php#L49) or [`deleteById`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockItemRepositoryInterface.php#L55)

## Inventory Catalog API

The following services reside under the [`Magento/InventoryCatalogApi/Api`](https://github.com/magento/inventory/blob/1.2.4/InventoryCatalogApi/Api) namespace.

Service | Description
--- | ---
[``DefaultSourceProviderInterface``](https://github.com/magento/inventory/blob/1.2.4/InventoryCatalogApi/Api/DefaultSourceProviderInterface.php) | Retrieves Default Source code
[`DefaultStockProviderInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryCatalogApi/Api/DefaultStockProviderInterface.php) | Retrieves Default Stock id
[`BulkInventoryTransferInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryCatalogApi/Api/BulkInventoryTransferInterface.php) | [Bulk transfers](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/#bulk-transfer) the whole quantity of products from origin to destination source
[`BulkPartialInventoryTransferInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryCatalogApi/Api/BulkPartialInventoryTransferInterface.php) | Runs [bulk partial inventory transfer](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/#bulk-partial-transfer) for specified items

## Inventory Sales API

The following services reside under the [`Magento/InventorySalesApi/Api`](https://github.com/magento/inventory/tree/1.2.4/InventorySalesApi/Api namespace, replacing deprecated services and APIs.

Service | Description                                                                                                                                 | Deprecated API
--- |---------------------------------------------------------------------------------------------------------------------------------------------| ---
[`StockResolverInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySalesApi/Api/StockResolverInterface.php) | Resolves linked Stock by provided sales channel type and code                                                                               | [`StockRegistryInterface::getStock`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockRegistryInterface.php#L23)
[`GetStockBySalesChannelInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySalesApi/Api/GetStockBySalesChannelInterface.php) | Resolves linked stock to provided sales channel object                                                                                      | [`StockRegistryInterface::getStock`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockRegistryInterface.php#L23)
[`IsProductSalableInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySalesApi/Api/IsProductSalableInterface.php) | Checks whether product salable                                                                                                              |  [`StockRegistryInterface::getProductStockStatus`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockRegistryInterface.php#L62) <br /> [`StockRegistryInterface::getProductStockStatusBySku`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockRegistryInterface.php#L70) <br /> [`StockRegistryInterface::getStockStatusBySku`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockRegistryInterface.php#L53)
[`AreProductsSalableInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySalesApi/Api/AreProductsSalableInterface.php) | Checks whether products in the list are salable                                                                                             |  [`StockRegistryInterface::getProductStockStatus`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockRegistryInterface.php#L62) <br /> [`StockRegistryInterface::getProductStockStatusBySku`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockRegistryInterface.php#L70) <br /> [`StockRegistryInterface::getStockStatusBySku`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockRegistryInterface.php#L53)
[`IsProductSalableForRequestedQtyInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySalesApi/Api/IsProductSalableForRequestedQtyInterface.php)  | Checks if the product is salable for the requested quantity (used for shopping cart and checkout)                                           | [`StockStateInterface::checkQuoteItemQty`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockStateInterface.php#L41) <br /> [`StockStateInterface::checkQty`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockStateInterface.php#L52)
[`GetProductSalableQtyInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySalesApi/Api/GetProductSalableQtyInterface.php)  | Gets product salable quantity (aggregated stock quantity including reservations)                                                            |  [`StockStateInterface::getStockQty`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockStateInterface.php#L72) or just retrieve `Qty` from [`StockStatus`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/Data/StockStatusInterface.php#L65) entity
[`PlaceReservationsForSalesEventInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySalesApi/Api/PlaceReservationsForSalesEventInterface.php) | Places reservation in the scope some sales event (such as order placement, shipment creation, credit memo creation, order cancelation, etc) |  [`RegisterProductSaleInterface`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/RegisterProductSaleInterface.php) <br /> [`RevertProductSaleInterface`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/RevertProductSaleInterface.php)

## Inventory Configuration API

The following services reside under the [`Magento/InventoryConfigurationApi/Api`](https://github.com/magento/inventory/tree/1.2.4/InventoryConfigurationApi/Api) namespace, replacing deprecated services and APIs.

Service | Description | Deprecated API
--- | --- | ---
[`GetStockItemConfigurationInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryConfigurationApi/Api/GetStockItemConfigurationInterface.php)  |  Retrieves stock item configuration by SKU and stock id |  Catalog inventory configuration stored in [`StockItem`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/Data/StockItemInterface.php) entity
[`SaveStockItemConfigurationInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryConfigurationApi/Api/SaveStockItemConfigurationInterface.php)  | Saves stock item configuration  |  Stock configuration saved using [`StockItemRepositoryInterface::save`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/CatalogInventory/Api/StockItemRepositoryInterface.php#L25)

## Inventory Source Selection Algorithm (SSA) API

The following services reside under the [`Magento/InventorySourceSelectionApi/Api`](https://github.com/magento/inventory/tree/1.2.4/InventorySourceSelectionApi/Api) namespace.

Service | Description
--- | ---
[`GetDefaultSourceSelectionAlgorithmCodeInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySourceSelectionApi/Api/GetDefaultSourceSelectionAlgorithmCodeInterface.php)  |  Gets the default Source Selection Algorithm (SSA) code
[`GetSourceSelectionAlgorithmListInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySourceSelectionApi/Api/GetSourceSelectionAlgorithmListInterface.php)  |  Gets the entire Source Selection Algorithm (SSA) list
[`SourceSelectionServiceInterface`](https://github.com/magento/inventory/blob/1.2.4/InventorySourceSelectionApi/Api/SourceSelectionServiceInterface.php)  |  Runs a specified Source Selection Algorithm (SSA) based on provided Inventory Request object

## Inventory Export Aggregated Stock Data API

The following services reside under the [`Magento/InventoryExportStockApi/Api`](https://github.com/magento/inventory/tree/1.2.4/InventoryExportStockApi/Api) namespace.

Service | Description
--- | ---
[`ExportStockIndexDataInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryExportStockApi/Api/ExportStockIndexDataInterface.php)  |  Returns salable quantities for a provided sales channel not including placed reservations for completed orders. The quantity amount is less precise and runs with high performance and speed.
[`ExportStockSalableQtyInterface`](https://github.com/magento/inventory/blob/1.2.4/InventoryExportStockApi/Api/ExportStockSalableQtyInterface.php)  |  Returns salable quantities for a provided sales channel including placed reservations (for completed orders). The quantity amount is precise and runs with reduced performance and slower speed.
