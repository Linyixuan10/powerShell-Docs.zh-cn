---
title: 使用 Windows PowerShell 脚本创建工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: cc613240e056e8443b075019cbff6dd15da3716f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557442"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="05b1f-102">使用 Windows PowerShell 脚本创建工作流</span><span class="sxs-lookup"><span data-stu-id="05b1f-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="05b1f-103">可以通过编写 Windows PowerShell 脚本来创建工作流。</span><span class="sxs-lookup"><span data-stu-id="05b1f-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="05b1f-104">若要创建工作流，请在脚本正文前使用工作流关键字，后跟工作流的名称。</span><span class="sxs-lookup"><span data-stu-id="05b1f-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="05b1f-105">例如：</span><span class="sxs-lookup"><span data-stu-id="05b1f-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="05b1f-106">查找工作流的方式与处理任何其他 Windows PowerShell 命令的方式相同。</span><span class="sxs-lookup"><span data-stu-id="05b1f-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="05b1f-107">实现并行和序列</span><span class="sxs-lookup"><span data-stu-id="05b1f-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="05b1f-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90))支持并行执行活动。</span><span class="sxs-lookup"><span data-stu-id="05b1f-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) supports execution of activities in parallel.</span></span> <span data-ttu-id="05b1f-109">若要在 Windows PowerShell 脚本中实现此功能，请 `parallel` 在脚本块前面使用关键字。</span><span class="sxs-lookup"><span data-stu-id="05b1f-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="05b1f-110">还可以使用 `foreach -parallel` 构造并行循环访问对象的集合。</span><span class="sxs-lookup"><span data-stu-id="05b1f-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="05b1f-111">若要按顺序在并行块中按顺序执行一组活动，请将该活动组括在脚本块中，并在块前面加上 sequence 关键字。</span><span class="sxs-lookup"><span data-stu-id="05b1f-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="05b1f-112">将计算机加入域</span><span class="sxs-lookup"><span data-stu-id="05b1f-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="05b1f-113">下面的脚本创建一个工作流，该工作流检查一组用户指定的计算机的域状态，将它们加入域（如果尚未加入域），然后再次检查状态。</span><span class="sxs-lookup"><span data-stu-id="05b1f-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>
<span data-ttu-id="05b1f-114">这是在[使用 Windows PowerShell 活动创建工作流](./creating-a-workflow-with-windows-powershell-activities.md)中说明的 XAML 工作流的脚本版本。</span><span class="sxs-lookup"><span data-stu-id="05b1f-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```
