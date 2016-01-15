---
description: na
keywords: na
title: Administering Azure Rights Management by Using Windows PowerShell
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
---
# Spr&#225;va Azure Rights Management pomoc&#237; prostřed&#237; Windows PowerShell
I když můžete aktivovat Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) pomocí [!INCLUDE[o365_2](../Token/o365_2_md.md)] centra pro správu nebo na portálu Azure klasické můžete také použít modul Windows PowerShell pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (službou AADRM), chcete-li to provést.

Po aktivaci [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], další správy pro službu nemusí být požadována. Některé scénáře pokročilé konfigurace však mohou vyžadovat můžete použít modul Windows PowerShell pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. V následující tabulce jsou uvedeny některé scénáře pokročilé konfigurace, které pomocí prostředí Windows PowerShell. Úplný seznam dostupných rutiny s dalšími informacemi o každé z nich, naleznete v části [Azure Rights Management rutin](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Pokud potřebujete nainstalovat modul prostředí Windows PowerShell pro [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], naleznete v části [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Je také doplňkové modul prostředí Windows PowerShell, **RMSProtection**, který podporuje Azure RMS a AD RMS. Tento modul podporuje ochranu a odebrání ochrany z více souborů, takže například můžete hromadně chránit všechny soubory ve složce. Další informace naleznete v tématu [Možnosti skriptování pro tito uživatelé](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md#BKMK_RMSProtectionModule) v oddílu [Konfigurace tito uživatelé pro Azure Rights Management a zjišťování služeb nebo obnovení dat](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md) tématu.

|Pokud potřebujete...|.. použijte následující rutiny|
|------------------------|----------------------------------|
|Migrovat z místní Rights Management (služby AD RMS nebo Microsoft RMS) do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Import AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|K připojení nebo odpojení od [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] služby pro vaši organizaci.|[Připojit AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Odpojení AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Generovat a spravovat vlastní klienta klíč – vyřazení scénáři klíč (BYOK).|[Přidat AadrmKey](http://msdn.microsoft.com/library/azure/dn629418.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Aktivace nebo deaktivace [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] služby pro vaši organizaci.|[Povolit službou Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Zakázat službou Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Zakázání nebo povolení sledování lokality pro Azure Rights Management dokumentů.|[Zakázat AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Povolit AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Konfiguraci ovládacích prvků registrace dvoufázové nasazení nástroje Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Sada AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Vytvářet a spravovat šablony zásad práv pro vaši organizaci.|[Přidat AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Export AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Import AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[Nové AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Odebrat AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Sada AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Nakonfigurujte maximální počet dní, které jsou přístupné obsah, který chrání vaše organizace bez připojení k Internetu (období platnosti licence použití).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Sada AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Spravovat funkci superuživatele [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] pro vaši organizaci.|[Povolit AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Zakázat AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Přidat AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Odebrat AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629405.aspx)|
|Spravovat uživatele a skupiny, kteří mají oprávnění ke správě [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] služby pro vaši organizaci.|[Přidat AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Odebrat AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Získat protokol [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] úlohy správy pro vaši organizaci.|[Get-AadrmAdminLog](http://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Odhlaste se a analýza využití protokolování pro [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Povolit AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629421.aspx)<br /><br />[Get-AadrmUsageLog](http://msdn.microsoft.com/library/azure/dn629401.aspx)<br /><br />[Get-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629425.aspx)<br /><br />[Get-AadrmUsageLogLastCounterValue](http://msdn.microsoft.com/library/azure/dn629423.aspx)<br /><br />[Get-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629419.aspx)<br /><br />[Sada AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629426.aspx)<br /><br />[Zakázat AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629404.aspx)|
|Zobrazit aktuální [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] Konfigurace služby pro vaši organizaci.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Migrovat organizaci z [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] do místního nasazení služby AD RMS.|[Sada AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

## Viz také
[Azure Rights Management](../Topic/Azure_Rights_Management.md)

