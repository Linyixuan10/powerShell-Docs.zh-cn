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
# <a name="public-resource-schema"></a><span data-ttu-id="f153c-102">公共资源架构</span><span class="sxs-lookup"><span data-stu-id="f153c-102">Public Resource Schema</span></span>

<span data-ttu-id="f153c-103">Management OData 使用 MOF 定义资源及其属性。</span><span class="sxs-lookup"><span data-stu-id="f153c-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="f153c-104">管理 OData 实体的属性直接与基础 cmdlet 返回的托管类型的属性相对应。</span><span class="sxs-lookup"><span data-stu-id="f153c-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="f153c-105">定义资源</span><span class="sxs-lookup"><span data-stu-id="f153c-105">Defining a resource</span></span>

<span data-ttu-id="f153c-106">每个资源都与 Windows PowerShell cmdlet 返回的对象相对应。</span><span class="sxs-lookup"><span data-stu-id="f153c-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="f153c-107">在公共资源 MOF 文件中，通过声明类来定义资源。</span><span class="sxs-lookup"><span data-stu-id="f153c-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="f153c-108">类包含与对象的属性相对应的属性。</span><span class="sxs-lookup"><span data-stu-id="f153c-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="f153c-109">例如，在下面的示例中，[系统](/dotnet/api/System.Diagnostics.Process)类由以下 MOF 表示。</span><span class="sxs-lookup"><span data-stu-id="f153c-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="f153c-110">每个属性名称前面都有一个数据类型。</span><span class="sxs-lookup"><span data-stu-id="f153c-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="f153c-111">本示例中的数据类型与 .NET Framework 中的基元 CLR 数据类型相对应，但属性也可以引用其他资源或复杂类型，这两种方法在稍后进行介绍。</span><span class="sxs-lookup"><span data-stu-id="f153c-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="f153c-112">`Key`限定符指示属性用于唯一标识资源实例。</span><span class="sxs-lookup"><span data-stu-id="f153c-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="f153c-113">一个资源可以有多个键。</span><span class="sxs-lookup"><span data-stu-id="f153c-113">A resource can have more than one key.</span></span>

<span data-ttu-id="f153c-114">`Required`限定符指示属性是必需的。</span><span class="sxs-lookup"><span data-stu-id="f153c-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="f153c-115">如果用限定符标记属性，则 `Key` 认为该属性是必需的，并且 `Required` 限定符不是必需的。</span><span class="sxs-lookup"><span data-stu-id="f153c-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="f153c-116">复杂数据类型</span><span class="sxs-lookup"><span data-stu-id="f153c-116">Complex data types</span></span>

<span data-ttu-id="f153c-117">实体的属性可以具有复杂的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f153c-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="f153c-118">复杂数据类型是由其他类型组成的类型，类似于 C 编程语言中的结构。</span><span class="sxs-lookup"><span data-stu-id="f153c-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="f153c-119">复杂类型在 MOF 文件中声明为带有限定符的类 `ComplexType` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f153c-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="f153c-120">若要将实体属性声明为复杂类型，可将其声明为 `string` 带有限定符的类型 `EmbeddedInstance` ，包括复杂类型的名称。</span><span class="sxs-lookup"><span data-stu-id="f153c-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="f153c-121">下面的示例演示 `PswsTest_ProcessModule` 上一示例中声明的类型的属性的声明。</span><span class="sxs-lookup"><span data-stu-id="f153c-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="f153c-122">关联实体</span><span class="sxs-lookup"><span data-stu-id="f153c-122">Associating entities</span></span>

<span data-ttu-id="f153c-123">可以使用 Association 和 AssociationClass 限定符来关联两个实体。</span><span class="sxs-lookup"><span data-stu-id="f153c-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="f153c-124">有关详细信息，请参阅[关联管理 OData 实体](./associating-management-odata-entities.md)。</span><span class="sxs-lookup"><span data-stu-id="f153c-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="f153c-125">派生类型</span><span class="sxs-lookup"><span data-stu-id="f153c-125">Derived types</span></span>

<span data-ttu-id="f153c-126">可以从其他类型派生类型。</span><span class="sxs-lookup"><span data-stu-id="f153c-126">You can derive a type from another type.</span></span> <span data-ttu-id="f153c-127">派生类型继承其派生的类型的所有属性，以及显式派生的任何属性。</span><span class="sxs-lookup"><span data-stu-id="f153c-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="f153c-128">下面的示例演示一个类型声明，然后是从该类型派生的两个类型的声明。</span><span class="sxs-lookup"><span data-stu-id="f153c-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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
