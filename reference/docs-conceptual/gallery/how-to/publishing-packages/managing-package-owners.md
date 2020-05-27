---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 管理包所有者
ms.openlocfilehash: 72a3ff72818c5461c74d46de5689e2d6c59b19bf
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564663"
---
# <a name="managing-package-owners"></a><span data-ttu-id="8b1bc-103">管理包所有者</span><span class="sxs-lookup"><span data-stu-id="8b1bc-103">Managing package owners</span></span>

<span data-ttu-id="8b1bc-104">由将包发布到库的用户来定义 PowerShell 库中包的所有权。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="8b1bc-105">有时需要在初始包发布之外管理此元数据，这意味着所有者元数据需要是可变的，而包本身不需要。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="8b1bc-106">所有包所有者都是对等的。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-106">All package owners are peers.</span></span>
<span data-ttu-id="8b1bc-107">这意味着任何包所有者都可发布包的新版本。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="8b1bc-108">这还意味着任何包所有者都可以删除任何其他包所有者。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="8b1bc-109">每个所有者的权利相同。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="8b1bc-110">设置包的初始所有者</span><span class="sxs-lookup"><span data-stu-id="8b1bc-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="8b1bc-111">当新包发布到 PowerShell 库时，由发布包的用户定义初始所有者。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="8b1bc-112">这根据 Publish-Module cmdlet 中使用谁的 API 密钥决定。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="8b1bc-113">添加所有者</span><span class="sxs-lookup"><span data-stu-id="8b1bc-113">Adding Owners</span></span>

<span data-ttu-id="8b1bc-114">将包发布到 PowerShell 库后，可轻松邀请其他用户成为包的所有者。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="8b1bc-115">使用包的当前所有者的帐户[登录](https://powershellgallery.com/users/account/LogOn) PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="8b1bc-116">通过使用“项”选项卡、搜索或单击你的用户名，然后单击[ **“管理我的包”** ](https://www.powershellgallery.com/account/Packages)，导航到包页面。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="8b1bc-117">以包的所有者身份登录时，左侧有“管理所有者”链接可以单击。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="8b1bc-118">输入要添加为所有者的人员的用户名，并单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="8b1bc-119">随后将向新的共同所有者发送一封电子邮件，作为成为包的所有者的邀请。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="8b1bc-120">该用户单击此链接后，将成为对包具有完全控制权的完全共同所有者，其控制权包括删除其他用户所有者身份的能力。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="8b1bc-121"> 注意：新的所有者必须先确认所有权，否则不会  列为包的所有者。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="8b1bc-122">查看“管理所有者”  页面时，你将在当前所有者中看到“等待审批”条目。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="8b1bc-123">可以删除该邀请；同样也可以删除其他所有者。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="8b1bc-124">此邀请过程可防止用户错误地将其他用户添加为其包的所有者。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="8b1bc-125">注意：“Authors”元数据是完全自由文本；仅“Owners”受控。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>

## <a name="removing-owners"></a><span data-ttu-id="8b1bc-126">删除所有者</span><span class="sxs-lookup"><span data-stu-id="8b1bc-126">Removing Owners</span></span>

<span data-ttu-id="8b1bc-127">如果包具有多个所有者而需删除其中之一，过程很简单：</span><span class="sxs-lookup"><span data-stu-id="8b1bc-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="8b1bc-128">使用包的当前所有者的帐户[登录](https://powershellgallery.com/users/account/LogOn) PowerShell 库；</span><span class="sxs-lookup"><span data-stu-id="8b1bc-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="8b1bc-129">通过使用“包”选项卡、搜索或单击你的用户名，然后单击[ **“管理我的包”** ](https://www.powershellgallery.com/account/Packages)，导航到包页面。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="8b1bc-130">以包的所有者身份登录时，左侧有“管理所有者”链接可以单击；</span><span class="sxs-lookup"><span data-stu-id="8b1bc-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="8b1bc-131">单击要删除的所有者旁边的“删除”链接。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-131">Click the 'remove' link next to the owner to be removed.</span></span>

## <a name="transferring-package-ownership"></a><span data-ttu-id="8b1bc-132">转移包所有权</span><span class="sxs-lookup"><span data-stu-id="8b1bc-132">Transferring Package Ownership</span></span>

<span data-ttu-id="8b1bc-133">我们有时会收到将包所有权从一个用户转移到另一个用户的支持请求，但你基本上总是可以自己完成该操作。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="8b1bc-134">将所有权从一个用户转移到另一个用户只是以上两种功能的组合。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="8b1bc-135">当前所有者邀请新用户成为共同所有者，新用户接受邀请；</span><span class="sxs-lookup"><span data-stu-id="8b1bc-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="8b1bc-136">新用户将旧用户从所有者列表中删除。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="8b1bc-137">此请求有多种形式，但过程相同。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="8b1bc-138">包所有权从一个开发人员更改为另一个开发人员</span><span class="sxs-lookup"><span data-stu-id="8b1bc-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="8b1bc-139">使用错误帐户意外发布了包</span><span class="sxs-lookup"><span data-stu-id="8b1bc-139">The package was accidentally published using the wrong account</span></span>

## <a name="orphaned-packages"></a><span data-ttu-id="8b1bc-140">孤立的包</span><span class="sxs-lookup"><span data-stu-id="8b1bc-140">Orphaned Packages</span></span>

<span data-ttu-id="8b1bc-141">最后一种情况曾经出现，但次数不多。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="8b1bc-142">包变得孤立，唯一的包所有者帐户不能用于添加新所有者。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="8b1bc-143">以下是本场景的一些示例：</span><span class="sxs-lookup"><span data-stu-id="8b1bc-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="8b1bc-144">所有者帐户与不再存在的电子邮件地址关联，且用户忘记其密码</span><span class="sxs-lookup"><span data-stu-id="8b1bc-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="8b1bc-145">生成包的已注册所有者已离开公司，无法与其联系以更新包所有权</span><span class="sxs-lookup"><span data-stu-id="8b1bc-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="8b1bc-146">由于存在仅影响少量包的 bug，包在库中无所有者</span><span class="sxs-lookup"><span data-stu-id="8b1bc-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="8b1bc-147">PowerShell 库管理员可以访问任何包的“管理所有者”链接。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="8b1bc-148">如果你是包的合法所有者，而无法联系当前所有者以获取所有权，则可以使用库中的“报告滥用行为”链接与 PowerShell 库管理员联系。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="8b1bc-149">然后，我们将按流程验证你对该包的所有权。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="8b1bc-150">如果我们确定你应为该包的所有者，我们将使用该包的“管理所有者”链接，向你发送成为所有者的邀请。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="8b1bc-151">我们将仅在验证你应为所有者后才执行此操作，此过程因具体情况而异。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="8b1bc-152">通常，我们将使用包的项目 URL 设法联系项目所有者，但我们也可能使用 Twitter、电子邮件或其他方式联系项目所有者。</span><span class="sxs-lookup"><span data-stu-id="8b1bc-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
