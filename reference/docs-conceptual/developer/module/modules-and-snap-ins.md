---
title: 模块和管理单元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: b3d8209ea7e3e8353e73ebce1531991ec9519c74
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811656"
---
# <a name="modules-and-snap-ins"></a>模块和管理单元

Cmdlet 可以使用模块（由 Windows PowerShell 2.0 引入）或管理单元添加到会话中。将 cmdlet 添加到会话后，它可以通过主机应用程序以编程方式运行，或在命令行中以编程方式运行。

出于以下原因，建议使用模块作为向会话添加 cmdlet 的传递方法：

- 模块允许通过加载定义 cmdlet 的程序集来添加 cmdlet。 无需实现管理单元类。

- 模块允许添加其他资源，例如变量、函数、脚本、类型和格式设置文件等。

- 管理单元只能用于向会话添加 cmdlet 和提供程序。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](writing-a-windows-powershell-module.md)

[编写 Windows PowerShell Cmdlet](../cmdlet/cmdlet-overview.md)
