---
title: 如何更新帮助文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 35b3fd696419d0135fd6f662223e6c8586df443a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561384"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="01a98-102">如何更新帮助文件</span><span class="sxs-lookup"><span data-stu-id="01a98-102">How to Update Help Files</span></span>

<span data-ttu-id="01a98-103">本主题说明如何为支持可更新帮助的模块更新帮助文件。</span><span class="sxs-lookup"><span data-stu-id="01a98-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="01a98-104">正在更新帮助文件</span><span class="sxs-lookup"><span data-stu-id="01a98-104">Updating Help Files</span></span>

<span data-ttu-id="01a98-105">更新帮助文件的原因有很多，例如，纠正错误、阐明概念、回答经常询问的问题、添加新文件，或者添加更好的更好的示例。</span><span class="sxs-lookup"><span data-stu-id="01a98-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="01a98-106">更新帮助文件：</span><span class="sxs-lookup"><span data-stu-id="01a98-106">To update a help file:</span></span>

1. <span data-ttu-id="01a98-107">更改文件。</span><span class="sxs-lookup"><span data-stu-id="01a98-107">Change the files.</span></span>

2. <span data-ttu-id="01a98-108">将文件转换为其他 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="01a98-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="01a98-109">收集每个 UI 区域性中的模块的所有帮助文件（新增、更改和未更改）。</span><span class="sxs-lookup"><span data-stu-id="01a98-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="01a98-110">对照 XML 架构验证文件。</span><span class="sxs-lookup"><span data-stu-id="01a98-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="01a98-111">重新生成每个 UI 区域性的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="01a98-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="01a98-112">在 HelpInfo XML 文件中，为每个 UI 区域性递增 CAB 文件的版本号。</span><span class="sxs-lookup"><span data-stu-id="01a98-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="01a98-113">将新的 CAB 文件上传到 HelpInfo XML 文件中的**HelpContentUri**元素的值指定的位置。</span><span class="sxs-lookup"><span data-stu-id="01a98-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="01a98-114">将较旧的 CAB 文件替换为新的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="01a98-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="01a98-115">将更新后的 HelpInfo XML 文件上传到模块清单中的**HelpInfoUri**键指定的位置。</span><span class="sxs-lookup"><span data-stu-id="01a98-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="01a98-116">用新文件替换旧的 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="01a98-116">Replace the older HelpInfo XML file with the new file.</span></span>
