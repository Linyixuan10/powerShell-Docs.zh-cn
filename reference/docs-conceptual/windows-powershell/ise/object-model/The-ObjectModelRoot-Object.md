---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: ObjectModelRoot 对象
ms.openlocfilehash: cd94e69de2e62f7ce9fac413e15458ae9986540e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809563"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot 对象

Windows PowerShell® 集成脚本环境 (ISE) 中的主体根对象（`$psISE` 对象）是 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 类的实例。 本主题介绍 **ObjectModelRoot** 对象的属性。

## <a name="properties"></a>属性

### <a name="currentfile"></a>CurrentFile

> 在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取与该主机对象相关联的当前具有焦点的文件。

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> 在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取具有焦点的 PowerShell 选项卡。

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> 在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取位于编辑器底部水平工具窗格中、当前可见的 Windows PowerShell ISE 加载项工具。

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> 在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取位于编辑器右侧竖直工具窗格中、当前可见的 Windows PowerShell ISE 加载项工具。

### <a name="options"></a>选项

> 在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取可以更改 Windows PowerShell ISE 中设置的各种选项。

### <a name="powershelltabs"></a>PowerShellTabs

> 在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取 Windows PowerShell ISE 中打开的 PowerShell 选项卡的集合。 默认情况下，此对象包含一个 PowerShell 选项卡。但是，可以将更多 PowerShell 选项卡添加到此对象中，方法是通过使用脚本或者使用 Windows PowerShell ISE 中的菜单。

## <a name="see-also"></a>另请参阅

- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
