---
title: 可更新帮助的工作方式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: e555741185f3d17b4099671d70dbc0545bfd5306
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560230"
---
# <a name="how-updatable-help-works"></a><span data-ttu-id="96cef-102">可更新帮助的工作原理</span><span class="sxs-lookup"><span data-stu-id="96cef-102">How Updatable Help Works</span></span>

<span data-ttu-id="96cef-103">本主题介绍了可更新的帮助如何处理每个模块的 HelpInfo XML 文件和 CAB 文件，并为用户安装更新的帮助。</span><span class="sxs-lookup"><span data-stu-id="96cef-103">This topic explains how Updatable Help processes the HelpInfo XML file and CAB files for each module, and installs updated help for users.</span></span>

## <a name="the-update-help-process"></a><span data-ttu-id="96cef-104">Update-help 过程</span><span class="sxs-lookup"><span data-stu-id="96cef-104">The Update-Help Process</span></span>

<span data-ttu-id="96cef-105">以下列表描述了当用户运行命令来更新特定 UI 区域性中的模块的帮助文件时， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="96cef-105">The following list describes the actions of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet when a user runs a command to update the help files for a module in a particular UI culture.</span></span>

1. <span data-ttu-id="96cef-106">`Update-Help`从模块清单中的**HelpInfoURI**键值指定的位置获取远程 HelpInfo XML 文件，并根据架构验证该文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-106">`Update-Help` gets the remote HelpInfo XML file from the location specified by the value of the **HelpInfoURI** key in the module manifest and validates the file against the schema.</span></span> <span data-ttu-id="96cef-107">（若要查看架构，请参阅[HELPINFO XML 架构](./helpinfo-xml-schema.md)。）然后， `Update-Help` 在用户计算机上的模块目录中查找模块的本地 HELPINFO XML 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-107">(To view the schema, see [HelpInfo XML Schema](./helpinfo-xml-schema.md).) Then `Update-Help` looks for a local HelpInfo XML file for the module in the module directory on the user's computer.</span></span>

2. <span data-ttu-id="96cef-108">`Update-Help`对模块的远程和本地 HelpInfo XML 文件中指定 UI 区域性的帮助文件的版本号进行比较。</span><span class="sxs-lookup"><span data-stu-id="96cef-108">`Update-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="96cef-109">如果远程文件上的版本号大于本地文件上的版本号，或者该模块没有本地 HelpInfo XML 文件，则 `Update-Help` 准备下载新的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-109">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file for the module, `Update-Help` prepares to download new help files.</span></span>

3. <span data-ttu-id="96cef-110">`Update-Help`从远程 HelpInfo XML 文件中的**HelpContentUri**元素指定的位置选择模块的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-110">`Update-Help` selects the CAB file for the module from the location specified by the **HelpContentUri** element in the remote HelpInfo XML file.</span></span> <span data-ttu-id="96cef-111">它使用模块名称、模块 GUID 和 UI 区域性来标识 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-111">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="96cef-112">`Update-Help`下载 CAB 文件，解压缩它，验证帮助内容文件，并将帮助内容文件保存在用户计算机上的模块目录的特定于语言的子目录中。</span><span class="sxs-lookup"><span data-stu-id="96cef-112">`Update-Help` downloads the CAB file, unpacks it, validates the help content files, and saves the help content files in the language-specific subdirectory of the module directory on the user's computer.</span></span>

5. <span data-ttu-id="96cef-113">`Update-Help`通过复制远程 HelpInfo XML 文件来创建本地 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-113">`Update-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="96cef-114">它编辑本地 HelpInfo XML 文件，使其仅包含它所安装的 CAB 文件的元素。</span><span class="sxs-lookup"><span data-stu-id="96cef-114">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it installed.</span></span> <span data-ttu-id="96cef-115">然后，它将本地 HelpInfo XML 文件保存到模块目录中并结束更新。</span><span class="sxs-lookup"><span data-stu-id="96cef-115">Then it saves the local HelpInfo XML file in the module directory and concludes the update.</span></span>

## <a name="the-save-help-process"></a><span data-ttu-id="96cef-116">保存帮助过程</span><span class="sxs-lookup"><span data-stu-id="96cef-116">The Save-Help Process</span></span>

<span data-ttu-id="96cef-117">下面的列表介绍当用户运行命令来更新文件共享中的帮助文件，然后使用这些文件来更新用户计算机上的帮助文件时， [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)和[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="96cef-117">The following list describes the actions of the [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) and [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets when a user runs commands to update the help files in a file share, and then use those files to update the help files on the user's computer.</span></span>

<span data-ttu-id="96cef-118">该 `Save-Help` cmdlet 将执行以下操作，以响应命令，以将模块的帮助文件保存在由**DestinationPath**参数指定的文件共享中。</span><span class="sxs-lookup"><span data-stu-id="96cef-118">The `Save-Help` cmdlet performs the following actions in response to a command to save the help files for a module in a file share that is specified by the **DestinationPath** parameter.</span></span>

1. <span data-ttu-id="96cef-119">`Save-Help`从模块清单中的**HelpInfoURI**键值指定的位置获取远程 HelpInfo XML 文件，并根据架构验证该文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-119">`Save-Help` gets  the remote HelpInfo XML file from the location specified by the value of the **HelpInfoURI** key in the module manifest and validates the file against the schema.</span></span> <span data-ttu-id="96cef-120">（若要查看架构，请参阅[HELPINFO XML 架构](./helpinfo-xml-schema.md)。）然后，在 `Save-Help` 命令中查找由**DestinationPath**参数指定的目录中的本地 HelpInfo XML 文件 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="96cef-120">(To view the schema, see [HelpInfo XML Schema](./helpinfo-xml-schema.md).) Then `Save-Help` looks for a local HelpInfo XML file in the directory that is specified by the **DestinationPath** parameter in the `Save-Help` command.</span></span>

2. <span data-ttu-id="96cef-121">`Save-Help`对模块的远程和本地 HelpInfo XML 文件中指定 UI 区域性的帮助文件的版本号进行比较。</span><span class="sxs-lookup"><span data-stu-id="96cef-121">`Save-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="96cef-122">如果远程文件上的版本号大于本地文件上的版本号，或者在**DestinationPath**目录中没有该模块的本地 HelpInfo XML 文件，则 `Save-Help` 准备下载新的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-122">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file for the module in the **DestinationPath** directory, `Save-Help` prepares to download new help files.</span></span>

3. <span data-ttu-id="96cef-123">`Save-Help`从远程 HelpInfo XML 文件中的**HelpContentUri**元素指定的位置选择模块的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-123">`Save-Help` selects the CAB file for the module from the location specified by the **HelpContentUri** element in the remote HelpInfo XML file.</span></span> <span data-ttu-id="96cef-124">它使用模块名称、模块 GUID 和 UI 区域性来标识 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-124">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="96cef-125">`Save-Help`下载 CAB 文件并将其保存在**DestinationPath**目录中。</span><span class="sxs-lookup"><span data-stu-id="96cef-125">`Save-Help` downloads the CAB file and saves it in the **DestinationPath** directory.</span></span> <span data-ttu-id="96cef-126">（它不创建任何特定于语言的子目录。）</span><span class="sxs-lookup"><span data-stu-id="96cef-126">(It does not create any language-specific subdirectories.)</span></span>

5. <span data-ttu-id="96cef-127">`Save-Help`通过复制远程 HelpInfo XML 文件来创建本地 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-127">`Save-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="96cef-128">它编辑本地 HelpInfo XML 文件，使其仅包含它保存的 CAB 文件的元素。</span><span class="sxs-lookup"><span data-stu-id="96cef-128">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it saved.</span></span> <span data-ttu-id="96cef-129">然后，它将本地 HelpInfo XML 文件保存在**DestinationPath**目录中，并结束更新。</span><span class="sxs-lookup"><span data-stu-id="96cef-129">Then it saves the local HelpInfo XML file in the  **DestinationPath** directory and concludes the update.</span></span>

   <span data-ttu-id="96cef-130">该 `Update-Help` cmdlet 将执行以下操作，以响应命令，以便从**SourcePath**参数所指定的文件共享中的文件更新用户计算机上的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-130">The `Update-Help` cmdlet performs the following actions in response to a command to update the help files on a user's computer from the files in a file share that is specified by the **SourcePath** parameter.</span></span>

1. <span data-ttu-id="96cef-131">`Update-Help`获取**SourcePath**目录中的远程 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-131">`Update-Help` gets the remote HelpInfo XML file from the **SourcePath** directory.</span></span> <span data-ttu-id="96cef-132">然后，它将在用户计算机上的模块目录中查找本地 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-132">Then it looks for a local HelpInfo XML file in the module directory on the user's computer.</span></span>

2. <span data-ttu-id="96cef-133">`Update-Help`对模块的远程和本地 HelpInfo XML 文件中指定 UI 区域性的帮助文件的版本号进行比较。</span><span class="sxs-lookup"><span data-stu-id="96cef-133">`Update-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="96cef-134">如果远程文件上的版本号大于本地文件上的版本号，或者如果没有本地 HelpInfo XML 文件，则 `Update-Help` 准备安装新的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-134">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file, `Update-Help` prepares to install new help files.</span></span>

3. <span data-ttu-id="96cef-135">`Update-Help`从**SourcePath**目录中选择模块的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-135">`Update-Help` selects the CAB file for the module from **SourcePath** directory.</span></span> <span data-ttu-id="96cef-136">它使用模块名称、模块 GUID 和 UI 区域性来标识 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-136">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="96cef-137">`Update-Help`解压缩 CAB 文件，验证帮助内容文件，并将帮助内容文件保存在用户计算机上的模块目录的特定于语言的子目录中。</span><span class="sxs-lookup"><span data-stu-id="96cef-137">`Update-Help` unpacks the CAB file, validates the help content files, and saves the help content files in the language-specific subdirectory of the module directory on the user's computer.</span></span>

5. <span data-ttu-id="96cef-138">`Update-Help`通过复制远程 HelpInfo XML 文件来创建本地 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="96cef-138">`Update-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="96cef-139">它编辑本地 HelpInfo XML 文件，使其仅包含它所安装的 CAB 文件的元素。</span><span class="sxs-lookup"><span data-stu-id="96cef-139">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it installed.</span></span> <span data-ttu-id="96cef-140">然后，它将本地 HelpInfo XML 文件保存到模块目录中并结束更新。</span><span class="sxs-lookup"><span data-stu-id="96cef-140">Then it saves the local HelpInfo XML file in the module directory and concludes the update.</span></span>
