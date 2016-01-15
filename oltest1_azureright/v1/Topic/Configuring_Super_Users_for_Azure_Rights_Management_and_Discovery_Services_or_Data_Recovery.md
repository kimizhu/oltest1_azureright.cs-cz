---
description: na
keywords: na
title: Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
---
# Konfigurace tito uživatel&#233; pro Azure Rights Management a zjišťov&#225;n&#237; služeb nebo obnoven&#237; dat
Funkci superuživatel společnosti Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) zajišťuje, že autorizované osoby a služby mohou vždy číst a zkontrolovat data, která chrání Azure RMS pro vaši organizaci. A v případě potřeby odebrat ochranu nebo změnit na ochranu, která již byla použita. Superuživatel má vždy úplná vlastnická práva na všechny licence udělená klienta služby RMS organizace. Tato možnost se někdy nazývá "důvody nad daty" a je zásadním prvkem zachovat kontrolu dat vaší organizace. Můžete například použijete tuto funkci pro žádné z následujících situacích:

-   Zaměstnanec opustí organizace a je třeba číst soubory, které jsou chráněny.

-   Odeberte aktuální zásady ochrany, který byl nakonfigurován pro soubory a použijte nové zásady ochrany musí správce IT.

-   Exchange Server je třeba index poštovní schránky pro operace hledání.

-   Máte existující IT služby řešení prevence (DLP) ztrátu dat, šifrování obsahu brány (CEG) a ochrany proti malwaru produkty, které je nutné zkontrolovat soubory, které jsou již chráněny.

-   Je třeba hromadně dešifrovat soubory pro auditování, právní nebo jiné důvody kompatibility.

Ve výchozím nastavení není povolena funkce superuživatel a žádní uživatelé jsou přiřazeny této role. Pokud nakonfigurujete konektor Rights Management for Exchange, a to není vyžadováno pro standardní služby se systémem Exchange Online, SharePoint Online nebo serveru SharePoint Server je pro vás povolen automaticky.

Pokud je nutné ručně povolit funkci superuživatel, použijte rutinu prostředí Windows PowerShell [Povolení AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx), a potom přiřadit uživatelé (nebo účty služby), podle potřeby s použitím [Přidat AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx) rutiny. Jeden nebo více tito uživatelé mohou mít pro vaši organizaci, ale je nutné přidat jednotlivé uživatele; skupiny nejsou podporovány.

> [!NOTE]
> Pokud jste ještě nenainstalovali modul prostředí Windows PowerShell pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], naleznete v části [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Doporučené postupy zabezpečení pro funkci superuživatel:

-   Omezení a sledování správci, komu jsou přiřazeny globálního správce vašeho klienta služeb Office 365 ani Azure RMS nebo komu jsou přiřazeny GlobalAdministrator role pomocí [Přidat AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) rutiny. Tito uživatelé mohou povolit funkci superuživatel a přiřadit uživatele (a sami) jako tito uživatelé a potenciálně dešifrovat všechny soubory, které chrání vaše organizace.

-   Chcete-li zjistit, kteří uživatelé a účty služby jsou přiřazeny jako tito uživatelé, použijte [Rutina Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx).  Všechny akce správy, jako je povolení nebo zakázání funkce super a přidávání ani odebírání tito uživatelé jsou zaznamenána a ověřovány pomocí [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) příkazu. Když tito uživatelé dešifrovat soubory, tato akce zaznamenána do protokolu a lze audit s [protokolování využití](https://technet.microsoft.com/library/dn529121.aspx).

-   Pokud není nutné provést funkci superuživatel pro každodenní služby, povolit funkci pouze v případě, že je třeba jej a znovu ji vypnout pomocí [Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx) rutiny.

Následující extrakce protokolu ukazuje některé položky příklad z pomocí rutiny Get-AadrmAdminLog. V tomto příkladu správce pro Contoso Ltd potvrdí, že funkci superuživatel je zakázána, přidá Richard Simone jako superuživatel, ověří, zda pouze superuživatel nakonfigurované pro Azure RMS Richard a pak povolí tuto funkci superuživatel tak, aby Richard lze nyní dešifrování některé soubory, které nebyly chráněny zaměstnanci, který nyní opustil společnost.

`2015-08-01T18:58:20	admin@contoso.com	GetSuperUserFeatureState	Passed	Disabled`
`2015-08-01T18:59:44	admin@contoso.com	AddSuperUser -id rsimone@contoso.com	Passed	True`
`2015-08-01T19:00:51	admin@contoso.com	GetSuperUser	Passed	rsimone@contoso.com`
`2015-08-01T19:01:45	admin@contoso.com	SetSuperUserFeatureState -state Enabled	Passed	True`

## <a name="BKMK_RMSProtectionModule"></a>Možnosti skriptování pro tito uživatelé
Často, někdo, kterému je přiřazena superuživatel pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] bude nutné odebrat ochranu z více souborů, na více místech. I když je možné provést ručně, je efektivnější (a často vyšší spolehlivost) pro tento skript. Chcete-li to provést, [Stažení nástroje ochrany RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Poté pomocí  [Odemknout RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) rutiny, a [chránit RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx)   rutina podle potřeby.

> [!IMPORTANT]
> Ačkoli nástroj RMS ochrany je určen pro tito uživatelé hromadné odemknout soubory pro účely obnovení, aktuální verzi nástroje pro Azure RMS nepodporuje ověřování uživatelů. Dokud toto omezení nebude vyřešen, musíte použít hlavní účet služby ověření s Azure RMS předtím, než je možné odebrat ochranu ze souborů.  Další informace a pokyny naleznete v tématu [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/azure/mt433202.aspx).

Další informace o tyto rutiny, naleznete v části [RMS ochrany rutiny](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> V modulu RMSProtection prostředí Windows PowerShell, která je dodávána s nástrojem pro ochranu RMS se liší od a doplňuje hlavní [modul prostředí Windows PowerShell pro službu Rights Management Azure](https://technet.microsoft.com/library/jj585027.aspx). Podporuje Azure RMS a služby AD RMS.

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

