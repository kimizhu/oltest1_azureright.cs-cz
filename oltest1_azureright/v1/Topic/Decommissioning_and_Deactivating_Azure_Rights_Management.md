---
description: na
keywords: na
title: Decommissioning and Deactivating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
---
# Vyřazov&#225;n&#237; z provozu a deaktivace Azure Rights Management
Jsou vždy v ovládacím prvku o tom, zda vaše organizace chrání obsah pomocí [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), a pokud se rozhodnete, že již, které chcete použít toto řešení ochrany informací, máte ujištění, že nebude uzamčena mimo obsah, který byl dříve chráněn. Pokud nepotřebujete nepřetržitý přístup k dříve chráněný obsah, můžete jednoduše deaktivovat a necháte platnost vašeho předplatného Azure Rights Management. To by být například vhodné pro při dokončení testování [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] před nasazením v provozním prostředí.

Nicméně pokud jste nasadili [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] v produkčním prostředí, ujistěte se, že máte kopii klíče klienta Azure Rights Management před deaktivovat službu a to provést, než vyprší platnost vašeho předplatného, protože tím bude zajištěno, že můžete zachovat přístup k obsahu, který byl chráněn Azure Rights Management po služba je deaktivována. Pokud jste použili přenést vlastní klíče řešení (BYOK) kde generovat a spravovat vlastní klíče v modul hardwarového zabezpečení, budou již klíč klienta Azure Rights Management. Ale pokud byla spravováno společností Microsoft (výchozí), postupujte podle pokynů pro export klíč klienta v [Operace pro klíč klienta Azure Rights Management](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md) tématu.

> [!TIP]
> I když vyprší platnost vašeho předplatného, váš klient Azure Rights Management zůstává k dispozici pro využívání obsahu po delší dobu. Můžete je však již moci exportovat klíč klienta.

Když máte klíč klienta Azure Rights Management, můžete nasadit Rights Management na místní (služby AD RMS) a importujte klíč klienta jako důvěryhodné domény publikování (důvěryhodné domény publikování). Pak máte následující možnosti pro vyřazení z provozu Azure Rights Management nasazení:

|Pokud to platí pro vás...|… postupujte takto:|
|-----------------------------|-----------------------|
|Aby všichni uživatelé pokračovat v používání Rights Management, ale použít místní řešení spíše než pomocí → Azure RMS|Použití [Set AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) rutiny přímé stávajících uživatelů pro místní nasazení při spotřebování obsahu chráněného po této změně. Instalace služby AD RMS budou uživatelé používat automaticky využívají chráněný obsah.<br /><br />Uživatelé využívat obsah, který byl chráněn před provedením této změny, vaše klienti přesměrovat na místní nasazení pomocí **LicensingRedirection** klíč registru pro Office 2016 nebo Office 2013, jak je popsáno v [služby zjišťování části](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) v poznámkách k nasazení klienta služby RMS a **LicenseServerRedirection** klíč registru pro systém Office 2010, jak je popsáno v [nastavení registru Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Chcete zastavit pomocí technologií Rights Management zcela →|Udělit oprávnění správce k určené [super uživatelská práva](https://technet.microsoft.com/library/mt147272.aspx) a poskytněte tato osoba [nástroj ochranu RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />Tohoto správce pak můžete použít nástroj k hromadné dešifrování souborů ve složkách, které byly chráněné službou Azure Rights Management, tak, aby soubory vrátit k nezůstaly a lze je číst proto bez technologie Rights Management, jako je například Azure RMS nebo AD RMS. Tento nástroj lze použít s Azure RMS a AD RMS, takže budete mít možnost, dešifrování souborů před nebo po deaktivovat Azure RMS nebo jejich kombinaci.|
|Nejste schopni identifikovat všechny soubory, které byly chráněné službou Azure RMS, nebo chcete, aby všichni uživatelé mohli automaticky číst všechny chráněné soubory, které byly neprovedených →|Nasadit nastavení registru na všech klientských počítačů pomocí **LicensingRedirection** klíče registru pro Office 2016 a Office 2013, jak je popsáno v [služby zjišťování části](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) v poznámkách k nasazení klienta služby RMS a **LicenseServerRedirection** klíč registru pro systém Office 2010, jak je popsáno v [nastavení registru Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Také nasadit další nastavení registru uživatelům zabránit v ochraně nové soubory nastavením **DisableCreation** k **1**, jak je popsáno v [nastavení registru Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Chcete, aby služba řízené, ruční obnovení pro všechny soubory, které byly zmeškaných →|Udělení označené uživatele ve skupině pro obnovení dat [super uživatelská práva](https://technet.microsoft.com/library/mt147272.aspx) a přiřaďte jim [nástroj ochranu RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256) tak, aby se odemknout soubory na žádost uživatele se standardním oprávněním.<br /><br />Na všech počítačích, nasadit nastavení uživatelům zabránit v ochraně nové soubory nastavením registru **DisableCreation** na **1**, jak je popsáno v [nastavení registru Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
Další informace o procedurách v této tabulce najdete následující prostředky:

-   Informace o AD RMS a odkazy na nasazení naleznete v tématu [Přehled Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx).

-   Pokyny k importu klíč klienta Azure RMS jako soubor důvěryhodné domény publikování naleznete v tématu [Přidat důvěryhodné domény publikování](https://technet.microsoft.com/library/cc771460.aspx).

-   Instalace modulu prostředí Windows PowerShell pro službu Azure RMS, chcete-li nastavit adresu URL migrace naleznete v části [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Jakmile budete připraveni deaktivovat službu Azure RMS pro vaši organizaci, použijte následující pokyny.

## Deaktivaci služby Rights Management
Použijte jednu z následujících postupů deaktivovat [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Můžete také použít rutiny prostředí Windows PowerShell, [Zakázat službou Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), chcete-li deaktivovat [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Chcete-li deaktivovat službu Rights Management z centra pro správu služeb Office 365

1.  [Přihlásit k odběru Office 365 pomocí pracovní nebo školní účet](https://portal.office.com/) který je správcem nasazení služeb Office 365.

2.  Pokud nejsou Centru správy Office 365 automaticky zobrazeny, vyberte ikonu Spouštěč aplikace v levém horním a zvolte **Admin**.**Admin** dlaždice se zobrazí pouze pro správce služeb Office 365.

    > [!TIP]
    > Nápovědu admin center najdete v tématu [centra pro správu Office 365 - správce nápovědy](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  V levém podokně rozbalte položku **Nastavení služby**.

4.  Klikněte na tlačítko **Rights Management**.

5.  Na **RIGHTS MANAGEMENT** klikněte na tlačítko **Spravovat**.

6.  Na **služby rights management** klikněte na tlačítko **deaktivovat**.

7.  Po zobrazení výzvy **Chcete deaktivovat službu Rights Management?**, klikněte na tlačítko **deaktivovat**.

Nyní byste měli vidět **Rights Management není aktivována** a možnost aktivovat.

#### Chcete-li deaktivovat z portálu Azure Rights Management

1.  Přihlaste se k [portálu Azure klasické](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  V levém podokně klikněte na tlačítko **služby ACTIVE DIRECTORY**.

3.  Z **služby active directory** klikněte na tlačítko **RIGHTS MANAGEMENT**.

4.  Vyberte adresář pro správu pro [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], klikněte na tlačítko **DEAKTIVUJTE**, a pak akci potvrďte.

**Stav správy práv** by nyní měl zobrazovat **neaktivní** a **DEAKTIVUJTE** je nahrazena možnost **Aktivovat**.

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

