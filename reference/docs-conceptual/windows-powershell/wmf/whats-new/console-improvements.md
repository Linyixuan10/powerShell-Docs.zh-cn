---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: WMF 5.1 中的控制台改进
ms.openlocfilehash: ae3d08a34a09bc32d40a8a45788999ee9c54a562
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808983"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="3d877-103">WMF 5.1 中的控制台改进</span><span class="sxs-lookup"><span data-stu-id="3d877-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="3d877-104">PowerShell 控制台改进</span><span class="sxs-lookup"><span data-stu-id="3d877-104">PowerShell console improvements</span></span>

<span data-ttu-id="3d877-105">在 WMF 5.1 中对 powershell.exe 进行了以下更改以改进控制台体验：</span><span class="sxs-lookup"><span data-stu-id="3d877-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="3d877-106">VT100 支持</span><span class="sxs-lookup"><span data-stu-id="3d877-106">VT100 support</span></span>

<span data-ttu-id="3d877-107">Windows 10 添加了对 [VT100 转义序列](/windows/console/console-virtual-terminal-sequences)的支持。</span><span class="sxs-lookup"><span data-stu-id="3d877-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="3d877-108">计算表宽度时，PowerShell 会忽略某些 VT100 格式设置转义序列。</span><span class="sxs-lookup"><span data-stu-id="3d877-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="3d877-109">PowerShell 还添加了一个新 API，它可以在格式设置代码中用于确定是否支持 VT100。</span><span class="sxs-lookup"><span data-stu-id="3d877-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="3d877-110">例如：</span><span class="sxs-lookup"><span data-stu-id="3d877-110">For example:</span></span>

```powershell
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```

<span data-ttu-id="3d877-111">下面是一个完整[示例](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7)，可用于突出显示来自 `Select-String` 的匹配项。</span><span class="sxs-lookup"><span data-stu-id="3d877-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="3d877-112">将该示例保存在名为 `MatchInfo.format.ps1xml` 的文件中，随后若要在配置文件或其他位置使用它，请运行 `Update-FormatData -Prepend MatchInfo.format.ps1xml`。</span><span class="sxs-lookup"><span data-stu-id="3d877-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="3d877-113">请注意，VT100 转义序列仅从 Windows 10 Aniversary 更新开始受支持。</span><span class="sxs-lookup"><span data-stu-id="3d877-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="3d877-114">它们在早期系统上不受支持。</span><span class="sxs-lookup"><span data-stu-id="3d877-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="3d877-115">PSReadline 中的 Vi 模式支持</span><span class="sxs-lookup"><span data-stu-id="3d877-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="3d877-116">[PSReadline](https://github.com/PowerShell/PSReadLine) 添加了对 vi 模式的支持。</span><span class="sxs-lookup"><span data-stu-id="3d877-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="3d877-117">若要使用 vi 模式，请运行 `Set-PSReadlineOption -EditMode Vi`。</span><span class="sxs-lookup"><span data-stu-id="3d877-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="3d877-118">带交互式输入的重定向 stdin</span><span class="sxs-lookup"><span data-stu-id="3d877-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="3d877-119">在早期版本中，重定向 stdin 以及你要以交互方式输入命令时，需要使用 `powershell -File -` 启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3d877-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="3d877-120">使用 WMF 5.1，不再需要如此困难地发现选项。</span><span class="sxs-lookup"><span data-stu-id="3d877-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="3d877-121">你可以在不使用任何选项的情况下启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3d877-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="3d877-122">请注意，PSReadline 不支持重定向 stdin，使用重定向 stdin 的内置命令行编辑体验极其有限，例如箭头键不起作用。</span><span class="sxs-lookup"><span data-stu-id="3d877-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="3d877-123">PSReadline 的未来版本应该会解决此问题。</span><span class="sxs-lookup"><span data-stu-id="3d877-123">A future release of PSReadline should address this issue.</span></span>
