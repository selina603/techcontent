<properties
    pageTitle="创建 Azure AD 用户帐户| Azure"
    description="本文介绍如何为 Azure 自动化中的 Runbook 创建 Azure AD 用户帐户凭据，以便在 Azure 和经典 Azure 中进行身份验证。"
    services="automation"
    documentationcenter=""
    author="MGoedtel"
    manager="jwhit"
    editor="tysonn"
    keywords="azure active directory 用户, azure 服务管理, azure ad 用户帐户"
    translationtype="Human Translation" />
<tags
    ms.assetid="fcfe266d-b22e-4dfb-8272-adcab09fc0cf"
    ms.service="automation"
    ms.devlang="na"
    ms.topic="get-started-article"
    ms.tgt_pltfrm="na"
    ms.workload="infrastructure-services"
    ms.date="04/13/2017"
    wacn.date="05/02/2017"
    ms.author="magoedte"
    ms.sourcegitcommit="78da854d58905bc82228bcbff1de0fcfbc12d5ac"
    ms.openlocfilehash="35c193e897ad7c441f77d3c1c5bb2c08055ac430"
    ms.lasthandoff="04/22/2017" />

# <a name="authenticate-runbooks-with-azure-classic-deployment-and-resource-manager"></a>使用 Azure 经典部署和 Resource Manager 部署对 Runbook 进行身份验证
本文介绍在为针对 Azure 经典部署模型或 Azure Resource Manager 资源运行的 Azure 自动化 Runbook 配置 Azure AD 用户帐户时所要执行的步骤。  尽管这仍是基于 Azure Resource Manager 的 Runbook 支持的身份验证标识，但建议的方法是使用 Azure 运行方式帐户。       

## <a name="create-a-new-azure-active-directory-user"></a>创建新的 Azure Active Directory 用户
1. 以你要管理的 Azure 订阅的服务管理员身份登录到 Azure 经典管理门户。
2. 选择“Active Directory” ，然后选择组织目录的名称。
3. 选择“用户”选项卡，然后在命令区域中选择“添加用户”。
4. 在“告诉我们有关此用户的信息”页上的“用户类型”下，选择“组织中的新用户”。
5. 输入用户名。  
6. 选择与 Active Directory 页上你的 Azure 订阅关联的目录名。
7. 在“用户配置文件”页上，提供名字和姓氏、用户友好名称，并从“角色”列表中选择用户。  不要**启用多重身份验证**。
8. 记下该用户的完整名称和临时密码。
9. 选择“设置”>“管理员”>“添加”。
10. 键入你创建的用户的完整用户名。
11. 选择希望该用户管理的订阅。
12. 从 Azure 注销，然后使用你刚创建的帐户重新登录。 系统将提示你更改用户密码。

## <a name="create-an-automation-account-in-azure-classic-management-portal"></a>在 Azure 经典管理门户中创建自动化帐户
在本部分中，你将执行以下步骤以在 Azure 经典管理门户中创建一个新的 Azure 自动化帐户，该帐户用于在 Azure 经典部署中管理资源的 Runbook。  

1. 以你要管理的 Azure 订阅的服务管理员身份登录到 Azure 经典管理门户。
2. 选择“自动化” 。
3. 在“自动化”页上，选择“创建自动化帐户”。
4. 在“创建自动化帐户”框中键入新自动化帐户的名称，然后从下拉列表中选择**区域**。  
5. 单击“确定”  接受设置并创建帐户。
6. 创建后，帐户会列在“自动化”  页上。
7. 单击该帐户，转到“仪表板”页。  
8. 在“自动化仪表板”页上，选择“资产” 。
9. 在“资产”页上，选择位于页面底部的“添加设置”。
10. 在“添加设置”页上，选择“添加凭据”。
11. 在“定义凭据”页的“凭据类型”下拉列表中选择“Windows PowerShell 凭据”，并提供凭据名称。
12. 在随后出现的“定义凭据”页上，在“用户名”字段中键入前面创建的 AD 用户帐户的用户名，并在“密码”和“确认密码”字段中键入密码。  单击“确定”以保存你的更改。

## <a name="use-the-credential-in-a-runbook"></a>在 Runbook 中使用凭据
可以使用 [Get-AutomationPSCredential](http://msdn.microsoft.com/zh-cn/library/dn940015.aspx) 活动检索 Runbook 中的凭据，然后将它与 [Add-AzureAccount](http://msdn.microsoft.com/zh-cn/library/azure/dn722528.aspx) 结合使用以连接到 Azure 订阅。 如果该凭据是多个 Azure 订阅的管理员，还应使用 [Select-AzureSubscription](http://msdn.microsoft.com/zh-cn/library/dn495203.aspx) 指定正确的订阅。 下面所示的 Windows PowerShell 通常出现在大多数 Azure 自动化 Runbook 的顶部。

    $cred = Get-AutomationPSCredential -Name "myuseraccount.partner.onmschina.cn"
    Add-AzureAccount -Environment AzureChinaCloud -Credential $cred
    Select-AzureSubscription -SubscriptionName "My Subscription"

应该在 Runbook 中任何 [检查点](http://technet.microsoft.com/zh-cn/library/dn469257.aspx#bk_Checkpoints) 的后面重复这些行。 如果 Runbook 已挂起，然后在另一个工作线程上恢复，则它需要再次执行身份验证。