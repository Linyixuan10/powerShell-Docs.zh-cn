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
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection 对象

**PowerShellTab** 集合对象是 **PowerShellTab** 对象的集合。 每个 **PowerShellTab** 对象充当一个单独的运行时环境。 它是 Microsoft.PowerShell.Host.ISE.PowerShellTabs 类的实例。 `$psISE.PowerShellTabs` 对象就是一个示例。

## <a name="methods"></a>方法

### <a name="add"></a>添加\(\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

向集合中添加一个新的 PowerShell 选项卡。 它将返回新添加的选项卡。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

删除由 **psTab** 参数指定的选项卡。

**psTab** 要删除的 PowerShell 选项卡。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

选择由 **psTab** 参数指定的 PowerShell 选项卡，以使它当前是处于活动状态的 PowerShell 选项卡。

**psTab** 要选择的 PowerShell 选项卡。

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

## <a name="see-also"></a>另请参阅

- [PowerShellTab 对象](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
