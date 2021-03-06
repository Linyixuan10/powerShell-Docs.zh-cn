---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Package 资源
ms.openlocfilehash: ff2eae712b4117da9bca915f52e18caed7c4885d
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559924"
---
# <a name="dsc-package-resource"></a>DSC Package 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **Package** 资源提供了在目标节点上安装或卸载程序包（如 Windows Installer 和 setup.exe 程序包）的机制。

## <a name="syntax"></a>语法

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>属性

|properties |说明 |
|---|---|
|名称 |指示要确保其特定状态的程序包的名称。 |
|路径 |指示程序包所在的路径。 |
|ProductId |指示唯一标识程序包的产品 ID。 |
|参数 |列出按照原样传输到程序包的参数字符串。 |
|凭据 |提供远程源上程序包的访问权限。 此属性不用于安装程序包。 程序包始终安装在本地系统上。 |
|LogPath |指示你希望提供程序用于保存安装或卸载程序包的日志文件的完整路径。 |
|ReturnCode |指示预期的返回代码。 如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。 |

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示程序包是否已安装。 将此属性设置为 **Absent** 可确保未安装包（如果已安装，则卸载包）。 将其设置为 **Present** 可确保已安装包。 默认值为 **Present**。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

此示例将运行位于指定路径且具有指定产品 ID 的 .msi 安装程序。

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```
