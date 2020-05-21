---
title: AccessDBProviderSample02 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf9351e-157f-4d48-8b8f-1fd64855b682
caps.latest.revision: 10
ms.openlocfilehash: d86148d54535822f00d3d752b509be690c0e4ff2
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690883"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="cd13d-102">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="cd13d-102">AccessDBProviderSample02</span></span>

<span data-ttu-id="cd13d-103">此示例演示如何覆盖[Newdrive \* 和 Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) [\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支持对 `New-PSDrive` 和 cmdlet 的调用的情况下出现的情况，请重写。 `Remove-PSDrive`</span><span class="sxs-lookup"><span data-stu-id="cd13d-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="cd13d-104">此示例中的提供程序类派生自[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="cd13d-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cd13d-105">演示</span><span class="sxs-lookup"><span data-stu-id="cd13d-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd13d-106">提供程序类最有可能派生自以下类之一，并可能实现其他提供程序接口：</span><span class="sxs-lookup"><span data-stu-id="cd13d-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="cd13d-107">" [Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="cd13d-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="cd13d-108">请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="cd13d-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="cd13d-109">" [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="cd13d-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="cd13d-110">请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="cd13d-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="cd13d-111">" [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="cd13d-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="cd13d-112">请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="cd13d-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="cd13d-113">有关根据提供程序功能选择要从哪个提供程序类派生的详细信息，请参阅[设计你的 Windows PowerShell 提供程序](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cd13d-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="cd13d-114">此示例对下列内容进行了说明：</span><span class="sxs-lookup"><span data-stu-id="cd13d-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="cd13d-115">声明 `CmdletProvider` 特性。</span><span class="sxs-lookup"><span data-stu-id="cd13d-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="cd13d-116">定义从[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类中驱动的提供程序类。</span><span class="sxs-lookup"><span data-stu-id="cd13d-116">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="cd13d-117">覆盖[Drivecmdletprovider. Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，以支持创建新驱动器。</span><span class="sxs-lookup"><span data-stu-id="cd13d-117">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="cd13d-118">（此示例不显示如何将动态参数添加到 `New-PSDrive` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="cd13d-118">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="cd13d-119">覆盖[Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支持删除现有驱动器。</span><span class="sxs-lookup"><span data-stu-id="cd13d-119">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="cd13d-120">示例</span><span class="sxs-lookup"><span data-stu-id="cd13d-120">Example</span></span>

<span data-ttu-id="cd13d-121">此示例演示如何重写 Drivecmdletprovider \* 和[Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[Drivecmdletprovider.. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法的操作方式。</span><span class="sxs-lookup"><span data-stu-id="cd13d-121">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="cd13d-122">对于此示例提供程序，创建驱动器时，其连接信息存储在对象中 `AccessDBPsDriveInfo` 。</span><span class="sxs-lookup"><span data-stu-id="cd13d-122">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  /// <summary>
  /// This sample implements a Windows PowerShell provider class
  /// that acts upon an Access database.
  /// </summary>
  /// <remarks>
  /// This example demonstrates only the drive overrides used to
  /// add and remove drives from the database.</remarks>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {
    #region Drive Manipulation

    /// <summary>
    /// The Windows PowerShell engine calls this method when the
    /// New-PSDrive cmdlet is run and the path to this provider is
    /// specified. This method creates a connection to the database
    /// file and sets the Connection property of the PSDriveInfo object.
    /// </summary>
    /// <param name="drive">
    /// Information describing the drive to create.
    /// </param>
    /// <returns>An accessDBPSDriveInfo object that represents
    /// the new drive.</returns>
    protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    } // End NewDrive.

    /// <summary>
    /// The Windows PowerShell engine calls this method when the
    /// Remove-PSDrive cmdlet is run and the path to this provider is
    /// specified. This method closes the ODBC connection of the drive.
    /// </summary>
    /// <param name="drive">The drive to remove.</param>
    /// <returns>An accessDBPSDriveInfo object that represents
    /// the removed drive.</returns>
    protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    } // End RemoveDrive.

    #endregion Drive Manipulation
  } // End AccessDBProvider class.

  #endregion AccessDBProvider

  #region AccessDBPSDriveInfo

  /// <summary>
  /// Any state associated with the drive is held here. In this
  /// case, the state information is the connection to the database.
  /// </summary>
  internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  } // End AccessDBPSDriveInfo class.

  #endregion AccessDBPSDriveInfo
}
```

## <a name="see-also"></a><span data-ttu-id="cd13d-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd13d-123">See Also</span></span>

[<span data-ttu-id="cd13d-124">"Itemcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="cd13d-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="cd13d-125">"Containercmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="cd13d-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="cd13d-126">"Navigationcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="cd13d-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="cd13d-127">设计 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="cd13d-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
