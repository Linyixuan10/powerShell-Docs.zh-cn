---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047054"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c6018-103">MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="c6018-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c6018-104">停止正在进行的配置更改。</span><span class="sxs-lookup"><span data-stu-id="c6018-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6018-105">语法</span><span class="sxs-lookup"><span data-stu-id="c6018-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c6018-106">参数</span><span class="sxs-lookup"><span data-stu-id="c6018-106">Parameters</span></span>

<span data-ttu-id="c6018-107">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="c6018-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c6018-108">返回值</span><span class="sxs-lookup"><span data-stu-id="c6018-108">Return value</span></span>

<span data-ttu-id="c6018-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="c6018-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6018-110">备注</span><span class="sxs-lookup"><span data-stu-id="c6018-110">Remarks</span></span>

<span data-ttu-id="c6018-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="c6018-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c6018-112">要求</span><span class="sxs-lookup"><span data-stu-id="c6018-112">Requirements</span></span>

<span data-ttu-id="c6018-113">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c6018-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c6018-114">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c6018-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c6018-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6018-115">See also</span></span>

[<span data-ttu-id="c6018-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c6018-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)