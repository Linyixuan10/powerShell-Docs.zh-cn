---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Registry 资源
ms.openlocfilehash: 9f65815cbe6a94831b88cb3425bf688e1a99a9c0
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559896"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="aa514-103">DSC Registry 资源</span><span class="sxs-lookup"><span data-stu-id="aa514-103">DSC Registry Resource</span></span>

> <span data-ttu-id="aa514-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="aa514-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="aa514-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Registry** 资源提供了在目标节点上管理注册表项和值的机制。</span><span class="sxs-lookup"><span data-stu-id="aa514-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa514-106">语法</span><span class="sxs-lookup"><span data-stu-id="aa514-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="aa514-107">属性</span><span class="sxs-lookup"><span data-stu-id="aa514-107">Properties</span></span>

|<span data-ttu-id="aa514-108">properties</span><span class="sxs-lookup"><span data-stu-id="aa514-108">Property</span></span> |<span data-ttu-id="aa514-109">说明</span><span class="sxs-lookup"><span data-stu-id="aa514-109">Description</span></span> |
|---|---|
|<span data-ttu-id="aa514-110">密钥</span><span class="sxs-lookup"><span data-stu-id="aa514-110">Key</span></span> |<span data-ttu-id="aa514-111">指示要确保其特定状态的注册表项的路径。</span><span class="sxs-lookup"><span data-stu-id="aa514-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="aa514-112">路径必须包含配置单元。</span><span class="sxs-lookup"><span data-stu-id="aa514-112">This path must include the hive.</span></span> |
|<span data-ttu-id="aa514-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="aa514-113">ValueName</span></span> |<span data-ttu-id="aa514-114">指示注册表值的名称。</span><span class="sxs-lookup"><span data-stu-id="aa514-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="aa514-115">若要添加或删除注册表项，请将此属性指定为空字符串，无需指定 **ValueType** 或 **ValueData**。</span><span class="sxs-lookup"><span data-stu-id="aa514-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData**.</span></span> <span data-ttu-id="aa514-116">若要修改或删除注册表项的默认值，请将此属性指定为空字符串，同时指定 **ValueType** 或 **ValueData**。</span><span class="sxs-lookup"><span data-stu-id="aa514-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData**.</span></span> |
|<span data-ttu-id="aa514-117">Force</span><span class="sxs-lookup"><span data-stu-id="aa514-117">Force</span></span> |<span data-ttu-id="aa514-118">如果指定的注册表项存在，**Force** 将用新值覆盖它。</span><span class="sxs-lookup"><span data-stu-id="aa514-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="aa514-119">如果要删除包含子项的注册表项，这必须是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="aa514-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="aa514-120">Hex</span><span class="sxs-lookup"><span data-stu-id="aa514-120">Hex</span></span> |<span data-ttu-id="aa514-121">指示是否以十六进制格式表示数据。</span><span class="sxs-lookup"><span data-stu-id="aa514-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="aa514-122">如果指定此项，则以十六进制格式显示 DWORD/QWORD 值数据。</span><span class="sxs-lookup"><span data-stu-id="aa514-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="aa514-123">对其他类型无效。</span><span class="sxs-lookup"><span data-stu-id="aa514-123">Not valid for other types.</span></span> <span data-ttu-id="aa514-124">默认值是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aa514-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="aa514-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="aa514-125">ValueData</span></span> |<span data-ttu-id="aa514-126">注册表值的数据。</span><span class="sxs-lookup"><span data-stu-id="aa514-126">The data for the registry value.</span></span> |
|<span data-ttu-id="aa514-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="aa514-127">ValueType</span></span> |<span data-ttu-id="aa514-128">指示值的类型。</span><span class="sxs-lookup"><span data-stu-id="aa514-128">Indicates the type of the value.</span></span> <span data-ttu-id="aa514-129">支持的类型包括：**String** (REG_SZ)、**Binary** (REG-BINARY)、**Dword**（32 位 REG_DWORD）、**Qword**（64 位 REG_QWORD）、**MultiString** (REG_MULTI_SZ)、**ExpandString** (REG_EXPAND_SZ)。</span><span class="sxs-lookup"><span data-stu-id="aa514-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="aa514-130">公共属性</span><span class="sxs-lookup"><span data-stu-id="aa514-130">Common properties</span></span>

|<span data-ttu-id="aa514-131">properties</span><span class="sxs-lookup"><span data-stu-id="aa514-131">Property</span></span> |<span data-ttu-id="aa514-132">说明</span><span class="sxs-lookup"><span data-stu-id="aa514-132">Description</span></span> |
|---|---|
|<span data-ttu-id="aa514-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aa514-133">DependsOn</span></span> |<span data-ttu-id="aa514-134">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="aa514-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aa514-135">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="aa514-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="aa514-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="aa514-136">Ensure</span></span> |<span data-ttu-id="aa514-137">指示项和值是否存在。</span><span class="sxs-lookup"><span data-stu-id="aa514-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="aa514-138">若要确保其存在，请将此属性设置为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="aa514-138">To ensure that they do, set this property to **Present**.</span></span> <span data-ttu-id="aa514-139">若要确保其不存在，请将此属性设置为 **Absent**。</span><span class="sxs-lookup"><span data-stu-id="aa514-139">To ensure that they do not exist, set the property to **Absent**.</span></span> <span data-ttu-id="aa514-140">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="aa514-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="aa514-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="aa514-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="aa514-142">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="aa514-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="aa514-143">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="aa514-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="aa514-144">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="aa514-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="aa514-145">示例</span><span class="sxs-lookup"><span data-stu-id="aa514-145">Example</span></span>

<span data-ttu-id="aa514-146">此示例确保名为“ExampleKey”的键存在于 **HKEY\_LOCAL\_MACHINE** 配置单元中。</span><span class="sxs-lookup"><span data-stu-id="aa514-146">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="aa514-147">必须使用用户凭据运行配置，而不是以系统身份运行，才能在 `HKEY_CURRENT_USER` 配置单元中更改注册表设置。</span><span class="sxs-lookup"><span data-stu-id="aa514-147">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="aa514-148">可以使用 **PsDscRunAsCredential** 属性来指定配置的用户凭据。</span><span class="sxs-lookup"><span data-stu-id="aa514-148">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="aa514-149">有关示例，请参阅[使用用户凭据运行 DSC](../../../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="aa514-149">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
