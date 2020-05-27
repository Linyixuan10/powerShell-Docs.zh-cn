---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShellTabCollection 对象
ms.openlocfilehash: 0aad885afd3ba3ae3b00f5c11d2c62a9ff303798
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808563"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="cd763-103">PowerShellTabCollection 对象</span><span class="sxs-lookup"><span data-stu-id="cd763-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="cd763-104">**PowerShellTab** 集合对象是 **PowerShellTab** 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="cd763-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="cd763-105">每个 **PowerShellTab** 对象充当一个单独的运行时环境。</span><span class="sxs-lookup"><span data-stu-id="cd763-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="cd763-106">它是 Microsoft.PowerShell.Host.ISE.PowerShellTabs 类的实例。</span><span class="sxs-lookup"><span data-stu-id="cd763-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="cd763-107">`$psISE.PowerShellTabs` 对象就是一个示例。</span><span class="sxs-lookup"><span data-stu-id="cd763-107">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="cd763-108">方法</span><span class="sxs-lookup"><span data-stu-id="cd763-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="cd763-109">添加\(\)</span><span class="sxs-lookup"><span data-stu-id="cd763-109">Add\(\)</span></span>

<span data-ttu-id="cd763-110">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="cd763-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cd763-111">向集合中添加一个新的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="cd763-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="cd763-112">它将返回新添加的选项卡。</span><span class="sxs-lookup"><span data-stu-id="cd763-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="cd763-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="cd763-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="cd763-114">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="cd763-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cd763-115">删除由 **psTab** 参数指定的选项卡。</span><span class="sxs-lookup"><span data-stu-id="cd763-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="cd763-116">**psTab** 要删除的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="cd763-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="cd763-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="cd763-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="cd763-118">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="cd763-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cd763-119">选择由 **psTab** 参数指定的 PowerShell 选项卡，以使它当前是处于活动状态的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="cd763-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="cd763-120">**psTab** 要选择的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="cd763-120">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="cd763-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd763-121">See Also</span></span>

- [<span data-ttu-id="cd763-122">PowerShellTab 对象</span><span class="sxs-lookup"><span data-stu-id="cd763-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="cd763-123">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="cd763-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="cd763-124">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="cd763-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
