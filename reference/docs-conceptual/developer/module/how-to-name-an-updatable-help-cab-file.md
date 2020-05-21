---
title: 如何为可更新的帮助 CAB 文件命名 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560553"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="7c44c-102">如何命名可更新帮助 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="7c44c-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="7c44c-103">本主题介绍可更新帮助 cabinet 的必需名称格式（。CAB）文件。</span><span class="sxs-lookup"><span data-stu-id="7c44c-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="7c44c-104">如何命名可更新帮助 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="7c44c-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="7c44c-105">可更新的 cabinet （。CAB）文件必须具有以下格式的名称。</span><span class="sxs-lookup"><span data-stu-id="7c44c-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="7c44c-106">名称的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="7c44c-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="7c44c-107">ModuleName[获取 Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 返回的**ModuleInfo**对象的**Name**属性的值。</span><span class="sxs-lookup"><span data-stu-id="7c44c-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="7c44c-108">ModuleGUID 模块清单中**GUID**密钥的值。</span><span class="sxs-lookup"><span data-stu-id="7c44c-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="7c44c-109">UICulture CAB 文件中的帮助文件的 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="7c44c-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="7c44c-110">此值必须与模块的 HelpInfo XML 文件中的一个**UICulture**元素的值匹配。</span><span class="sxs-lookup"><span data-stu-id="7c44c-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="7c44c-111">例如，如果模块名称为 "TestModule"，则模块 GUID 为 9cabb9ad-f2ac 4914-a46b-bfc1bebf07f9，而 UI 区域性为 "en-us"，则 CAB 文件的名称将为：</span><span class="sxs-lookup"><span data-stu-id="7c44c-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
