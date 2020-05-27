---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISESnippetCollection 对象
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808573"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="cd1b5-103">ISESnippetCollection 对象</span><span class="sxs-lookup"><span data-stu-id="cd1b5-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="cd1b5-104">**ISESnippetCollection** 对象是 **ISESnippet** 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="cd1b5-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="cd1b5-105">与 **PowerShellTab** 对象关联的文件集合是此类的成员。</span><span class="sxs-lookup"><span data-stu-id="cd1b5-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="cd1b5-106">`$psISE.CurrentPowerShellTab.Files` 集合就是一个示例。</span><span class="sxs-lookup"><span data-stu-id="cd1b5-106">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="cd1b5-107">方法</span><span class="sxs-lookup"><span data-stu-id="cd1b5-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="cd1b5-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="cd1b5-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="cd1b5-109">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="cd1b5-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cd1b5-110">加载包含用户定义的代码段的 `.snippets.ps1xml` 文件。</span><span class="sxs-lookup"><span data-stu-id="cd1b5-110">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="cd1b5-111">创建代码段最简单的方法就是使用 `New-IseSnippet` cmdlet，后者会自动将它们存储在配置文件文件夹中，以便你每次启动 Windows PowerShell ISE 时进行加载。</span><span class="sxs-lookup"><span data-stu-id="cd1b5-111">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="cd1b5-112">**FilePathName** - 字符串，包含代码段定义的 .snippets.ps1xml 文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="cd1b5-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="cd1b5-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd1b5-113">See Also</span></span>

- [<span data-ttu-id="cd1b5-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="cd1b5-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="cd1b5-115">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="cd1b5-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="cd1b5-116">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="cd1b5-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
