---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Service 资源
ms.openlocfilehash: acd0710fb4b131876e3edece15b07cff8e9a8a9e
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83556999"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="19a17-103">DSC Service 资源</span><span class="sxs-lookup"><span data-stu-id="19a17-103">DSC Service Resource</span></span>

> <span data-ttu-id="19a17-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="19a17-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="19a17-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Service** 资源提供了在目标节点上管理服务的机制。</span><span class="sxs-lookup"><span data-stu-id="19a17-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="19a17-106">语法</span><span class="sxs-lookup"><span data-stu-id="19a17-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="19a17-107">属性</span><span class="sxs-lookup"><span data-stu-id="19a17-107">Properties</span></span>

|<span data-ttu-id="19a17-108">properties</span><span class="sxs-lookup"><span data-stu-id="19a17-108">Property</span></span> |<span data-ttu-id="19a17-109">说明</span><span class="sxs-lookup"><span data-stu-id="19a17-109">Description</span></span> |
|---|---|
|<span data-ttu-id="19a17-110">名称</span><span class="sxs-lookup"><span data-stu-id="19a17-110">Name</span></span> |<span data-ttu-id="19a17-111">指示服务名称。</span><span class="sxs-lookup"><span data-stu-id="19a17-111">Indicates the service name.</span></span> <span data-ttu-id="19a17-112">请注意，有时它与显示名称不同。</span><span class="sxs-lookup"><span data-stu-id="19a17-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="19a17-113">可使用 `Get-Service` cmdlet 获取服务及其当前状态的列表。</span><span class="sxs-lookup"><span data-stu-id="19a17-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="19a17-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="19a17-114">BuiltInAccount</span></span> |<span data-ttu-id="19a17-115">指示要用于服务的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="19a17-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="19a17-116">允许用于此属性的值有：LocalService  、LocalSystem  和 NetworkService  。</span><span class="sxs-lookup"><span data-stu-id="19a17-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="19a17-117">凭据</span><span class="sxs-lookup"><span data-stu-id="19a17-117">Credential</span></span> |<span data-ttu-id="19a17-118">指示服务将在其下运行的帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="19a17-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="19a17-119">此属性与 **BuiltinAccount** 属性不能一起使用。</span><span class="sxs-lookup"><span data-stu-id="19a17-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="19a17-120">StartupType</span><span class="sxs-lookup"><span data-stu-id="19a17-120">StartupType</span></span> |<span data-ttu-id="19a17-121">设置服务的启动类型。</span><span class="sxs-lookup"><span data-stu-id="19a17-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="19a17-122">允许用于此属性的值有：**Automatic**、**Disabled** 和 **Manual**。</span><span class="sxs-lookup"><span data-stu-id="19a17-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="19a17-123">状态</span><span class="sxs-lookup"><span data-stu-id="19a17-123">State</span></span> |<span data-ttu-id="19a17-124">指示你想要确保服务所处的状态。</span><span class="sxs-lookup"><span data-stu-id="19a17-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="19a17-125">有效值为：**Running** 或 **Stopped**。</span><span class="sxs-lookup"><span data-stu-id="19a17-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="19a17-126">说明</span><span class="sxs-lookup"><span data-stu-id="19a17-126">Description</span></span> |<span data-ttu-id="19a17-127">指示目标服务的说明。</span><span class="sxs-lookup"><span data-stu-id="19a17-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="19a17-128">DisplayName</span><span class="sxs-lookup"><span data-stu-id="19a17-128">DisplayName</span></span> |<span data-ttu-id="19a17-129">指示目标服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="19a17-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="19a17-130">路径</span><span class="sxs-lookup"><span data-stu-id="19a17-130">Path</span></span> |<span data-ttu-id="19a17-131">指示新服务的二进制文件的路径。</span><span class="sxs-lookup"><span data-stu-id="19a17-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="19a17-132">公共属性</span><span class="sxs-lookup"><span data-stu-id="19a17-132">Common properties</span></span>

|<span data-ttu-id="19a17-133">properties</span><span class="sxs-lookup"><span data-stu-id="19a17-133">Property</span></span> |<span data-ttu-id="19a17-134">说明</span><span class="sxs-lookup"><span data-stu-id="19a17-134">Description</span></span> |
|---|---|
|<span data-ttu-id="19a17-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="19a17-135">DependsOn</span></span> |<span data-ttu-id="19a17-136">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="19a17-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="19a17-137">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="19a17-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="19a17-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="19a17-138">Ensure</span></span> |<span data-ttu-id="19a17-139">指示目标服务是否在系统中存在。</span><span class="sxs-lookup"><span data-stu-id="19a17-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="19a17-140">将此属性设置为 **Absent** 可确保目标服务不存在。</span><span class="sxs-lookup"><span data-stu-id="19a17-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="19a17-141">将其设置为 **Present** 可确保目标服务存在。</span><span class="sxs-lookup"><span data-stu-id="19a17-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="19a17-142">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="19a17-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="19a17-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="19a17-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="19a17-144">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="19a17-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="19a17-145">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="19a17-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="19a17-146">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="19a17-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="19a17-147">示例</span><span class="sxs-lookup"><span data-stu-id="19a17-147">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
