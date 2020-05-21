---
title: 公共资源架构 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: 52244ee7496b99e11f0306e93728736fc9c51be5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564697"
---
# <a name="public-resource-schema"></a>公共资源架构

Management OData 使用 MOF 定义资源及其属性。 管理 OData 实体的属性直接与基础 cmdlet 返回的托管类型的属性相对应。

## <a name="defining-a-resource"></a>定义资源

每个资源都与 Windows PowerShell cmdlet 返回的对象相对应。 在公共资源 MOF 文件中，通过声明类来定义资源。 类包含与对象的属性相对应的属性。 例如，在下面的示例中，[系统](/dotnet/api/System.Diagnostics.Process)类由以下 MOF 表示。

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

每个属性名称前面都有一个数据类型。 本示例中的数据类型与 .NET Framework 中的基元 CLR 数据类型相对应，但属性也可以引用其他资源或复杂类型，这两种方法在稍后进行介绍。

`Key`限定符指示属性用于唯一标识资源实例。 一个资源可以有多个键。

`Required`限定符指示属性是必需的。 如果用限定符标记属性，则 `Key` 认为该属性是必需的，并且 `Required` 限定符不是必需的。

### <a name="complex-data-types"></a>复杂数据类型

实体的属性可以具有复杂的数据类型。 复杂数据类型是由其他类型组成的类型，类似于 C 编程语言中的结构。 复杂类型在 MOF 文件中声明为带有限定符的类 `ComplexType` ，如下面的示例中所示。

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

若要将实体属性声明为复杂类型，可将其声明为 `string` 带有限定符的类型 `EmbeddedInstance` ，包括复杂类型的名称。 下面的示例演示 `PswsTest_ProcessModule` 上一示例中声明的类型的属性的声明。

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>关联实体

可以使用 Association 和 AssociationClass 限定符来关联两个实体。 有关详细信息，请参阅[关联管理 OData 实体](./associating-management-odata-entities.md)。

### <a name="derived-types"></a>派生类型

可以从其他类型派生类型。 派生类型继承其派生的类型的所有属性，以及显式派生的任何属性。 下面的示例演示一个类型声明，然后是从该类型派生的两个类型的声明。

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```
