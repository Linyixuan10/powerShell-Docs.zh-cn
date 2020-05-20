---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSCAutomationHostEnabled 注册表项
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954264"
---
><span data-ttu-id="25d47-103">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="25d47-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="25d47-104">DSCAutomationHostEnabled 注册表项</span><span class="sxs-lookup"><span data-stu-id="25d47-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="25d47-105">DSC 使用 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System 下的 DSCAutomationHostEnabled 注册表项，以便在初始启动时配置计算机。</span><span class="sxs-lookup"><span data-stu-id="25d47-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="25d47-106">DSCAutomationHostEnabled  支持三种模式：</span><span class="sxs-lookup"><span data-stu-id="25d47-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="25d47-107">DSCAutomationHostEnabled 值</span><span class="sxs-lookup"><span data-stu-id="25d47-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="25d47-108">说明</span><span class="sxs-lookup"><span data-stu-id="25d47-108">Description</span></span>   |
|---|---|
<span data-ttu-id="25d47-109">0</span><span class="sxs-lookup"><span data-stu-id="25d47-109">0</span></span> | <span data-ttu-id="25d47-110">禁用对启动状态计算机的配置。</span><span class="sxs-lookup"><span data-stu-id="25d47-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="25d47-111">1</span><span class="sxs-lookup"><span data-stu-id="25d47-111">1</span></span> | <span data-ttu-id="25d47-112">启用对启动状态计算机的配置。</span><span class="sxs-lookup"><span data-stu-id="25d47-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="25d47-113">2</span><span class="sxs-lookup"><span data-stu-id="25d47-113">2</span></span> | <span data-ttu-id="25d47-114">仅在 DSC 处于挂起或当前状态时，启用对计算机的配置。</span><span class="sxs-lookup"><span data-stu-id="25d47-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="25d47-115">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="25d47-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="25d47-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25d47-116">See Also</span></span>

<span data-ttu-id="25d47-117">有关如何使用此功能在初始启动时运行配置的示例，请参阅[初始启动时使用 DSC 配置虚拟机](bootstrapDsc.md)。</span><span class="sxs-lookup"><span data-stu-id="25d47-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
