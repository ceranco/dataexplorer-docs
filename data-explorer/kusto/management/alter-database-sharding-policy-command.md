---
title: .alter database sharding policy command - Azure Data Explorer
description: Learn how to use the .alter database sharding policy command to change the database's sharding policy.
ms.reviewer: yonil
ms.topic: reference
ms.date: 04/20/2023
---
# .alter database sharding policy

Changes the database sharding policy. The [sharding policy](../management/shardingpolicy.md) is used to manage data sharding for databases and tables by defining if and how [extents (data shards)](../management/extents-overview.md) in the Azure Data Explorer cluster should be sealed.

When a database is created, it contains the default data sharding policy. All tables created in the database inherit this policy unless the policy is explicitly overridden at the table level.

## Permissions

You must have at least [Database Admin](access-control/role-based-access-control.md) permissions to run this command.

## Syntax

`.alter` `database` *DatabaseName* `policy` `sharding` *PolicyObject*

## Parameters

|Name|Type|Required|Description|
|--|--|--|--|
|*DatabaseName*|string|&check;|The name of the database for which to alter the sharding policy.|
|*PolicyObject*|string|&check;|A policy object that defines the sharding policy. For more information, see the [sharding policy](../management/shardingpolicy.md).|

## Returns

Returns a JSON representation of the policy.

## Example

The following command returns the updated extents sharding policy for the database:

````kusto
.alter database MyDatabase policy sharding
```
{
    "MaxRowCount" : 750000,
    "MaxExtentSizeInMb" : 1024,
    "MaxOriginalSizeInMb": 2048
}
```
````
