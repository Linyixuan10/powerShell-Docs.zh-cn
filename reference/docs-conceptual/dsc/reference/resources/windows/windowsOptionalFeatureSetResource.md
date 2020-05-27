---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsOptionalFeatureSet 资源
ms.openlocfilehash: 0930bd0c6d1955005ea607b610e004818c0ad06f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560145"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="874d0-103">DSC WindowsOptionalFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="874d0-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="874d0-104">适用于：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="874d0-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="874d0-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsOptionalFeatureSet** 资源提供了确保在目标节点上启用可选功能的机制。</span><span class="sxs-lookup"><span data-stu-id="874d0-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="874d0-106">此资源是[复合资源](../../../resources/authoringResourceComposite.md)，它会针对 **Name** 属性中指定的每个功能调用 [WindowsOptionalFeature 资源](windowsOptionalFeatureResource.md)。</span><span class="sxs-lookup"><span data-stu-id="874d0-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="874d0-107">要将一些 Windows 可选功能配置为相同状态时，请使用此资源。</span><span class="sxs-lookup"><span data-stu-id="874d0-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="874d0-108">语法</span><span class="sxs-lookup"><span data-stu-id="874d0-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="874d0-109">属性</span><span class="sxs-lookup"><span data-stu-id="874d0-109">Properties</span></span>

|<span data-ttu-id="874d0-110">properties</span><span class="sxs-lookup"><span data-stu-id="874d0-110">Property</span></span> |<span data-ttu-id="874d0-111">说明</span><span class="sxs-lookup"><span data-stu-id="874d0-111">Description</span></span> |
|---|---|
|<span data-ttu-id="874d0-112">名称</span><span class="sxs-lookup"><span data-stu-id="874d0-112">Name</span></span> |<span data-ttu-id="874d0-113">指示要确保启用或禁用的功能的名称。</span><span class="sxs-lookup"><span data-stu-id="874d0-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="874d0-114">源</span><span class="sxs-lookup"><span data-stu-id="874d0-114">Source</span></span> |<span data-ttu-id="874d0-115">未实现。</span><span class="sxs-lookup"><span data-stu-id="874d0-115">Not implemented.</span></span> |
|<span data-ttu-id="874d0-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="874d0-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="874d0-117">指定 DISM 在搜索源文件以启用功能时是否联系 Windows 更新 (WU)。</span><span class="sxs-lookup"><span data-stu-id="874d0-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="874d0-118">如果为 `$true`，则 DISM 不联系 WU。</span><span class="sxs-lookup"><span data-stu-id="874d0-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="874d0-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="874d0-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="874d0-120">当 **Ensure** 设置为 **Absent** 时，设置为 `$true` 以删除与功能关联的所有文件。</span><span class="sxs-lookup"><span data-stu-id="874d0-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="874d0-121">LogLevel</span><span class="sxs-lookup"><span data-stu-id="874d0-121">LogLevel</span></span> |<span data-ttu-id="874d0-122">日志中显示的最大输出级别。</span><span class="sxs-lookup"><span data-stu-id="874d0-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="874d0-123">接受的值包括：**ErrorsOnly**、**ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation**。</span><span class="sxs-lookup"><span data-stu-id="874d0-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="874d0-124">LogPath</span><span class="sxs-lookup"><span data-stu-id="874d0-124">LogPath</span></span> |<span data-ttu-id="874d0-125">希望资源提供程序在其中记录操作的日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="874d0-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="874d0-126">公共属性</span><span class="sxs-lookup"><span data-stu-id="874d0-126">Common properties</span></span>

|<span data-ttu-id="874d0-127">properties</span><span class="sxs-lookup"><span data-stu-id="874d0-127">Property</span></span> |<span data-ttu-id="874d0-128">说明</span><span class="sxs-lookup"><span data-stu-id="874d0-128">Description</span></span> |
|---|---|
|<span data-ttu-id="874d0-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="874d0-129">DependsOn</span></span> |<span data-ttu-id="874d0-130">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="874d0-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="874d0-131">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="874d0-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="874d0-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="874d0-132">Ensure</span></span> |<span data-ttu-id="874d0-133">指定是否启用功能。</span><span class="sxs-lookup"><span data-stu-id="874d0-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="874d0-134">若要确保启用功能，请将此属性设置为 **Enable**。</span><span class="sxs-lookup"><span data-stu-id="874d0-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="874d0-135">若要确保禁用功能，请将此属性设置为 **Disable**。</span><span class="sxs-lookup"><span data-stu-id="874d0-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="874d0-136">默认值为 **Enable**。</span><span class="sxs-lookup"><span data-stu-id="874d0-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="874d0-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="874d0-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="874d0-138">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="874d0-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="874d0-139">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="874d0-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="874d0-140">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="874d0-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
