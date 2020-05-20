---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 启动 Windows PowerShell 2.0 引擎
ms.openlocfilehash: 824077008d2dcfd707e977d2112f0882d07a8aca
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030444"
---
# <a name="starting-the-windows-powershell-20-engine"></a><span data-ttu-id="454d8-103">启动 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="454d8-103">Starting the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="454d8-104">本部分介绍如何在包含 Windows PowerShell 2.0 引擎 的 Windows 8.1、Windows Server 2012 R2、Windows 8 和 Windows Server 2012 上，以及安装了 Windows PowerShell 2.0、Windows PowerShell 3.0 和 Windows PowerShell 4.0 的其他系统上启动 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="454d8-104">This section explains how to start the Windows PowerShell 2.0 Engine on Windows 8.1, Windows Server 2012 R2, Windows 8, and Windows Server 2012, which include the Windows PowerShell 2.0 Engine, and on other systems on which Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 are installed.</span></span>

<span data-ttu-id="454d8-105">Windows PowerShell 4.0 和 Windows PowerShell 3.0 旨在能够与 Windows PowerShell 2.0 向后兼容。</span><span class="sxs-lookup"><span data-stu-id="454d8-105">Windows PowerShell 4.0 and Windows PowerShell 3.0 are designed to be backwards compatible with Windows PowerShell 2.0.</span></span> <span data-ttu-id="454d8-106">为 Windows PowerShell 2.0 编写的 Cmdlet、提供程序、管理单元、模块以及脚本无需更改，即可在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中运行。</span><span class="sxs-lookup"><span data-stu-id="454d8-106">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in Windows PowerShell 4.0 and Windows PowerShell 3.0.</span></span> <span data-ttu-id="454d8-107">但是，由于 Microsoft.NET framework 4 中的运行时激活策略的更改，如果使用 CLR 4.0 编译的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 中未进行修改，为 Windows PowerShell 2.0 编写并使用公共语言运行时 (CLR) 2.0 编译的 Windows PowerShell 主机程序将无法运行。</span><span class="sxs-lookup"><span data-stu-id="454d8-107">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in Windows PowerShell 3.0 or Windows PowerShell 4.0, which are compiled with CLR 4.0.</span></span> <span data-ttu-id="454d8-108">Windows PowerShell 2.0 引擎仅在当前脚本或主机程序无法运行时使用，因为它与 Windows PowerShell 4.0、Windows PowerShell 3.0 或 Microsoft .NET Framework 4 不兼容。</span><span class="sxs-lookup"><span data-stu-id="454d8-108">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 4.0, Windows PowerShell 3.0, or Microsoft .NET Framework 4.</span></span> <span data-ttu-id="454d8-109">这种情况很少见。</span><span class="sxs-lookup"><span data-stu-id="454d8-109">Such cases are expected to be rare.</span></span>

<span data-ttu-id="454d8-110">许多需要 Windows PowerShell 2.0 引擎的程序将自动启动。</span><span class="sxs-lookup"><span data-stu-id="454d8-110">Many programs that require the Windows PowerShell 2.0 Engine start it automatically.</span></span> <span data-ttu-id="454d8-111">这些说明适用于极少数需要手动启动该引擎的情况。</span><span class="sxs-lookup"><span data-stu-id="454d8-111">These instructions are included for the rare situations in which you need to start the engine manually.</span></span>

## <a name="installing-and-enabling-required-programs"></a><span data-ttu-id="454d8-112">安装和启用必需程序</span><span class="sxs-lookup"><span data-stu-id="454d8-112">Installing and Enabling Required Programs</span></span>

<span data-ttu-id="454d8-113">启动 Windows PowerShell 2.0 引擎之前，请先启用 Windows PowerShell 2.0 引擎和具有 Service Pack 1 的 Microsoft.NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="454d8-113">Before starting the Windows PowerShell 2.0 Engine, enable the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 with Service Pack 1.</span></span> <span data-ttu-id="454d8-114">有关说明，请参阅[安装 Windows PowerShell](../install/Installing-Windows-PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="454d8-114">For instructions, see [Installing Windows PowerShell](../install/Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="454d8-115">安装了 Windows Management Framework 4.0 或 Windows Management Framework 3.0 的系统上具备所有必需组件。</span><span class="sxs-lookup"><span data-stu-id="454d8-115">Systems on which Windows Management Framework 4.0 or Windows Management Framework 3.0 are installed have all of the required components.</span></span> <span data-ttu-id="454d8-116">无需进行任何其他配置。</span><span class="sxs-lookup"><span data-stu-id="454d8-116">No further configuration is necessary.</span></span> <span data-ttu-id="454d8-117">有关安装 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) 或 Windows Management Framework 3.0 的信息，请参阅[安装 Windows PowerShell](../install/Installing-Windows-PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="454d8-117">For information about installing [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) or Windows Management Framework 3.0, see [Installing Windows PowerShell](../install/Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-the-windows-powershell-20-engine"></a><span data-ttu-id="454d8-118">如何启动 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="454d8-118">How to start the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="454d8-119">启动 Windows PowerShell 时，默认启动最新版本。</span><span class="sxs-lookup"><span data-stu-id="454d8-119">When you start Windows PowerShell the newest version starts by default.</span></span> <span data-ttu-id="454d8-120">若要使用 Windows PowerShell 2.0 引擎启动 Windows PowerShell，请使用 PowerShell.exe 的版本参数。</span><span class="sxs-lookup"><span data-stu-id="454d8-120">To start Windows PowerShell with the Windows PowerShell 2.0 Engine, use the Version parameter of PowerShell.exe.</span></span> <span data-ttu-id="454d8-121">你可以在任何命令提示符（包括 Windows PowerShell 和 Cmd.exe）处运行该命令。</span><span class="sxs-lookup"><span data-stu-id="454d8-121">You can run the command at any command prompt, including Windows PowerShell and Cmd.exe.</span></span>

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a><span data-ttu-id="454d8-122">如何使用 Windows PowerShell 2.0 引擎启动远程会话</span><span class="sxs-lookup"><span data-stu-id="454d8-122">How to start a remote session with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="454d8-123">若要在远程会话中运行 Windows PowerShell 2.0 引擎，请在加载 Windows PowerShell 2.0 引擎的远程计算机上创建会话配置（也称为“终结点”）。</span><span class="sxs-lookup"><span data-stu-id="454d8-123">To run the Windows PowerShell 2.0 Engine in a remote session, create a session configuration (also known as an "endpoint") on the remote computer that loads the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="454d8-124">会话配置保存在远程计算机上，并且任何已获得授权的用户都可以将其用于创建使用 Windows PowerShell 2.0 引擎的会话。</span><span class="sxs-lookup"><span data-stu-id="454d8-124">The session configuration is saved on the remote computer and can be used by any authorized user to create sessions that use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="454d8-125">这是一项高级任务，通常由系统管理员执行。</span><span class="sxs-lookup"><span data-stu-id="454d8-125">This is an advanced task that is typically performed by a system administrator.</span></span>

<span data-ttu-id="454d8-126">以下过程使用 [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet 的 **PSVersion** 参数来创建使用 Windows PowerShell 2.0 引擎的会话配置。</span><span class="sxs-lookup"><span data-stu-id="454d8-126">The following procedure uses the **PSVersion** parameter of the [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet to create a session configuration that uses the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="454d8-127">你还可以使用 [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet 的 **PowerShellVersion** 参数为加载 Windows PowerShell 2.0 引擎的会话创建会话配置文件，此外，你可以使用 [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) 参数的 **PSVersion** 参数将会话配置更改为使用 Windows PowerShell 2.0 引擎。</span><span class="sxs-lookup"><span data-stu-id="454d8-127">You can also use the **PowerShellVersion** parameter of the [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet to create a session configuration file for a session that loads the Windows PowerShell 2.0 Engine and you can use the **PSVersion** parameter of the [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parameter to change a session configuration to use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="454d8-128">有关会话配置文件的详细信息，请参阅 [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8)。有关会话配置（包括安装和安全性）的信息，请参阅 [about_Session_Configurations[v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab)。</span><span class="sxs-lookup"><span data-stu-id="454d8-128">For more information about session configuration files, see [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8).For information about session configurations, including setup and security, see [about_Session_Configurations[v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).</span></span>

#### <a name="to-start-a-remote-windows-powershell-20-session"></a><span data-ttu-id="454d8-129">启动远程 Windows PowerShell 2.0 会话</span><span class="sxs-lookup"><span data-stu-id="454d8-129">To start a remote Windows PowerShell 2.0 session</span></span>

1. <span data-ttu-id="454d8-130">若要创建需要 Windows PowerShell 2.0 引擎的会话配置，请使用 [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet 的 **PSVersion** 参数，其值为“2.0”。</span><span class="sxs-lookup"><span data-stu-id="454d8-130">To create a session configuration that requires the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet with a value of "2.0".</span></span> <span data-ttu-id="454d8-131">在计算机上的连接的“服务器端”或接收端运行此命令。</span><span class="sxs-lookup"><span data-stu-id="454d8-131">Run this command on the computer at the "server side" or receiving end of the connection.</span></span>

   <span data-ttu-id="454d8-132">下面的示例命令在 Server01 计算机上创建 PS2 会话配置。</span><span class="sxs-lookup"><span data-stu-id="454d8-132">The following sample command creates the PS2 session configuration on the Server01 computer.</span></span> <span data-ttu-id="454d8-133">若要运行此命令，请使用 **“以管理员身份运行”** 选项启动 Windows PowerShell 4.0 或 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="454d8-133">To run this command, start Windows PowerShell 4.0 or Windows PowerShell 3.0 with the **Run as administrator** option.</span></span>

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. <span data-ttu-id="454d8-134">若要在使用 PS2 会话配置的 Server01 计算机上创建会话，请使用创建远程会话的 cmdlet（例如 [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet）的 **ConfigurationName** 参数。</span><span class="sxs-lookup"><span data-stu-id="454d8-134">To create a session on the Server01 computer that uses the PS2 session configuration, use the **ConfigurationName** parameter of cmdlets that create a remote session, such as the [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet.</span></span>

   <span data-ttu-id="454d8-135">使用会话配置的会话启动时，Windows PowerShell 2.0 引擎会自动加载到该会话中。</span><span class="sxs-lookup"><span data-stu-id="454d8-135">When a session that uses the session configuration starts, the Windows PowerShell 2.0 Engine is automatically loaded into the session.</span></span>

   <span data-ttu-id="454d8-136">下面的命令在使用 PS2 会话配置的 Server01 计算机上启动一个会话。</span><span class="sxs-lookup"><span data-stu-id="454d8-136">The following command starts a session on the Server01 computer that uses the PS2 session configuration.</span></span> <span data-ttu-id="454d8-137">该命令将该会话保存在 $s 变量中。</span><span class="sxs-lookup"><span data-stu-id="454d8-137">The command saves the session in the $s variable.</span></span>

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a><span data-ttu-id="454d8-138">如何使用 Windows PowerShell 2.0 引擎启动后台作业</span><span class="sxs-lookup"><span data-stu-id="454d8-138">How to start a background job with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="454d8-139">若要使用 Windows PowerShell 2.0 引擎启动后台作业，请使用 [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet 的**PSVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="454d8-139">To start a background job with the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet.</span></span>

<span data-ttu-id="454d8-140">下面的命令使用 Windows PowerShell 2.0 引擎启动后台作业</span><span class="sxs-lookup"><span data-stu-id="454d8-140">The following command starts a background job with the Windows PowerShell 2.0 Engine</span></span>

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

<span data-ttu-id="454d8-141">有关后台作业的详细信息，请参阅 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。</span><span class="sxs-lookup"><span data-stu-id="454d8-141">For more information about background jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>
