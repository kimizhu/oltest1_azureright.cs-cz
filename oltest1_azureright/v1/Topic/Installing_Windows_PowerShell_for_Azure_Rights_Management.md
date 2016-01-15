---
description: na
keywords: na
title: Installing Windows PowerShell for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
---
# Instalace prostřed&#237; Windows PowerShell pro službu Azure Rights Management
Následující informace použijte k pomoci při instalaci prostředí Windows PowerShell pro aplikaci Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

Tento modul prostředí Windows PowerShell slouží ke správě [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] z příkazového řádku s použitím libovolného počítače, který má připojení k Internetu a který splňuje požadavky uvedené v následující části. Prostředí Windows PowerShell pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] podporuje skripty pro automatizaci nebo může být nutné pro scénáře pokročilé konfigurace. Další informace o úlohy správy a konfigurace, které modul podporuje naleznete v tématu [Správa Azure Rights Management pomocí prostředí Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Požadované součásti
V této tabulce jsou uvedeny požadavky na instalaci a použití prostředí Windows PowerShell pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Požadavek|Další informace|
|-------------|-------------------|
|Verze systému Windows, který podporuje [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] modulu správy|V seznamu podporovaných operačních systémů v **požadavky na systém** část [stránce stažení pro nástroj pro správu Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Minimální verze prostředí Windows PowerShell: 2.0|Podpora [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] modulu správy je představen v prostředí Windows PowerShell 2.0.<br /><br />Ve výchozím nastavení většina operačních systémů Windows nainstalovat s alespoň verze 2.0 prostředí Windows PowerShell. Pokud potřebujete k instalaci prostředí Windows PowerShell 2.0, naleznete v části [instalaci prostředí Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx). **Tip:** Můžete ověřit verzi prostředí Windows PowerShell, na kterých běží tak, že napíšete **$PSVersionTable** v relaci prostředí Windows PowerShell.|
|Minimální verze rozhraní Microsoft .NET Framework: 4.5 **Tip:** Tato verze rozhraní Microsoft .NET Framework je součástí novějších operačních systémech, takže by měla pouze třeba ručně nainstalovat Pokud váš operační systém klienta je menší než Windows 8.0 nebo operačního systému serveru je nižší než Windows Server 2012.|Pokud již není nainstalováno, můžete stáhnout [rozhraní Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Je vyžadována pro některý ze třídy této verze rozhraní Microsoft .NET Framework, [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] Správa modul používá.|
|Přihlášení asistent 7.0 služeb Microsoft Online Services|Společnost Microsoft Online Services přihlášení pomocníka, je nutné [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] ověřování.<br /><br />Další informace naleznete v tématu [Stažení softwaru: Služeb Microsoft Online Services Pomocníka pro IT specialisty RTW](http://www.microsoft.com/en-us/download/details.aspx?id=41950).|

## Postup instalace modulu správy Rights Management

1.  Přejděte na Microsoft Download Center a [Stažení nástroje pro správu Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721), která obsahuje [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] modulu správy pro prostředí Windows PowerShell.

2.  Z místní složky, kde stáhnout a uložit [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] instalační soubor, poklepejte na spustitelný soubor, který jste stáhli pro danou platformu (WindowsAzureADRightsManagementAdministration_x64 nebo WindowsAzureADRightsManagementAdministration_x86.exe) ke spuštění Azure AD Rights Management Správa Průvodce instalací.

3.  Dokončete průvodce.

Prostředí Windows PowerShell pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] je nyní nainstalován.

## Další kroky
Rutiny, které jsou k dispozici, spusťte prostředí Windows PowerShell s **Spustit jako správce** možnost a zadejte následující příkaz:

```
Get-Command -Module aadrm
```
Použití `the Get-Help <cmdlet_name>` příkaz, který má v nápovědě pro konkrétní rutiny.

Další informace:

-   Úplný seznam rutin, které jsou k dispozici: [Rutiny Azure práva pro správu](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Seznam scénáře hlavní konfigurace, které podporují prostředí Windows PowerShell: [Správa Azure Rights Management pomocí prostředí Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Před spuštěním všechny příkazy, které slouží ke konfiguraci [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] služby, je nutné připojit ke službě s použitím [Připojit AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) rutiny. Po dokončení spuštění příkazů konfigurace, které chcete odpojit od služby pomocí [odpojení AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) rutiny.

> [!NOTE]
> Pokud jste ještě neaktivovali [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], lze provést po připojení ke službě, s použitím [Enable-službou Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) rutiny.

## Viz také
[Správa Azure Rights Management pomocí prostředí Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

