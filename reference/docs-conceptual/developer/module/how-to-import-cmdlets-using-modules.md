---
title: 如何使用模块导入 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 840c5bc92d718ec4e54d864dc5e012cd33f83905
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811316"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="b5820-102">如何使用模块导入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5820-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="b5820-103">本文介绍如何使用二进制模块将 cmdlet 导入到 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="b5820-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="b5820-104">模块的成员可以包括 cmdlet、提供程序、函数、变量、别名等等。</span><span class="sxs-lookup"><span data-stu-id="b5820-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="b5820-105">管理单元只能包含 cmdlet 和提供程序。</span><span class="sxs-lookup"><span data-stu-id="b5820-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="b5820-106">如何使用模块加载 cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5820-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="b5820-107">创建与用于实现 cmdlet 的程序集文件同名的模块文件夹。</span><span class="sxs-lookup"><span data-stu-id="b5820-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="b5820-108">在此过程中，将在 Windows 文件夹中创建模块文件夹 `system32` 。</span><span class="sxs-lookup"><span data-stu-id="b5820-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="b5820-109">请确保 `PSModulePath` 环境变量包含新模块文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="b5820-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="b5820-110">默认情况下，系统文件夹已添加到 `PSModulePath` 环境变量中。</span><span class="sxs-lookup"><span data-stu-id="b5820-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="b5820-111">若要查看 `PSModulePath` ，请键入： `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="b5820-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="b5820-112">将 cmdlet 程序集复制到模块文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b5820-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="b5820-113">`.psd1`在模块的根文件夹中添加模块清单文件（）。</span><span class="sxs-lookup"><span data-stu-id="b5820-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="b5820-114">PowerShell 使用模块清单导入模块。</span><span class="sxs-lookup"><span data-stu-id="b5820-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="b5820-115">有关详细信息，请参阅[如何编写 PowerShell 模块清单](../module/how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="b5820-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="b5820-116">运行以下命令，将 cmdlet 添加到会话：</span><span class="sxs-lookup"><span data-stu-id="b5820-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="b5820-117">此过程可用于测试 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5820-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="b5820-118">它将程序集中的所有 cmdlet 添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="b5820-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="b5820-119">有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="b5820-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5820-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5820-120">See also</span></span>

[<span data-ttu-id="b5820-121">如何编写 PowerShell 模块清单</span><span class="sxs-lookup"><span data-stu-id="b5820-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="b5820-122">导入 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="b5820-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="b5820-123">Import-module</span><span class="sxs-lookup"><span data-stu-id="b5820-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="b5820-124">安装模块</span><span class="sxs-lookup"><span data-stu-id="b5820-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="b5820-125">修改 PSModulePath 安装路径</span><span class="sxs-lookup"><span data-stu-id="b5820-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="b5820-126">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5820-126">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
