---
title: 创建 Management OData Web 服务 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: f903c99300a34c0dfbed598738e96142588d69d9
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691492"
---
# <a name="creating-a-management-odata-web-service"></a>创建管理 OData Web 服务

管理 ODATA IIS 扩展是一个基础结构，用于创建 ASP.NET web 服务终结点，该终结点公开作为 OData Web 服务实体的 Windows PowerShell cmdlet 和脚本访问的管理数据。 它通过处理 OData 请求并将其转换为 Windows PowerShell 调用来实现此功能。 产品团队可以在此基础结构的基础上构建，以创建用于公开特定管理数据集的终结点。

下载并安装[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例。 按照说明部署 web 服务。 此 web 服务通过创建、读取、更新和删除（CRUD）操作公开服务和进程。 向 web 服务发出的 CRUD 请求调用执行所请求操作的 Windows PowerShell 命令。 CRUD 操作与基础 Windows PowerShell 命令之间的映射是通过两个架构文件（架构）和 schema 来实现的。 架构的 mof 文件使用[分布式管理任务组](https://www.dmtf.org/)（DMTF）托管对象（mof）标准。 架构 .xml 文件使用[资源映射架构](./resource-mapping-schema.md)中描述的 xml 架构。

> [!IMPORTANT]
> 在 Windows Server 2008 R2 SP1 上启用管理 ODATA IIS 扩展之前，必须启用以下功能。
>
> 1. IIS-Iis-webserverrole was-windowsactivationservice
> 2. IIS-WebServer
> 3. IIS-HttpTracing
> 4. IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>创建管理 OData web 服务的步骤

以下主题介绍了如何创建和部署管理 OData web 服务。

- [向管理 OData Web 服务添加资源](./adding-resources-to-a-management-odata-web-service.md)

- [实现管理 OData Web 服务的自定义授权](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [实现管理 OData Web 服务的会话配置](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [创作管理 OData Web 服务的 MOF 架构文件](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [创作管理 OData Web 服务的 XML 架构文件](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [创作管理 OData Web 服务的 Web.config 架构文件](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [部署管理 OData Web 服务](./deploying-a-management-odata-web-service.md)

- [关联管理 OData 实体](./associating-management-odata-entities.md)

## <a name="see-also"></a>另请参阅

[管理 ODATA IIS 扩展架构文件](./management-odata-iis-extension-schema-files.md)
