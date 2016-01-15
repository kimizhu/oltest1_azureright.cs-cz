---
description: na
keywords: na
title: Rights Management sharing application administrator guide
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
---
# Průvodce Rights Management sd&#237;len&#237; aplikace Spr&#225;vce
Následující informace použijte, pokud jste zodpovědní za sdílení aplikace v podnikové síti Microsoft Rights Management, nebo pokud chcete další technické informace, než je v [Průvodce Rights Management sdílení aplikace uživatele](../Topic/Rights_Management_sharing_application_user_guide.md) nebo [Nejčastější dotazy týkající se společnost Microsoft Rights Management sdílení aplikací pro systém Windows](http://go.microsoft.com/fwlink/?LinkId=303971):

-   [Automatické nasazení pro aplikace pro sdílení Microsoft Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ScriptedInstall)

    -   [Probíhá ověření úspěšné instalace](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)

    -   [Odinstalační příkazy](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_uninstallscripted)

    -   [Potlačení prostřednictvím služby Automatické aktualizace](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SuppressAutomaticUpdates)

    -   [Pouze Azure RMS: Konfigurace sledování dokumentu.](#BKMK_DocumentTracking)

    -   [Služby AD RMS pouze: Podpora pro více domén e-mailu v rámci vaší organizace](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains)

-   [Technický přehled pro aplikace pro sdílení Microsoft Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_AdminOverview)

    -   [Úroveň ochrany – nativní a obecný](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection)

    -   [Podporované typy souborů a přípon souborů](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)

    -   [Změna úrovně ochrany výchozí souborů](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)

> [!TIP]
> Pokud jste novou aplikaci sdílení RMS nebo hledáte další informace, podívejte se na téma [jak RMS chrání všechny typy souborů – pomocí aplikace sdílení RMS](https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app).

Aplikace pro sdílení obsahu RMS je nejvhodnější pro práci s Azure RMS, protože tato konfigurace nasazení podporuje odesílání chráněné přílohy uživatelům v jiné organizaci a možnosti, například e-mailová oznámení a sledování s odvolání dokumentů.  Ovšem s určitými omezeními také funguje s místní verzí, služby AD RMS. Komplexní porovnání funkcí, které jsou podporovány Azure RMS a služby AD RMS naleznete v tématu [porovnání Rights Management Azure a služby AD RMS](https://technet.microsoft.com/library/jj739831.aspx). Pokud jste službu AD RMS a chcete přejít na Azure RMS, naleznete v části [migrace ze služby AD RMS na Azure Rights Management](https://technet.microsoft.com/library/dn858447.aspx).

## <a name="BKMK_ScriptedInstall"></a>Automatické nasazení pro aplikace pro sdílení Microsoft Rights Management
Verze systému Windows aplikace sdílení RMS podporuje instalaci typu skriptů, díky čemuž je vhodný pro podnikového nasazení.

Pouze požadavky pro zařízení jsou spuštění počítače s minimální verze aktualizace Service Pack 1 pro systém Windows 7 a zda je nainstalován Microsoft Framework, minimální verze 4.0. Pokud je třeba nainstalovat rozhraní Microsoft .NET Framework 4.0, můžete [ji stáhnout z Microsoft Download Center instalaci](http://www.microsoft.com/download/details.aspx?id=17718).

#### Chcete-li stáhnout žádost o automatického nasazení pro sdílení obsahu RMS

1.  Přejděte do [Microsoft Rights Management aplikace pro Windows pro sdílení](http://www.microsoft.com/download/details.aspx?id=40857) stránky v Microsoft Download Center a klikněte na tlačítko **Stáhnout**.

2.  Vyberte a stahování souborů, které potřebujete. Existují dvě klienta instalačních balíčků: jeden pro Windows 64-bit (Microsoft Rights Management sdílení aplikace x64.zip) a druhou pro systém Windows 32 bitů (Microsoft Rights Management sdílení x86.zip aplikace).

3.  Extrahujte soubory z komprimované instalační balíčky, například poklepáním. Zkopírujte extrahovaných souborů do umístění v síti, může přistupovat klientských počítačů.

Instalační balíčky pro aplikace pro sdílení obsahu RMS podporuje různých scénářů nasazení a obsahuje následující položky:

|Popis|Scénář nasazení|
|---------|-------------------|
|Společnost Microsoft Online Pomocníka pro přihlášení|Požadováno pro následující:<br /><br />-   Systém Office 2010 a Azure RMS<br />-   Office 2013 a Azure RMS, pokud není nainstalován [9. června 2015 aktualizace pro Office 2013](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Oprava hotfix pro systém Office (KB 2596501)|Požadováno pro následující:<br /><br />-   Systém Office 2010 a Azure RMS<br />-   Systém Office 2010 a služby Active Directory RMS|
|Oprava hotfix Chcete-li povolit klienta služby AD RMS 1.0 budete chtít pracovat s Azure RMS (KB 2843630)|Požadováno pro následující:<br /><br />-   Systém Office 2010 a Azure RMS<br />-   Systém Office 2010 a služby Active Directory RMS|
|Klienta služby AD RMS a aplikace pro sdílení obsahu RMS|Požadováno pro následující:<br /><br />-   Office 2016 nebo Office 2013 a Azure RMS nebo RMS služby Active Directory<br />-   Systém Office 2010 a Azure RMS<br />-   Systém Office 2010 a služby Active Directory RMS<br />-   Sdílení aplikací a doplněk Office pouze RMS|
|Doplněk Office pro pás karet|Požadováno pro následující:<br /><br />-   Office 2016 nebo Office 2013 a Azure RMS nebo RMS služby Active Directory<br />-   Systém Office 2010 a Azure RMS<br />-   Systém Office 2010 a služby Active Directory RMS<br />-   Sdílení aplikací a doplněk Office pouze RMS|
|Nástroj pro přípravu Azure Active Directory Rights Management|Požadováno pro následující:<br /><br />-   Systém Office 2010 a Azure RMS|
Chcete-li identifikovat příkazy potřebné k nasazení aplikace pro tyto scénáře nasazení pro sdílení obsahu RMS pomocí následujících postupů:

-   **Office 2016 nebo Office 2013 a Azure RMS nebo RMS služby Active Directory**

    Vaši uživatelé se systémem Office 2016 nebo Office 2013, vaše organizace používá Azure RMS nebo Active Directory RMS a uživatelé spolupracovat s jinými organizacemi, kteří používají Azure RMS nebo Active Directory RMS.

-   **Systém Office 2010 a Azure RMS**

    Vaši uživatelé se systémem Office 2010, vaše organizace používá Azure RMS a uživatelé spolupracovat s jinými organizacemi, kteří používají Azure RMS nebo Active Directory RMS.

-   **Systém Office 2010 a služby Active Directory RMS**

    Vaši uživatelé se systémem Office 2010, vaše organizace používá službu AD RMS a uživatelé spolupracovat s jinými organizacemi, kteří používají Azure RMS.

-   **Sdílení aplikací a doplněk Office pouze RMS**

    Vaši uživatelé se systémem Office 2016, Office 2013 nebo systému Office 2010, vaše organizace používá službu AD RMS a není nutné uživatelé spolupracovat s jinými organizacemi, kteří používají Azure RMS. Tato instalace vám umožní nainstalovat jen sdílení aplikací a doplněk Office.

> [!NOTE]
> V těchto případech Pokud vaše organizace je spuštěna služba AD RMS, vaši uživatelé mohou přijímat chráněný obsah od jiných organizací, kteří používají Azure RMS, ale vaši uživatelé nelze odeslat chráněný obsah uživatelům v organizaci používající Azure RMS. Však pokud vaše organizace běží Azure RMS, vaše uživatelé mohou odesílat a přijímat chráněný obsah od jiných organizací.

K dokončení instalace pro každou proceduru, nutné restartovat počítač. Automatické restartování můžete spustit pomocí příkazu, například vypínání /i.

#### Chcete-li nasadit aplikace pro Office 2016 Office 2013 a Azure RMS nebo Active Directory RMS pro sdílení obsahu RMS

-   V každém počítači, ve kterém chcete nainstalovat aplikaci a související součásti pro sdílení obsahu RMS spusťte se zvýšenými oprávněními následující příkaz:

    ```
    setup.exe /s
    ```

Chcete-li ověřit úspěch, podívejte se na téma [Probíhá ověření úspěšné instalace](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) v tomto tématu.

#### Chcete-li nasadit aplikaci pro systém Office 2010 a Azure RMS pro sdílení obsahu RMS

1.  Musí být globální správce vašeho klienta služby Azure Active Directory nebo Office 365, tak, aby spuštěním nástroj pro přípravu Azure Active Directory Rights Management můžete získat adresu URL organizace certifikační služby. Tento nástroj je nutné spustit pouze jednou v jednom počítači. Adresa URL certifikační služby budete používat při instalaci aplikace v každém počítači pro sdílení obsahu RMS:

    1.  Přihlaste se k počítači pomocí účtu místního správce.

    2.  V tomto počítači [Stáhnout a nainstalovat Microsoft Online v Pomocníkovi pro přihlášení](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Spusťte následující příkaz zobrazíte zobrazené na obrazovce adresa URL certifikační služby, které lze zkopírovat a uložit na další krok:

        -   Pro Windows 8.1 a Windows 8, 64bitová verze:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Pro Windows 8.1 a Windows 8, 32 bitů:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Pro systém Windows 7, 64bitová verze:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Tento příkaz může zobrazit výzvu k zadání pověření pro Azure. Pokud počítač není připojen k doméně, budete vyzváni. Pokud je počítač připojen k doméně, může být tento nástroj moci použít pověření uložená v mezipaměti.

2.  V každém počítači, na který nainstalujete aplikaci sdílení RMS spusťte se zvýšenými oprávněními následující příkaz:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  V každém počítači, na který nainstalujete aplikaci sdílení RMS, musí uživatelé spusťte následující příkaz (nemusí zvýšenými oprávněními). K tomuto účelu včetně pokládání uživatelům spustit příkaz (například na odkaz v e-mailovou zprávu nebo odkaz na portálu oddělení technické podpory nápovědy) různými způsoby nebo ho můžete přidat do jejich přihlašovacího skriptu:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Chcete-li ověřit úspěch, podívejte se na téma [Probíhá ověření úspěšné instalace](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) v tomto tématu.

#### Chcete-li nasadit aplikaci pro systém Office 2010 a Active Directory RMS pro sdílení obsahu RMS

1.  V každém počítači, na který nainstalujete aplikaci sdílení RMS spusťte se zvýšenými oprávněními následující příkaz:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  V každém počítači, na který nainstalujete aplikaci sdílení RMS, musí uživatelé spusťte následující příkaz (nemusí zvýšenými oprávněními). K tomuto účelu včetně pokládání uživatelům spustit příkaz (například na odkaz v e-mailovou zprávu nebo odkaz na portálu oddělení technické podpory nápovědy) různými způsoby nebo ho můžete přidat do jejich přihlašovacího skriptu:

    -   Pro Windows 10, Windows 8.1 a Windows 8, 64bitová verze:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Pro Windows 10, Windows 8.1 a Windows 8, 32 bitů:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Pro systém Windows 7, 64bitová verze:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Chcete-li ověřit úspěch, podívejte se na téma [Probíhá ověření úspěšné instalace](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) v tomto tématu.

#### Chcete-li nainstalovat aplikaci a doplněk Office pouze pro sdílení obsahu RMS

1.  Instalace klienta služby AD RMS a sdílení aplikací pomocí následujícího příkazu:

    -   64bitová verze systému Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Pro 32bitová verze systému Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Příklad: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Nainstalujte doplněk Office pomocí následujících příkazů:

    -   Pro 64bitové verze systému Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Pro 32bitové verze systému Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Příklad: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Chcete-li ověřit úspěch, podívejte se na téma [Probíhá ověření úspěšné instalace](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) v tomto tématu.

### <a name="BKMK_verifyscripted"></a>Probíhá ověření úspěšné instalace
Soubory protokolu instalace slouží k ověření úspěšné instalace.

##### Chcete-li ověřit úspěch instalace pro aplikace pro Office 2016 Office 2013 a Azure RMS nebo Active Directory RMS pro sdílení obsahu RMS

-   Chcete-li ověřte, zda úspěšný příkaz Setup.exe v každém počítači, vyhledejte soubor protokolu instalace **RMInstaller.log** v *%temp%\RMS_installer_ &lt; guid &gt;* složku a potom identifikovat ukončovací kód.

    V případě úspěšné instalace má ukončovací kód s hodnotou 0 a jakékoli jiné číslo označuje selhání instalace.

    Příklad názvu souboru protokolu: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

##### Chcete-li ověřit úspěch instalace pro aplikace pro systém Office 2010 a Azure RMS pro sdílení obsahu RMS

1.  Chcete-li ověřte, zda úspěšný příkaz Setup.exe v každém počítači, vyhledejte soubor protokolu instalace **RMInstaller.log** v *%temp%\RMS_installer_ &lt; guid &gt;* složku a potom identifikovat ukončovací kód.

    V případě úspěšné instalace má ukončovací kód s hodnotou 0 a jakékoli jiné číslo označuje selhání instalace.

    Příklad názvu souboru protokolu: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Chcete-li ověřit úspěch pro příkaz RMSSetup.exe, by měl mít uživatel následující soubory vytvořené v jejich *%localappdata%\microsoft\drm* složky:

    -   CERTIFIKÁTU. počítač 2048.drm

    -   Machine.drm certifikátu.

    -   CLC &#42;.drm

    -   GIKU &#42;.drm

    Příklad CLC &#42;.drm souboru:

    **.Drm CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf; k5b11; k4a10; kac15; k29b2b6980f4c}**

##### Chcete-li ověřit úspěch instalace pro aplikace pro systém Office 2010 a Active Directory RMS pro sdílení obsahu RMS

1.  Chcete-li ověřte, zda úspěšný příkaz Setup.exe v každém počítači, vyhledejte v souboru protokolu instalace *%temp%\RMS_installer_ &lt; guid &gt;* složku a identifikovat ukončovací kód.

    V případě úspěšné instalace má ukončovací kód s hodnotou 0 a jakékoli jiné číslo označuje selhání instalace.

    Příklad názvu souboru protokolu: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Chcete-li ověřte, zda úspěšný příkaz aadrmprep.exe v každém počítači, vyhledejte následující text v souboru protokolu instalace: **aadrmprep.exe byl ukončen s stav úspěch**

    > [!NOTE]
    > V některých případech mohou tuto instalaci spustit dvakrát. první výskyt se nezdaří a druhou je úspěšné.

    Pokud chcete zkontrolovat změny registru, které tento nástroj provádí ručně, že jsou následující:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @= "&lt; certifikační adresa url &gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser = "&lt; default_user &gt;"

##### Chcete-li ověřit úspěch instalace pro aplikaci a doplněk Office pouze pro sdílení obsahu RMS

1.  Chcete-li ověřit úspěch příkaz Setup_ipviewer.exe, vyhledejte následující text v souboru protokolu instalace: **Stav chyby nebo úspěšné instalace: 0**

    Příklad řádky z úspěšné instalace:

    **MSI (s) (F0:B8) [14:19:57:854]: Produkt: Active Directory klient Rights Management Services 2.1 – instalace byla úspěšně dokončena.**

    **MSI (s) (F0:B8) [14:19:57:854]: Instalační služba systému Windows je nainstalován produkt. Název produktu: Služby Active Directory Rights Management Services Client 2.1. Verze produktu: 1.0.1179.1. Jazyk produktu: 1033. Výrobce: Společnost Microsoft Corporation. Stav chyby nebo úspěšné instalace: 0.**

2.  Chcete-li ověřit úspěch doplněk Office, v každém počítači, hledat následující text v souboru protokolu instalace: **Stav chyby nebo úspěšné instalace: 0**

    Příklad řádky z úspěšné instalace:

    **MSI (s) (9C: 88) [18:49:04:007]: Produkt: Aplikace Microsoft Office RMS doplňků--Instalace byla úspěšně dokončena.**

    **MSI (s) (9C: 88) [18:49:04:007]: Instalační služba systému Windows je nainstalován produkt. Název produktu: Doplňky systému Office RMS společnosti Microsoft. Verze produktu: 1.0.7. Jazyk produktu: 1033. Výrobce: Společnost Microsoft. Stav chyby nebo úspěšné instalace: 0.**

### <a name="BKMK_uninstallscripted"></a>Odinstalační příkazy
Příkazy instalace, které jsou požadovány pro tyto nasazení nepodporují příkazu odinstalaci. Klient služby AD RMS a sdílení aplikací můžete odinstalovat a odinstalujete doplněk Office. Pomocí následujících příkazů odinstalace těchto elementů.

##### Chcete-li odinstalovat klienta služby AD RMS a aplikace pro sdílení obsahu RMS

-   Pomocí následujících příkazů:

    -   64bitová verze systému Windows:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Pro 32bitová verze systému Windows:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

##### Chcete-li odinstalovat doplněk Office

-   Pomocí následujících příkazů:

    -   Pro 64bitové verze systému Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Pro 32bitové verze systému Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

### <a name="BKMK_SuppressAutomaticUpdates"></a>Potlačení prostřednictvím služby Automatické aktualizace
Ve výchozím nastavení jsou uživatelé upozornění, pokud existuje novější verze aplikace sdílení RMS a vyzváni, abyste ji stáhnout. Toto oznámení můžete potlačit tím, že následující registru upravit:

1.  Přejděte na **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** a pokud dosud neexistují, vytvořte nový klíč s názvem **RmsSharingApp**.

2.  Vyberte **RmsSharingApp**, vytvořte novou hodnotu DWORD **AllowUpdatePrompt**, a nastavte hodnotu na **0**.

Vzhledem k tomu, že aplikace sdílení RMS není podporována službou WSUS, můžete provádět následující postup můžete otestovat všechny nové verze aplikace před nasazením všem uživatelům aplikace pro sdílení obsahu RMS:

1.  V počítačích všech uživatelů spusťte skript, chcete-li potlačit automatické aktualizace. V počítačích, které správci používat k testování nové verze nespouštějte tento skript.

2.  Pokud je k dispozici nová verze, správci ji stáhnout a otestovat.

3.  Po dokončení testování není a všechny problémy vyřešit, nasazení na nejnovější verzi pro všechny uživatele pomocí automatického nasazení pokyny v tomto průvodci.

### <a name="BKMK_DocumentTracking"></a>Pouze Azure RMS: Konfigurace sledování dokumentu.
Máte-li [odběr, který podporuje sledování dokumentů](https://technet.microsoft.com/en-us/dn858608), sledování dokumentů webu je povolena ve výchozím nastavení pro všechny uživatele ve vaší organizaci.  Sledování dokumentů zobrazuje informace, jako jsou e-mailové adresy uživatelů, kteří se pokusil o přístup k chráněné dokumenty uživatelé sdílet, pokud tyto osoby se pokusil o přístup a jejich umístění. Pokud tyto informace zobrazení je zakázáno ve vaší organizaci vzhledem k požadavkům ochrany osobních údajů, můžete zakázat přístup k dokumentu sledování webu pomocí  [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) rutiny. Můžete je znovu povolit přístup k webu kdykoli, s použitím [Povolení AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037), a můžete zkontrolovat, zda je aktuálně povoleno nebo zakázáno pomocí přístup [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

 Chcete-li spustit tyto rutiny, můžete musí mít alespoň verze **2.3.0.0** modulu Azure RMS pro prostředí Windows PowerShell.  Pokyny k instalaci, naleznete v části [instalaci prostředí Windows PowerShell pro službu Rights Management Azure](https://technet.microsoft.com/library/jj585012.aspx).

> [!TIP]
> Pokud byly dříve staženy a nainstalovány v modulu, zkontrolujte číslo verze spuštěním: `(Get-Module aadrm –ListAvailable).Version`

Následující adresy URL se používají pro sledování dokumentů a musí být povoleno (například, přidejte je do důvěryhodné servery používáte-li aplikaci Internet Explorer se zvýšeným zabezpečením):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > je tato adresa URL pro Bing maps.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="BKMK_FederatedDomains"></a>Služby AD RMS pouze: Podpora pro více domén e-mailu v rámci vaší organizace
Pokud používáte službu AD RMS a uživatele ve vaší organizaci máte více domén e-mailu, pravděpodobně v důsledku fúze nebo získání, je nutné provést následující registru upravit:

1.  Přejděte na **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** a pokud dosud neexistují, vytvořte nový klíč s názvem **RmsSharingApp**.

2.  Vyberte **RmsSharingApp**, vytvořte novou hodnotu Víceřetězcová hodnota s názvem **FederatedDomains**, a pak přidejte domény a všechny subdomény, které vaše organizace používá. Zástupné znaky nejsou podporovány.

    Příklad: Společnost ABC &amp; firma má standardní e-mailová doména **cohovineyardandwinery.com**, ale v důsledku fúze, domény e-mailu také použít **cohowinery.com**, **eastcoast.cohowinery.com**, a **cohovineyard**. Pro **FederatedDomains** správce zadá hodnotu dat: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Pokud neprovedete tato změna v registru, uživatelé nebudou moci spotřebovávat obsah, který je chráněn ostatním uživatelům ve své organizaci. Tato úprava registru není vyžadován, pokud použijete Azure RMS.

## <a name="BKMK_AdminOverview"></a>Technický přehled pro aplikace pro sdílení Microsoft Rights Management
Microsoft Rights Management, aplikace pro sdílení je volitelný ke stažení aplikace pro systém Microsoft Windows a další platformy jsou k dispozici následující:

-   Ochranu k jednomu souboru nebo hromadného ochrany více souborů také všechny soubory v rámci vybrané složky.

-   Plná podpora pro ochranu libovolný typ souboru a integrované prohlížeče pro nejčastěji používané typy souborů textu a obrázků.

-   Obecný ochranu pro soubory, které nepodporují ochranu RMS.

-   Úplnou interakci s soubory chráněné pomocí sady Office informace Rights Management (IRM).

-   Úplnou interakci s ochránit pomocí služby SharePoint, FCI a podporované PDF, nástroje pro vytváření souborů PDF.

Microsoft Rights Management, aplikace pro sdílení využívá novou [klienta služby AD RMS 2.1 runtime](http://www.microsoft.com/download/details.aspx?id=38396). Pomocí funkce služby AD RMS 2.1, Microsoft Rights Management, aplikace pro sdílení poskytuje koncovým uživatelům jednoduché použití ochrany a spotřeby.

S vydáním říjen 2013 RMS můžete nativně chránit dokumenty pomocí systému Office 2010 a poslat lidem v jiné společnosti, který poté můžou pomocí nich pomocí Azure RMS. Kromě toho se této verze při použití služby AD RMS v kryptografických režim 2, můžete použít RMS pro uživatele a spotřebovávat obsah od osob v jiné společnosti, která používá Azure RMS. Další informace o kryptografických režim 2, naleznete v části [AD RMS kryptografických režimy](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

### <a name="BKMK_LevelsofProtection"></a>Úroveň ochrany – nativní a obecný
Microsoft Rights Management aplikace pro sdílení podporuje ochrany ve dvou různých úrovních, jak je uvedeno v následující tabulce.

|Typ ochrany|Nativní|Obecná|
|---------------|-----------|----------|
|Popis|Nativní ochrany pro text, obrázek, aplikace Microsoft Office (Word, Excel, PowerPoint) soubory, soubory PDF a další typy souborů aplikace, které podporují služby AD RMS, poskytuje silné úroveň ochrany, který zahrnuje jak šifrování a vynucení práva (oprávnění).|Obecný ochranu pro všechny ostatní aplikace a typy souborů, poskytuje úroveň ochrany, která obsahuje oba zapouzdření souboru pomocí .pfile typ souboru a ověřování k ověření, pokud je uživatel oprávnění k otevření souboru.|
|Ochrana|Soubory jsou plně zašifrovány a vynucení ochrany z následujících způsobů:<br /><br />-   Předtím, než je vykreslen chráněný obsah, který musí nastat úspěšné ověřování pro uživatele, kteří příjem souborů prostřednictvím e-mailu nebo jsou udělen přístup k němu prostřednictvím souboru nebo sdílené složky oprávnění.<br />-   Navíc práva k používání a zásad nastavených modulem na vlastníka obsahu, když jsou chráněny soubory jsou plně uplatněna při vykreslení obsahu v prohlížeči IP (pro chráněný text a soubory obrázků) nebo k aplikaci (pro všechny ostatní podporované typy souborů).|Ochrana souborů je vynuceno z následujících způsobů:<br /><br />-   Předtím, než je vykreslen chráněný obsah, který úspěšném ověření musí být stejné pro uživatele, kteří jsou oprávnění k otevření souboru a vzhledem k přístupu k němu. Pokud ověření selže, soubor nebude možné otevřít.<br />-   Práva k používání a zásad nastavených modulem na vlastníka obsahu jsou zobrazeny na autorizované uživatele informují o zamýšlené využití zásad.<br />-   Dojde k protokolování auditu autorizovaných uživatelů otevírání a přístupu k souborům, ale žádná práva k používání vynucuje podpora aplikací.|
|Výchozí nastavení pro typy souborů|Toto je výchozí úroveň ochrany pro následující typy souborů:<br /><br />-   Text a soubory obrázků<br />-   Soubory aplikace Microsoft Office (Word, Excel, PowerPoint)<br />-   Formát přenosných dokumentu (PDF)<br /><br />Další informace naleznete v následující části [Podporované typy souborů a přípon souborů](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes).|Toto je výchozí ochrany pro všechny ostatní typy souborů (například .vsdx a ve formátu RTF) není podporován prostřednictvím úplnou ochranu.|
Můžete změnit výchozí úroveň ochrany, která se použije aplikace sdílení RMS. Můžete změnit výchozí úroveň nativní pro obecný, z obecného na nativní a dokonce i zabránit aplikaci z použití ochrany pro sdílení obsahu RMS. Další informace naleznete [Změna úrovně ochrany výchozí souborů](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection) v tomto tématu.

### <a name="BKMK_SupportFileTypes"></a>Podporované typy souborů a přípon souborů
Následující tabulka uvádí typy souborů, které jsou nativně podporovaných sdílení aplikací Microsoft Rights Management. Pro tyto typy souborů původní příponu názvu souboru se změní, když je použit nativní chráněné a tyto soubory stát jen pro čtení.

Kromě toho při nativní aplikace pro sdílení obsahu RMS chrání Word, Excel nebo PowerPoint soubor, který uživatelům chránit tím, že sdílení, tato akce automaticky vytvoří druhý soubor, který je kopií původního se stejným názvem, ale s **.ppdf** přípony názvu ¹ souboru. Tato verze souboru zajišťuje, příjemci, kteří nainstalovat aplikaci sdílení RMS vždy otevřít soubor, který byl použit nativní ochrany.

Pro soubory, které jsou obecně chráněny se změní na .pfile vždy původní příponu názvu souboru.

> [!WARNING]
> Pokud máte brány firewall, proxy servery webových nebo softwaru pro zabezpečení, který zkontrolovat a provést akci podle přípon názvů souborů, může být nutné překonfigurovat tyto pro podporu nové přípony názvů souborů.

|Původní příponu názvu souboru|Příponu názvu souboru chráněného RMS|
|---------------------------------|----------------------------------------|
|TXT|.ptxt|
|XML|.pxml|
|JPG|.pjpg|
|JPEG|.ppng|
|PDF|.ppdf|
|PNG|.ppng|
|TIFF|.ptiff|
|BMP|.pbmp|
|GIF|.pgif|
|.giff|.pgiff|
|JPE|.pjpe|
|JFIF|.pjfif|
|.jif|.pjif|
|.JT|.PJT|
Používá technologii programem Foxit ¹ vykreslování PDF. Copyright © 2003 – 2014, programem Foxit Corporation.

Následující tabulka uvádí typy souborů, které sdílení aplikace Microsoft Rights Management nativně podporuje v aplikaci Microsoft Office 2016, Office 2013 a Office 2010. Pro tyto soubory příponu názvu souboru se nezmění po soubor je chráněn systémem RMS.

|Typy souborů podporované v Office|Typy souborů podporované v Office|
|-------------------------------------|-------------------------------------|
|DOC<br /><br />DOCM<br /><br />.docx<br /><br />.dot<br /><br />dotm<br /><br />dotx<br /><br />potm<br /><br />POTX<br /><br />PPS<br /><br />ppsm<br /><br />PPSX<br /><br />ppt<br /><br />pptm|PPTX<br /><br />.thmx<br /><br />XLA<br /><br />xlam<br /><br />.xls<br /><br />XLSB<br /><br />xlt<br /><br />XLSM<br /><br />XLSX<br /><br />XLTM<br /><br />XLTX<br /><br />XPS|

### <a name="BKMK_ChangeDefaultProtection"></a>Změna úrovně ochrany výchozí souborů
Je možné změnit, jak aplikace pro sdílení obsahu RMS chrání soubory úpravou registru. Můžete například vynutit soubory, které podporují nativní ochrany ke generické chybě chráněny pomocí aplikace sdílení RMS.

Důvody proč můžete chtít provést, postupujte takto:

-   Chcete-li zajistit, aby všichni uživatelé umožňující otevřít soubor ze svých mobilních zařízení.

-   Chcete-li zajistit, aby všichni uživatelé umožňující otevřít soubor, když nemají aplikaci, která podporuje nativní ochrany.

-   Chcete-li zohlednit systémech zabezpečení, které provést akce se soubory podle jejich příponu názvu souboru a může být nakonfigurovat tak, zohlednit příponu názvu souboru .pfile, ale nelze musí překonfigurovat skutečnost zohlednit více přípon názvů souborů pro nativní ochrany.

Podobně můžete vynutit aplikujte nativní ochrany souborů, které jsou ve výchozím nastavení, bude mít obecný ochranu použité pro sdílení obsahu RMS. To může být vhodné, pokud máte aplikace, která podporuje rozhraní API služby RMS – například, aplikace – firemní vytvořené své interní vývojáři nebo aplikaci, zakoupili od nezávislým dodavatelem softwaru (ISV).

Můžete také vynutit aplikace k blokování ochrany souborů pro sdílení obsahu RMS (nevztahuje nativní ochranu nebo obecný protection). Například to může být vyžadována Pokud máte automatizované aplikace nebo služby, které musí být možné otevřít určitý soubor ke zpracování jeho obsah. Pokud zablokujete ochranu pro určitý typ souboru, uživatelé k ochraně soubor, který má daný typ souboru nelze použít aplikaci sdílení RMS. Při pokusu, se uživatelům zobrazí zprávu, že správce zabránil ochrany a jejich musíte zrušit jejich akci, která má chráněný soubor.

Chcete-li nakonfigurovat aplikaci, aby použít obecný ochrany pro všechny soubory, které ve výchozím nastavení, by měly nativní ochrany, které jsou použity pro sdílení obsahu RMS, proveďte následující úpravy registru:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Vytvořit nový klíč s názvem **&#42;**.

    Toto nastavení označuje soubory s jakoukoliv příponou názvu souboru.

2.  V klíči nově přidané **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\ &#42;**, vytvořte novou hodnotu řetězce (REG_SZ) s názvem **šifrování** má hodnotu dat **Pfile**.

    Toto nastavení je výsledkem použití obecný Ochrana aplikace pro sdílení obsahu RMS.

Tyto dvě nastavení je výsledkem použití obecný ochranu pro všechny soubory, které mají příponu názvu souboru aplikace pro sdílení obsahu RMS. Pokud je to určitého cíle, není vyžadována žádná další konfigurace. Výjimky pro určité typy souborů, však můžete definovat tak, že jsou stále nativně chráněny. Chcete-li to provést, je třeba provést tři další registru úpravy pro každý typ souboru:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Přidáte nový klíč, který má název příponu názvu souboru (bez předchozího období).

    Například pro soubory, které mají .docx, přípony názvu souboru, vytvořte klíč s názvem **DOCX**.

2.  V klíči typ nově přidaného souboru (například **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), vytvořte novou hodnotu DWORD s názvem **AllowPFILEEncryption** má hodnotu **0**.

3.  V klíči typ nově přidaného souboru (například **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), vytvořte novou hodnotu řetězce s názvem **šifrování** má hodnotu **nativní**.

V důsledku tato nastavení jsou všechny soubory ke generické chybě chráněny kromě souborů, které mají příponu názvu souboru .docx, které jsou nativně chráněny pomocí aplikace sdílení RMS.

Opakujte tyto tři kroky pro jiné typy souborů, které chcete definovat jako výjimky, protože podporují nativní ochrany a nechcete, aby mohly být obecně chráněny pomocí aplikace sdílení RMS.

Můžete provádět podobné úpravy registru pro další scénáře změnou hodnotu **šifrování** řetězec, který podporuje následující hodnoty:

-   **Pfile**: Obecný ochrany

-   **Nativní**: Nativní ochrany

-   **Off**: Ochrana bloku

## Viz také
[Průvodce Rights Management sdílení aplikace uživatele](../Topic/Rights_Management_sharing_application_user_guide.md)

