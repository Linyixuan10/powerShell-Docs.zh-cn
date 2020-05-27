---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxPackage 资源
ms.openlocfilehash: 49eef4adc9700a13bfb1e96457d90898a353d60d
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560825"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="18f65-103">适用于 Linux 的 DSC nxPackage 资源</span><span class="sxs-lookup"><span data-stu-id="18f65-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="18f65-104">PowerShell Desired State Configuration (DSC) 中的 **nxPackage** 资源提供了在 Linux 节点上管理程序包的机制。</span><span class="sxs-lookup"><span data-stu-id="18f65-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="18f65-105">语法</span><span class="sxs-lookup"><span data-stu-id="18f65-105">Syntax</span></span>

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="18f65-106">属性</span><span class="sxs-lookup"><span data-stu-id="18f65-106">Properties</span></span>

|<span data-ttu-id="18f65-107">properties</span><span class="sxs-lookup"><span data-stu-id="18f65-107">Property</span></span> |<span data-ttu-id="18f65-108">说明</span><span class="sxs-lookup"><span data-stu-id="18f65-108">Description</span></span> |
|---|---|
|<span data-ttu-id="18f65-109">名称</span><span class="sxs-lookup"><span data-stu-id="18f65-109">Name</span></span> |<span data-ttu-id="18f65-110">要确保其特定状态的程序包的名称。</span><span class="sxs-lookup"><span data-stu-id="18f65-110">The name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="18f65-111">PackageManager</span><span class="sxs-lookup"><span data-stu-id="18f65-111">PackageManager</span></span> |<span data-ttu-id="18f65-112">支持的值包括 **yum**、**apt** 和 **zypper**。</span><span class="sxs-lookup"><span data-stu-id="18f65-112">Supported values are **yum**, **apt**, and **zypper**.</span></span> <span data-ttu-id="18f65-113">指定安装程序包时要使用的程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="18f65-113">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="18f65-114">如果指定了 **FilePath**，则将使用提供的路径安装程序包。</span><span class="sxs-lookup"><span data-stu-id="18f65-114">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="18f65-115">否则，将使用程序包管理器从预配置的存储库安装程序包。</span><span class="sxs-lookup"><span data-stu-id="18f65-115">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="18f65-116">如果既不提供 **PackageManager**，也不提供 **FilePath**，则将使用系统默认的程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="18f65-116">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span> |
|<span data-ttu-id="18f65-117">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="18f65-117">PackageGroup</span></span> |<span data-ttu-id="18f65-118">如果为 `$true`，则 **Name** 应为用于 **PackageManager** 的包组的名称。</span><span class="sxs-lookup"><span data-stu-id="18f65-118">If `$true`, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="18f65-119">提供 **FilePath** 时，**PackageGroup** 无效。</span><span class="sxs-lookup"><span data-stu-id="18f65-119">**PackageGroup** is not valid when providing a **FilePath**.</span></span> |
|<span data-ttu-id="18f65-120">参数</span><span class="sxs-lookup"><span data-stu-id="18f65-120">Arguments</span></span> |<span data-ttu-id="18f65-121">将完全按原样传输给程序包的参数字符串。</span><span class="sxs-lookup"><span data-stu-id="18f65-121">A string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="18f65-122">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="18f65-122">ReturnCode</span></span> |<span data-ttu-id="18f65-123">预期的返回代码。</span><span class="sxs-lookup"><span data-stu-id="18f65-123">The expected return code.</span></span> <span data-ttu-id="18f65-124">如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。</span><span class="sxs-lookup"><span data-stu-id="18f65-124">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |
|<span data-ttu-id="18f65-125">文件路径</span><span class="sxs-lookup"><span data-stu-id="18f65-125">FilePath</span></span> |<span data-ttu-id="18f65-126">包所在的文件路径。</span><span class="sxs-lookup"><span data-stu-id="18f65-126">The file path where the package resides.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="18f65-127">公共属性</span><span class="sxs-lookup"><span data-stu-id="18f65-127">Common properties</span></span>

|<span data-ttu-id="18f65-128">properties</span><span class="sxs-lookup"><span data-stu-id="18f65-128">Property</span></span> |<span data-ttu-id="18f65-129">说明</span><span class="sxs-lookup"><span data-stu-id="18f65-129">Description</span></span> |
|---|---|
|<span data-ttu-id="18f65-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="18f65-130">DependsOn</span></span> |<span data-ttu-id="18f65-131">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="18f65-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="18f65-132">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="18f65-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="18f65-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="18f65-133">Ensure</span></span> |<span data-ttu-id="18f65-134">确定是否检查程序包是否存在。</span><span class="sxs-lookup"><span data-stu-id="18f65-134">Determines whether to check if the package exists.</span></span> <span data-ttu-id="18f65-135">将此属性设置为 **Present** 可确保包存在。</span><span class="sxs-lookup"><span data-stu-id="18f65-135">Set this property to **Present** to ensure the package exists.</span></span> <span data-ttu-id="18f65-136">将其设置为 **Absent** 可确保包不存在。</span><span class="sxs-lookup"><span data-stu-id="18f65-136">Set it to **Absent** to ensure the package does not exist.</span></span> <span data-ttu-id="18f65-137">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="18f65-137">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="18f65-138">示例</span><span class="sxs-lookup"><span data-stu-id="18f65-138">Example</span></span>

<span data-ttu-id="18f65-139">以下示例确保使用“Yum”包管理器在 Linux 计算机上安装了名为“httpd”的包。</span><span class="sxs-lookup"><span data-stu-id="18f65-139">The following example ensures that the package named "httpd" is installed on a Linux computer, using the "Yum" package manager.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```
