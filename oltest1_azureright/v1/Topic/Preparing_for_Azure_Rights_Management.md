---
description: na
keywords: na
title: Preparing for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
---
# Př&#237;prava na Azure Rights Management
Poté, co jste se přihlásili k předplatnému cloudu a navázat vaší organizace pomocí účtu pro [!INCLUDE[o365_1](../Token/o365_1_md.md)] nebo Azure Active Directory, jste připraveni povolit [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] služby.

Však předtím, než tak učiníte, ujistěte se, že níže jsou na místě:

-   Uživatelských účtů a skupin v cloudu, který vytvoříte ručně nebo která jsou automaticky vytvořen a synchronizovat ze služby Active Directory Domain Services (AD DS).

    Při synchronizaci místní účty a skupiny, je třeba synchronizovat všechny atributy. Seznam atributů, které mají být synchronizovány pro Azure RMS naleznete v tématu to [Azure RMS oddílu](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/) z dokumentace rozhraní Azure Active Directory. Pro usnadnění nasazení, doporučujeme použít [Azure AD připojit](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) připojit vašeho místního adresáře s Azure Active Directory, ale můžete použít jakoukoli metodu synchronizace adresáře, která je možné dosáhnout stejného výsledku.

-   Poštovní skupiny v cloudu, který budete používat s Rights Management. Ty mohou být předdefinované skupiny nebo ručně vytvořené skupiny, které obsahují uživatelů, kteří budou používat službu Rights Management.

    Pokud máte systému Exchange Online, můžete vytvořit a používat poštovní skupiny pomocí Centrum pro správu systému Exchange. Pokud jste služby AD DS a synchronizují do Azure AD, můžete vytvořit a používat poštovní skupiny, které jsou skupiny zabezpečení nebo distribučních skupin.

## Povolit službu Rights Management
Ve výchozím nastavení [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] je zakázána, když si zaregistrujte své [!INCLUDE[o365_2](../Token/o365_2_md.md)] nebo účet Azure AD. Chcete-li povolit [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] pro vaši organizaci, je nutné aktivovat službu. Další informace naleznete v tématu [Aktivace Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

