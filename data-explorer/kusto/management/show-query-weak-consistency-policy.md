---
title: .show cluster policy query_weak_consistency command
description: Learn how to use the `.show cluster policy query_weak_consistency` command to show the query weak consistency policy of the cluster.
ms.reviewer: yabenyaa
ms.topic: reference
ms.date: 05/24/2023
---
# .show cluster policy query_weak_consistency command

This article describes the show management command used for the [query weak consistency policy](query-weak-consistency-policy.md). This command returns the query weak consistency policy of the cluster.

## Permissions

You must have at least [AllDatabasesMonitor](access-control/role-based-access-control.md) permissions to run this command.

## Syntax

`.show` `cluster` `policy` `query_weak_consistency`

[!INCLUDE [syntax-conventions-note](../../includes/syntax-conventions-note.md)]

## Returns

|Policy name | Entity name | Policy | Child entities | Entity type | EffectivePolicy
|---|---|---|---|---|---
|QueryWeakConsistencyPolicy |  | JSON serialization of the [query weak consistency policy object](./query-weak-consistency-policy.md#the-policy-object) that has been set for the cluster. It includes all the defined values, including default settings. | | Cluster | JSON serialization of the [query weak consistency policy object](./query-weak-consistency-policy.md#the-policy-object) currently in use for the cluster. It excludes any values that are set to the default (-1), providing a representation of the policy configuration that is actively governing the cluster's behavior.

## Example

```kql
.show cluster policy query_weak_consistency 
```

|PolicyName|EntityName|Policy|ChildEntities|EntityType|EffectivePolicy|
|---|---|---|---|---|---|
|QueryWeakConsistencyPolicy||{"PercentageOfNodes": 17, "MinimumNumberOfNodes": -1, "MaximumNumberOfNodes": 12, "SuperSlackerNumberOfNodesThreshold": -1, "EnableMetadataPrefetch": false, "MaximumLagAllowedInMinutes": -1, "RefreshPeriodInSeconds": -1}| |Cluster|{"PercentageOfNodes": 17, "MinimumNumberOfNodes": 2, "MaximumNumberOfNodes": 12, "SuperSlackerNumberOfNodesThreshold": 2147483647, "EnableMetadataPrefetch": false, "MaximumLagAllowedInMinutes": 5, "RefreshPeriodInSeconds": 120}
