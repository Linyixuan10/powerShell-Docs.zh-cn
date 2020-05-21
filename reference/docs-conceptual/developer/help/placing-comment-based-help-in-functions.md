---
title: 在函数中放置基于注释的帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: 898225a582c7ed25f746dec7f84012db1ae60b98
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557052"
---
# <a name="placing-comment-based-help-in-functions"></a>在函数中放置基于注释的帮助

本主题介绍在何处放置函数的基于注释的帮助，以便该 `Get-Help` cmdlet 将基于注释的帮助主题与正确的函数相关联。

## <a name="where-to-place-comment-based-help-for-a-function"></a>在何处放置函数的基于注释的帮助

- 函数体的开头。

- 函数体的末尾。

- 关键字之前 `Function` 。 当函数在脚本或脚本模块中时，基于注释的帮助的最后一行与关键字之间不能有多个空行 `Function` 。 否则， `Get-Help` 将帮助与脚本相关联，而不是与函数相关联。

## <a name="examples-of-help-placement-in-a-function"></a>函数中帮助位置的示例

 下面的示例显示了三个位置选项中的每一个选项，用于为函数提供基于注释的帮助。

### <a name="help-at-the-beginning-of-a-function-body"></a>函数体开始的帮助

 下面的示例显示了函数体开头的注释。

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>函数体末尾的帮助

 下面的示例显示了函数体末尾的注释。

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>函数关键字之前的帮助

 下面的示例显示了基于函数关键字之前的行的注释。

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```
