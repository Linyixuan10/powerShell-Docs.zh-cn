---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 使用熟悉的命令名称
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809423"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="53858-103">使用熟悉的命令名称</span><span class="sxs-lookup"><span data-stu-id="53858-103">Using familiar command names</span></span>

<span data-ttu-id="53858-104">PowerShell 支持别名以通过备用名称引用命令。</span><span class="sxs-lookup"><span data-stu-id="53858-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="53858-105">别名允许具有其他 Shell 经验的用户使用其已知的常见命令名称在 PowerShell 中执行类似操作。</span><span class="sxs-lookup"><span data-stu-id="53858-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="53858-106">别名将新名称与其他命令关联。</span><span class="sxs-lookup"><span data-stu-id="53858-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="53858-107">例如，PowerShell 具有名为 `Clear-Host` 的内部函数，该函数清空输出窗口。</span><span class="sxs-lookup"><span data-stu-id="53858-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="53858-108">可以在命令提示符下键入 `cls` 或 `clear` 别名。</span><span class="sxs-lookup"><span data-stu-id="53858-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="53858-109">PowerShell 解释这些别名并运行 `Clear-Host` 函数。</span><span class="sxs-lookup"><span data-stu-id="53858-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="53858-110">此功能可帮助用户了解 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="53858-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="53858-111">首先，大多数 cmd.exe  和 Unix 用户都要使用大量命令，用户通过名称已经了解这些命令。</span><span class="sxs-lookup"><span data-stu-id="53858-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="53858-112">PowerShell 等效项可能不会产生相同的结果。</span><span class="sxs-lookup"><span data-stu-id="53858-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="53858-113">但是，结果非常接近，用户可以在不知道 PowerShell 命令名称的情况下完成工作。</span><span class="sxs-lookup"><span data-stu-id="53858-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="53858-114">学习新的命令 shell 时，“手指记忆”是另一个令人沮丧的主要原因。</span><span class="sxs-lookup"><span data-stu-id="53858-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="53858-115">如果你已使用 cmd.exe  多年，则可能会条件反射地键入 `cls` 命令来清除屏幕。</span><span class="sxs-lookup"><span data-stu-id="53858-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="53858-116">如果没有 `Clear-Host` 的别名，则会收到一条错误消息，并且不知道如何操作才能清除输出。</span><span class="sxs-lookup"><span data-stu-id="53858-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="53858-117">以下列表显示可在 PowerShell 中使用的常见 cmd.exe  和 UNIX 命令：</span><span class="sxs-lookup"><span data-stu-id="53858-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="53858-118">cat</span><span class="sxs-lookup"><span data-stu-id="53858-118">cat</span></span>|<span data-ttu-id="53858-119">dir</span><span class="sxs-lookup"><span data-stu-id="53858-119">dir</span></span>|<span data-ttu-id="53858-120">mount</span><span class="sxs-lookup"><span data-stu-id="53858-120">mount</span></span>|<span data-ttu-id="53858-121">rm</span><span class="sxs-lookup"><span data-stu-id="53858-121">rm</span></span>|
|<span data-ttu-id="53858-122">CD</span><span class="sxs-lookup"><span data-stu-id="53858-122">cd</span></span>|<span data-ttu-id="53858-123">echo</span><span class="sxs-lookup"><span data-stu-id="53858-123">echo</span></span>|<span data-ttu-id="53858-124">移动</span><span class="sxs-lookup"><span data-stu-id="53858-124">move</span></span>|<span data-ttu-id="53858-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="53858-125">rmdir</span></span>|
|<span data-ttu-id="53858-126">chdir</span><span class="sxs-lookup"><span data-stu-id="53858-126">chdir</span></span>|<span data-ttu-id="53858-127">erase</span><span class="sxs-lookup"><span data-stu-id="53858-127">erase</span></span>|<span data-ttu-id="53858-128">popd</span><span class="sxs-lookup"><span data-stu-id="53858-128">popd</span></span>|<span data-ttu-id="53858-129">sleep</span><span class="sxs-lookup"><span data-stu-id="53858-129">sleep</span></span>|
|<span data-ttu-id="53858-130">clear</span><span class="sxs-lookup"><span data-stu-id="53858-130">clear</span></span>|<span data-ttu-id="53858-131">h</span><span class="sxs-lookup"><span data-stu-id="53858-131">h</span></span>|<span data-ttu-id="53858-132">ps</span><span class="sxs-lookup"><span data-stu-id="53858-132">ps</span></span>|<span data-ttu-id="53858-133">sort</span><span class="sxs-lookup"><span data-stu-id="53858-133">sort</span></span>|
|<span data-ttu-id="53858-134">cls</span><span class="sxs-lookup"><span data-stu-id="53858-134">cls</span></span>|<span data-ttu-id="53858-135">history</span><span class="sxs-lookup"><span data-stu-id="53858-135">history</span></span>|<span data-ttu-id="53858-136">pushd</span><span class="sxs-lookup"><span data-stu-id="53858-136">pushd</span></span>|<span data-ttu-id="53858-137">tee</span><span class="sxs-lookup"><span data-stu-id="53858-137">tee</span></span>|
|<span data-ttu-id="53858-138">copy</span><span class="sxs-lookup"><span data-stu-id="53858-138">copy</span></span>|<span data-ttu-id="53858-139">kill</span><span class="sxs-lookup"><span data-stu-id="53858-139">kill</span></span>|<span data-ttu-id="53858-140">pwd</span><span class="sxs-lookup"><span data-stu-id="53858-140">pwd</span></span>|<span data-ttu-id="53858-141">type</span><span class="sxs-lookup"><span data-stu-id="53858-141">type</span></span>|
|<span data-ttu-id="53858-142">del</span><span class="sxs-lookup"><span data-stu-id="53858-142">del</span></span>|<span data-ttu-id="53858-143">lp</span><span class="sxs-lookup"><span data-stu-id="53858-143">lp</span></span>|<span data-ttu-id="53858-144">r</span><span class="sxs-lookup"><span data-stu-id="53858-144">r</span></span>|<span data-ttu-id="53858-145">写入</span><span class="sxs-lookup"><span data-stu-id="53858-145">write</span></span>|
|<span data-ttu-id="53858-146">diff</span><span class="sxs-lookup"><span data-stu-id="53858-146">diff</span></span>|<span data-ttu-id="53858-147">ls</span><span class="sxs-lookup"><span data-stu-id="53858-147">ls</span></span>|<span data-ttu-id="53858-148">ren</span><span class="sxs-lookup"><span data-stu-id="53858-148">ren</span></span>||

<span data-ttu-id="53858-149">`Get-Alias` cmdlet 显示与别名关联的本机 PowerShell 命令的真实名称。</span><span class="sxs-lookup"><span data-stu-id="53858-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="53858-150">解释标准别名</span><span class="sxs-lookup"><span data-stu-id="53858-150">Interpreting standard aliases</span></span>

<span data-ttu-id="53858-151">我们之前描述的别名时为了实现与其他命令 shell 的名称兼容性而设计的。</span><span class="sxs-lookup"><span data-stu-id="53858-151">The aliases we described previously were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="53858-152">PowerShell 中内置的大多数别名都是为了实现简洁性而设计的。</span><span class="sxs-lookup"><span data-stu-id="53858-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="53858-153">较短的名称更容易键入，但如果你不知道它们所指的是什么，则难以理解。</span><span class="sxs-lookup"><span data-stu-id="53858-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="53858-154">PowerShell 别名尝试兼顾清晰度和简洁性。</span><span class="sxs-lookup"><span data-stu-id="53858-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="53858-155">PowerShell 为常见名词和谓词使用一组标准的别名。</span><span class="sxs-lookup"><span data-stu-id="53858-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="53858-156">示例缩写：</span><span class="sxs-lookup"><span data-stu-id="53858-156">Example abbreviations:</span></span>

| <span data-ttu-id="53858-157">名词或谓词</span><span class="sxs-lookup"><span data-stu-id="53858-157">Noun or Verb</span></span> | <span data-ttu-id="53858-158">缩写</span><span class="sxs-lookup"><span data-stu-id="53858-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="53858-159">获取</span><span class="sxs-lookup"><span data-stu-id="53858-159">Get</span></span>          | <span data-ttu-id="53858-160">g</span><span class="sxs-lookup"><span data-stu-id="53858-160">g</span></span>            |
| <span data-ttu-id="53858-161">Set</span><span class="sxs-lookup"><span data-stu-id="53858-161">Set</span></span>          | <span data-ttu-id="53858-162">s</span><span class="sxs-lookup"><span data-stu-id="53858-162">s</span></span>            |
| <span data-ttu-id="53858-163">Item</span><span class="sxs-lookup"><span data-stu-id="53858-163">Item</span></span>         | <span data-ttu-id="53858-164">i</span><span class="sxs-lookup"><span data-stu-id="53858-164">i</span></span>            |
| <span data-ttu-id="53858-165">位置</span><span class="sxs-lookup"><span data-stu-id="53858-165">Location</span></span>     | <span data-ttu-id="53858-166">l</span><span class="sxs-lookup"><span data-stu-id="53858-166">l</span></span>            |
| <span data-ttu-id="53858-167">Command</span><span class="sxs-lookup"><span data-stu-id="53858-167">Command</span></span>      | <span data-ttu-id="53858-168">cm</span><span class="sxs-lookup"><span data-stu-id="53858-168">cm</span></span>           |
| <span data-ttu-id="53858-169">Alias</span><span class="sxs-lookup"><span data-stu-id="53858-169">Alias</span></span>        | <span data-ttu-id="53858-170">al</span><span class="sxs-lookup"><span data-stu-id="53858-170">al</span></span>           |

<span data-ttu-id="53858-171">了解简写名称后，这些别名是可以理解的。</span><span class="sxs-lookup"><span data-stu-id="53858-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="53858-172">Cmdlet 名称</span><span class="sxs-lookup"><span data-stu-id="53858-172">Cmdlet name</span></span>    | <span data-ttu-id="53858-173">Alias</span><span class="sxs-lookup"><span data-stu-id="53858-173">Alias</span></span> |
|----------------|-------|
| `Get-Item`     | <span data-ttu-id="53858-174">gi</span><span class="sxs-lookup"><span data-stu-id="53858-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="53858-175">si</span><span class="sxs-lookup"><span data-stu-id="53858-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="53858-176">gl</span><span class="sxs-lookup"><span data-stu-id="53858-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="53858-177">sl</span><span class="sxs-lookup"><span data-stu-id="53858-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="53858-178">gcm</span><span class="sxs-lookup"><span data-stu-id="53858-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="53858-179">gal</span><span class="sxs-lookup"><span data-stu-id="53858-179">gal</span></span>   |

<span data-ttu-id="53858-180">熟悉 PowerShell 别名后，就很容易猜到 sal  别名指的是 `Set-Alias`。</span><span class="sxs-lookup"><span data-stu-id="53858-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="53858-181">创建新别名</span><span class="sxs-lookup"><span data-stu-id="53858-181">Creating new aliases</span></span>

<span data-ttu-id="53858-182">可以使用 `Set-Alias` cmdlet 创建自己的别名。</span><span class="sxs-lookup"><span data-stu-id="53858-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="53858-183">例如，以下语句创建之前讨论的标准 cmdlet 别名：</span><span class="sxs-lookup"><span data-stu-id="53858-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="53858-184">在内部，PowerShell 会在启动过程中使用类似的命令，但这些别名不可更改。</span><span class="sxs-lookup"><span data-stu-id="53858-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="53858-185">如果尝试执行其中一个命令，你将收到一个错误，该错误说明别名无法进行修改。</span><span class="sxs-lookup"><span data-stu-id="53858-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="53858-186">例如：</span><span class="sxs-lookup"><span data-stu-id="53858-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
