---
title: 可更新的帮助 CAB 文件中允许的文件类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 6e9e51a50226430465726d27874e02e98ee67672
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811536"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="ba9fc-102">可更新帮助 CAB 文件中允许的文件类型</span><span class="sxs-lookup"><span data-stu-id="ba9fc-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="ba9fc-103">本主题列出并描述了可更新的帮助 CAB 文件的内容要求。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="ba9fc-104">可更新的帮助 CAB 文件要求</span><span class="sxs-lookup"><span data-stu-id="ba9fc-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="ba9fc-105">默认情况下，未压缩的 CAB 文件内容限制为 1 GB。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="ba9fc-106">若要绕过此限制，用户必须使用[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[Get-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 的**Force**参数。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="ba9fc-107">若要确保从 Internet 下载的帮助文件的安全性，可更新的 Help CAB 文件只能包含下面列出的文件类型。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="ba9fc-108">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 根据帮助主题架构验证所有文件。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="ba9fc-109">如果此 `Update-Help` cmdlet 遇到无效的文件或不是允许的类型，则它不会安装无效文件，并且不会在用户的计算机上停止从 CAB 安装文件。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="ba9fc-110">基于 XML 的 cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="ba9fc-111">基于 XML 的脚本和函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="ba9fc-112">适用于 Windows PowerShell 提供程序的基于 XML 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="ba9fc-113">基于文本的帮助主题，如 "关于" 主题。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="ba9fc-114">当解压缩 CAB 时， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)会验证 cab 内容。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="ba9fc-115">如果 `Update-Help` 在可更新的 HELP CAB 文件中查找不符合的文件类型，则会生成一个终止错误并停止该操作。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="ba9fc-116">它不会从 CAB 中安装任何帮助文件，甚至不会从兼容的文件类型安装任何帮助文件。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>
