---
description: na
keywords: na
title: Azure Rights Management Deployment Roadmap
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
---
# Pl&#225;n nasazen&#237; Azure Rights Management
Pomocí následujících kroků pro přípravu, provádění a správu Azure Rights Management (Azure RMS) pro vaši organizaci.

Nicméně pokud chcete rychle vyzkoušejte Azure RMS pro sebe, spíše než limit vrátit v provozním prostředí, naleznete v části [Rychlé zahájení kurzu Azure Rights Management](../Topic/Quick_Start_Tutorial_for_Azure_Rights_Management.md).

> [!IMPORTANT]
> Než provedete následující kroky, ujistěte se, že jste zkontrolovali [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Krok 1: Potvrďte, že máte předplatné, které obsahuje Azure Rights Management
Existuje více než jeden typ předplatné, které obsahuje [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Podívejte se na téma [Cloud odběry, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) v oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) téma a zkontrolujte, zda vaše předplatné obsahuje funkce, které chcete použít ve vaší organizaci odkazem v tabulce [nabídek porovnání RMS Rights Management Services ()](https://technet.microsoft.com/dn858608).

## Krok 2: Připravit účtu klienta používat službu Rights Management
Než začnete používat [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], proveďte následující přípravu:

1.  Ujistěte se, že vaše Azure nebo Office 365 klienta obsahuje uživatelských účtů a skupin, které budou použity službou Azure RMS k ověřování uživatelů z vaší organizace. V případě potřeby vytvořte těchto účtů a skupin nebo synchronizovat z vašeho místního adresáře. Další informace naleznete v tématu [Příprava na Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

2.  Rozhodněte, zda chcete, aby společnosti Microsoft ke správě vašeho klienta klíče (výchozí), nebo generovat a spravovat své klíč klienta sami (známého pod názvem přenést vlastní klíč nebo BYOK). Všimněte si, že v současné době nelze použít BYOK Pokud použijete systému Exchange Online. Další informace naleznete v tématu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

3.  Nainstalujte modul prostředí Windows PowerShell pro [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] na alespoň jeden počítač, který má přístup k Internetu. Můžete provést tento krok nyní nebo později. Další informace naleznete v tématu [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

4.  Pokud aktuálně používáte místně Rights Management services: Přenesení přesunout klíče, šablony a adresy URL do cloudu. Další informace naleznete v tématu [Migrace ze služby AD RMS na Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

5.  Aktivujte službu Rights Management, takže můžete začít používat službu. Pokud je požadován do několika fází rozdělený nasazení konfigurujte uživatelských ovládacích prvků nově příchozího omezit využití pro konkrétního uživatele. Další informace naleznete v tématu [Aktivace Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

Volitelně lze využít konfigurací následujících možností:

-   Vlastní šablony, je-li šablony zásad práv ve výchozím nastavení nejsou dostatečná pro vaši organizaci. Můžete provést tento krok nyní nebo později. Další informace naleznete v tématu [Konfigurace vlastních šablon pro Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

-   Využití protokolování, takže je možné sledovat, jak vaše organizace používá službu Rights Management. Můžete provést tento krok nyní nebo později. Další informace naleznete v tématu [Protokolování a analýza využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

## Krok 3: Konfigurace aplikace a služby pro službu Rights Management
Konfigurace aplikace může zahrnovat instalaci Rights Management, aplikace pro sdílení a povolení podpory pro informace o rights management (IRM) funkce ve službě SharePoint Online nebo systému Exchange Online. Další informace naleznete v tématu [Konfigurace aplikací pro Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

Pokud máte existující IT služby, které je nutné zkontrolovat soubory, které bude chránit Azure RMS – například data nevracení prevence (DLP) řešení, obsahu šifrování brány (CEG) a ochrany proti malwaru produkty – konfigurace účtů služeb, které se tito uživatelé pro Azure RMS. Další informace naleznete v tématu [Konfigurace tito uživatelé pro Azure Rights Management a zjišťování služeb nebo obnovení dat](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

Pokud máte místní služby, které chcete používat s Azure Rights Management, nainstalujte a nakonfigurujte konektor Rights Management. Další informace naleznete v tématu [Nasazení konektoru Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Krok 4: Publikovat a spotřebovávat obsahu chráněného právy
Můžete začít publikovat a spotřebovávat chráněný obsah a protokolu, jak vaše společnost používá službu Rights Management. Další informace naleznete v tématu [Použití služby Azure Rights Management](../Topic/Using_Azure_Rights_Management.md).

## Krok 5: Podle potřeby spravovat službu Rights Management pro svůj účet klienta
Jak začít používat [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], můžete zjistit, [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] modul pro prostředí Windows PowerShell užitečné pomohou skript nebo automatizovat pro správu změn. Další informace naleznete v tématu [Správa Azure Rights Management pomocí prostředí Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

