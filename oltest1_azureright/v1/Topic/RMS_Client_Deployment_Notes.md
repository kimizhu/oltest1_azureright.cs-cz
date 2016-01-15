---
description: na
keywords: na
title: RMS Client Deployment Notes
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
---
# Pozn&#225;mky k nasazen&#237; klienta služby RMS
Služba Rights Management RMS (klient) verze 2 je také označována jako klient MSIPC. Je, že software pro počítače se systémem Windows, který komunikuje se službou Microsoft Rights Management services místně nebo v cloudu k ochraně přístup k a používání údajů jako prochází aplikací a zařízení, v rámci hranice vaší organizace nebo mimo těch spravované hranice. Kromě dodání s [Rights Management aplikace pro Windows pro sdílení](https://technet.microsoft.com/library/dn919648.aspx), klienta služby RMS je k dispozici [jako volitelně stáhnout](http://www.microsoft.com/download/details.aspx?id=38396) můžete v případě potvrzení a přijetí licenční smlouvy, volně distribuovat softwaru jiných dodavatelů, aby klienti mohli chránit a spotřebovávat obsah, který je chráněn Rights Management services.

Toto téma obsahuje následující oddíly:

-   [Další distribuci klienta služby RMS](#BKMK_RedistributeInstaller)

-   [Instalace klienta služby RMS](#BKMK_InstallClient)

-   [Dotazy a odpovědi týkající se klienta služby RMS](#BKMK_QA)

-   [Nastavení klienta služby RMS](#BKMK_Settings)

-   [Služby AD RMS pouze: Omezení klienta služby RMS k použití Důvěryhodné servery služby AD RMS](#BKMK_UsingTrustedServers)

-   [Zjišťování služby RMS](#BKMK_ServiceDiscovery)

## <a name="BKMK_RedistributeInstaller"></a>Další distribuci klienta služby RMS
Klient služby RMS můžete volně dále distribuovat a v sadě, s jinými aplikacemi a řešení IT. Pokud jsou vývojář aplikace nebo poskytovatele řešení a chcete distribuovat klienta služby RMS, máte dvě možnosti:

-   Doporučené: Vložit instalační program klienta služby RMS ve vaší instalaci aplikace a potom ho spusťte v tichém režimu ( **/quiet** přepínače, podrobně popsány v následující části).

-   Přesvědčte se, klienta služby RMS předpokladem pro vaši aplikaci. U tuto možnost budete možná muset poskytnout uživatelům další pokyny pro ně získat, nainstalovat a aktualizovat počítače s klientem, před použitím aplikace.

## <a name="BKMK_InstallClient"></a>Instalace klienta služby RMS
Klient služby RMS je obsažen v spustitelný soubor Instalační služby s názvem **setup_msipc_***&lt; Hledat &gt;***.exe**, kde *&lt; Hledat &gt;* je buď **x86** (pro 32-bit klientské počítače) nebo **x64** (pro 64bitové klientské počítače). 64bitový (x 64) instalační balíček nainstaluje jak 32-bit spustitelného pro zajištění kompatibility se službou 32bitových aplikací, které běží na 64bitový operační systém instalace, tak i 64-bit spustitelného pro podporu nativní 64bitové aplikace. Instalační program 32bitový (x 86), budou spuštěny na instalaci 64bitová verze systému Windows.

> [!NOTE]
> Je nutné zvýšenými oprávněními k instalaci klienta služby RMS, jako je členem skupiny Administrators v místním počítači.

Můžete nainstalovat klienta služby RMS pomocí některé z následujících způsobů instalace:

-   **Tichém režimu.** S použitím **/quiet** Přepnout jako součást možnosti příkazového řádku, můžete v počítačích bezobslužném režimu instalace klienta služby RMS. Následující příklad ukazuje bezobslužném režimu instalace pro klienta služby RMS 64bitové klientské počítače:

    ```
    setup_msipc_x64.exe /quiet
    ```

-   **Interaktivní režim.** Alternativně můžete nainstalovat klienta služby RMS pomocí na základě GUI instalačního programu, která je poskytována Průvodce instalací klienta služby RMS. Chcete-li to provést, poklepejte na instalačního balíčku klienta služby RMS (**setup_msipc_***&lt; Hledat &gt;***.exe**) ve složce, do kterého byl zkopírován nebo staženy do místního počítače.

## <a name="BKMK_QA"></a>Dotazy a odpovědi týkající se klienta služby RMS
V následující části obsahuje nejčastější dotazy týkající se klienta služby RMS a odpovědi na ně.

### Jaké operační systémy podporují klienta služby RMS?
Klient služby RMS je podporována v následujících operačních systémech:

|Serverový operační systém Windows|Klientský operační systém Windows|
|-------------------------------------|-------------------------------------|
|Windows Server 2012 R2|Windows 8.1.|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 s minimální s aktualizací SP1|
|Windows Server 2008 (pouze služby AD RMS)|Windows Vista s minimální SP2 (AD RMS pouze)|

### Které procesory nebo platformy podporovat klienta služby RMS?
Klient služby RMS je podporován na x 86 a x 64 computing platformy.

### Kde je nainstalován klient služby RMS?
Ve výchozím nastavení je nainstalován klient služby RMS v %ProgramFiles%\Active adresář Rights Management Services klienta 2. &lt; číslo podverze &gt;.

### Jaké soubory jsou přidruženy klientský software služby RMS?
Jako součást klientského softwaru služby RMS jsou nainstalovány následující soubory:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Kromě těchto souborů klienta služby RMS také nainstaluje soubory podporující sadu multilingual user interface (MUI) v 44 jazycích. Chcete-li ověřit jazyky podporované, spusťte instalaci klienta služby RMS a po dokončení instalace zkontrolujte obsah složky podpora více jazyků ve složce výchozí cestu.

### Klient služby RMS zahrnuta ve výchozím nastavení je při instalaci na podporovaný operační systém?
Číslo. Tato verze klienta služby RMS je dodávána volitelné ke stažení, který je možné nainstalovat odděleně v počítačích se systémem podporované verze operačního systému Microsoft Windows.

### Je klient služby RMS automaticky aktualizován prostřednictvím služby Microsoft Update?
Pokud jste nainstalovali tohoto klienta služby RMS pomocí možnosti tichou instalaci, dědí klienta služby RMS aktuální nastavení služby Microsoft Update. Pokud jste nainstalovali klienta služby RMS pomocí na základě GUI instalačního programu, Průvodce instalací klienta služby RMS vás vyzve k povolení služby Microsoft Update.

## <a name="BKMK_Settings"></a>Nastavení klienta služby RMS
V následující části obsahuje nastavení informace o klienta služby RMS. Tyto informace mohou být užitečné, pokud dochází k problémům s aplikacemi a službami, které používají klienta služby RMS.

> [!NOTE]
> Některá nastavení, závisí na tom, zda spuštění aplikace RMS enlightened jako aplikace v režimu klienta (například aplikace Microsoft Word a aplikace Outlook nebo aplikaci sdílení RMS) nebo aplikace v režimu serveru (například služby SharePoint a Exchange).  V následujících tabulkách, tato nastavení jsou označeny jako **režim klienta** a **režim serveru**, v tomto pořadí.

### Licence, kde úložiště klienta služby RMS v klientských počítačích
Klient služby RMS ukládá licencí na místním disku a také ukládá do mezipaměti některé informace v registru systému Windows.

|Popis|Režim cest|Režim cesty k serveru|
|---------|--------------|-------------------------|
|Umístění úložiště licencí|%localappdata%\Microsoft\MSIPC|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\*&lt; SID &gt;*\|
|Šablona umístění úložiště|%localappdata%\Microsoft\MSIPC\Templates|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\Templates\*&lt; SID &gt;*\|
|Umístění v registru|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> nastavení \Local<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> /*&lt; SID &gt;*|
> [!NOTE]
> *&lt; SID &gt;* je identifikátor zabezpečení (SID) pro účet, pod kterým běží serverové aplikace. Například pokud aplikace běží pod předdefinovaný účet síťové služby, nahradit *&lt; SID &gt;* s hodnotou známý SID pro tento účet (S-1-5-20).

### Nastavení registru systému Windows pro klienta služby RMS
Klíče registru systému Windows slouží k nastavení nebo změna některé konfigurace klienta služby RMS. Můžete například jako správce pro službu RMS enlightened aplikace, které komunikovat se servery služby AD RMS, můžete aktualizovat umístění služby enterprise (přepsání AD RMS serveru, který je aktuálně vybraných pro publikování) v závislosti na klientském počítači aktuální umístění v rámci vaší topologie služby Active Directory. Nebo můžete chtít povolit trasování RMS v klientském počítači, které vám pomohou vyřešit problémy s aplikacemi RMS enlightened. V následující tabulce použijte k identifikaci nastavení registru, které můžete změnit pro klienta služby RMS.

|Úloha|Nastavení|
|---------|-------------|
|Služby AD RMS pouze: Chcete-li aktualizovat umístění služby enterprise klientského počítače|Aktualizace následujících klíčů registru:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />    REG_SZ: výchozí<br />    **Hodnota:**&lt; protokolu http nebo https &gt; :// *RMS_Cluster_Name*/_wmcs/certifikaci<br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />    REG_SZ: výchozí<br />    **Hodnota:** &lt; protokolu http nebo https &gt; :// *RMS_Cluster_Name*/_wmcs/Licensing|
|Povolení a zakázání trasování|Aktualizujte následující klíč registru:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />    REG_DWORD: Trasování<br />    **Hodnota:** 1, chcete-li povolit trasování, 0, chcete-li zakázat trasování (výchozí)|
|Chcete-li změnit frekvenci ve dnech, chcete-li aktualizovat šablony|Následující hodnoty registru určit, jak často bude aktualizován šablony v počítači uživatele není nastavena hodnota TemplateUpdateFrequencyInSeconds.  Pokud jsou nastaveny ani jeden z těchto hodnot, je výchozí hodnota intervalu pro aplikace pomocí klienta služby RMS (verze 1.0.1784.0), chcete-li stáhnout šablony 1 den. Verze před to mít výchozí hodnota je každých 7 dnů.<br /><br />**Režim klienta:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Hodnota:** Celočíselná hodnota, která určuje počet dní (minimálně 1) mezi soubory ke stažení.<br /><br />**Režim serveru:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Hodnota:** Celočíselná hodnota, která určuje počet dní (minimálně 1) mezi soubory ke stažení.|
|Chcete-li změnit frekvenci v sekundách, chcete-li aktualizovat šablony **Important:** Pokud je tento parametr zadán, bude hodnota aktualizace šablony ve dnech je ignorována. Zadejte jednu nebo druhou, ne však obojí.|Následující hodnoty registru určit, jak často bude možné aktualizovat šablony v počítači uživatele. Pokud není nastavena tato hodnota nebo chcete-li změnit frekvenci ve dnech (TemplateUpdateFrequency), je výchozí hodnota intervalu pro aplikace pomocí klienta služby RMS (verze 1.0.1784.0), chcete-li stáhnout šablony 1 den. Verze před to mít výchozí hodnota je každých 7 dnů.<br /><br />**Režim klienta:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Hodnota:** Celočíselná hodnota, která určuje počet sekund (minimálně 1) mezi soubory ke stažení.<br /><br />**Režim serveru:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Hodnota:** Celočíselná hodnota, která určuje počet sekund (minimálně 1) mezi soubory ke stažení.|
|Služby AD RMS pouze: Chcete-li stáhnout šablony okamžitě v dalším publikování požadavku|Při testování a vyhodnocení měli byste klienta služby RMS na co nejdříve stáhnout šablony. Chcete-li to provést, odstraňte následující klíč registru a klienta služby RMS bude stáhnout šablony okamžitě v dalším požadavku publikování, nikoli počkejte za dobu určenou v závislosti na nastavení registru TemplateUpdateFrequency:<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; název serveru &gt; \Template **Note:** &lt; název serveru &gt; může mít externí (corprights.contoso.com) a adresy URL interní (corprights) a proto dvě různé položky.|
|Služby AD RMS pouze: Chcete-li povolit podporu pro federovaného ověření|Je-li klientský počítač RMS připojí k clusteru služby AD RMS pomocí federovaného vztahu důvěryhodnosti, je nutné nakonfigurovat domovskou sféru federace.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_SZ: FederationHomeRealm<br />    **Hodnota:** Hodnota této položky registru je identifikátor (URI) služby federation service (například "https://fs-01.contoso.com").|
|Služby AD RMS pouze: Pro podporu partnera federačních serverech, které vyžadují ověřování založené na formulářích na vstup uživatele|Ve výchozím nastavení klienta služby RMS provozované v tichém režimu a není vyžadováno vstup uživatele. Partner federačních serverech, však může nakonfigurovat tak, aby požadovat vstup uživatele, například jako pomocí ověřování na základě formulářů. V takovém případě musíte nakonfigurovat klienta služby RMS ignorovat v tichém režimu, aby formulář federovaného ověření se zobrazí v okně prohlížeče a uživatel je povýšen pro ověřování.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_DWORD: EnableBrowser **Note:** Je-li na federačním serveru konfigurován pro použití ověřování pomocí formulářů, je třeba zadat Tento klíč. Pokud na federačním serveru konfigurován pro použití integrovaného ověřování systému Windows, tento klíč není povinný.|
|Služby AD RMS pouze: Chcete-li blokovat ILS služby spotřeba|Ve výchozím nastavení klienta služby RMS umožňuje náročných obsah chráněný službou ILS ale můžete nakonfigurovat klienta tak, aby tato služba blokovat nastavením následující klíč registru. Pokud tento klíč registru je nastavena na blokovat službu ILS, bude jakékoli pokusy o otevření a spotřebovávat obsah chráněný službou ILS vrátil následující chybu:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: **DisablePassportCertification**<br />    **Hodnota:** 1 blokovat ILS spotřeby, 0, chcete-li povolit používání ILS (výchozí)|

### Správa distribuce šablony pro klienta služby RMS
Šablony usnadnit uživatelům a správcům rychle použít Rights Management ochrany a klienta služby RMS automaticky stáhne šablony z jeho servery RMS nebo služby, je-li vložit šablony, které se v následujícím umístění složky, nebude klienta služby RMS stáhnout všechny šablony z výchozího umístění a namísto toho stáhnout šablony, které jste umístili v této složce. Klient služby RMS může nadále stáhnout šablony z jiných dostupných serverů RMS.

**Režim klienta:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Režim serveru:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\*&lt; SID &gt;*

Při použití v této složce neexistuje žádné speciální konvenci požadované s tím rozdílem, že šablony, které by měl být vydán RMS server nebo služby a jejich musí mít příponu názvu souboru XML. Můžete například Contoso Confidential.xml nebo Contoso ReadOnly.xml jsou platné názvy.

## <a name="BKMK_UsingTrustedServers"></a>Služby AD RMS pouze: Omezení klienta služby RMS k použití Důvěryhodné servery služby AD RMS
Klient služby RMS lze omezit pomocí konkrétní důvěryhodné služby AD RMS servery pouze tím, že tyto změny do registru systému Windows v místních počítačích.

**Chcete-li povolit omezení RMS klienta k použití pouze důvěryhodné servery služby AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_DWORD: AllowTrustedServersOnly

    **Hodnota:** Pokud je zadán nenulovou hodnotu, budou klienta služby RMS důvěřovat pouze zadané servery, které jsou nakonfigurovány v seznamu TrustedServers a službou Azure Rights Management.

**Chcete-li přidat členy do seznamu Důvěryhodné servery služby AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_SZ: *&lt; URL_or_HostName &gt;*

    **Hodnota:** Řetězcové hodnoty přidané v tomto umístění klíče registru může být buď formát název domény DNS (například **adrms.contoso.com**) nebo úplné adresy URL na důvěryhodné servery služby AD RMS (například **https://adrms.contoso.com**). Pokud zadaná adresa URL začíná **https://**,  klienta služby RMS bude používat protokol SSL nebo TLS se připojit k zadané serveru služby AD RMS.

## <a name="BKMK_ServiceDiscovery"></a>Zjišťování služby RMS
Zjišťování služby RMS vám umožní zkontrolovat, které RMS server nebo služby ke komunikaci se službou před chrání obsah klienta služby RMS. Zjišťování služby může také dojít, pokud klient služby RMS spotřebovává chráněný obsah, ale je méně pravděpodobné, že dojít, protože tyto zásady připojena k obsahu obsahuje upřednostňovaný server RMS nebo služby a pouze v případě, který neúspěšné nemá klient spusťte zjišťování služby.

Zjišťování služby hledá nejprve s místní verzí aplikace Rights Management (AD RMS). Pokud bude tento krok neúspěšný, zjišťování služby automaticky vyhledá verzi cloudu Rights Management (Azure RMS).

Při provádění zjišťování služby pro nasazení součásti místně, ověří klienta služby RMS následující:

1.  Registru systému Windows v místním počítači: Pokud nastavení zjišťování služby jsou nakonfigurována v registru, tato nastavení, jsou použity jako první.  Ve výchozím nastavení nejsou konfigurována v registru.

2.  Active Directory Domain Services: Počítač domény připojený k dotazuje služby Active Directory na spojovací bod služby (spojovací bod služby). Pokud je registrovaný spojovací bod služby, je vrácena RMS klienta k použití na adresu URL serveru RMS.

### Služby AD RMS pouze: Povolení zjišťování služby na straně serveru pomocí služby Active Directory
Pokud váš účet nemá dostatečná oprávnění (skupiny Enterprise Admins a místní správce na serveru služby AD RMS), můžete automaticky zaregistrovat spojovací bod služby (spojovací bod) při instalaci serveru služby AD RMS kořenového clusteru. Pokud spojovací bod služby již existuje v doménové struktuře, musíte nejprve odstranit stávající spojovací bod předtím, než se můžete zaregistrovat nový.

Můžete zaregistrovat a odstranit spojovací bod služby po instalaci služby AD RMS pomocí následujícího postupu. Než začnete, ujistěte se, že váš účet požadovaná oprávnění (skupiny Enterprise Admins a místní správce na serveru služby AD RMS).

##### Chcete-li povolit zjišťování služby AD RMS pomocí registrace spojovací bod služby ve službě Active Directory

1.  Otevřete konzolu pro správu služby Active Directory Services na serveru služby AD RMS:

    -   Pokud používáte systém Windows Server 2008 R2 nebo Windows Server 2008, klikněte na tlačítko **Start**, klikněte na tlačítko **Nástroje pro správu**, a potom klikněte na tlačítko **Active Directory Rights Management Services**.

    -   Pokud používáte systém Windows Server 2012 R2 nebo Windows Server 2012, v části správce serveru, klikněte na tlačítko **Nástroje**, a potom klikněte na tlačítko **Active Directory Rights Management Services**.

2.  V konzole služby AD RMS klikněte pravým tlačítkem na clusteru služby AD RMS a potom klikněte na tlačítko **Vlastnosti**.

3.  Klikněte na tlačítko **spojovací bod** karty.

4.  Vyberte **Změnit spojovací bod služby** zaškrtávací políčko.

5.  Vyberte **Nastavit spojovací bod služby na aktuální certifikační cluster** možnost a potom klikněte na tlačítko **OK**.

### Povolení zjišťování služby na straně klienta pomocí registru systému Windows
Jako alternativu k použití spojovací bod služby nebo kde spojovací bod služby neexistuje můžete konfigurovat registru v klientském počítači, aby mohl klient služby RMS najít jeho serveru služby AD RMS.

##### Chcete-li povolit zjišťování služby AD RMS klientů pomocí registru systému Windows

1.  Otevřete editor registru systému Windows, Regedit.exe:

    -   V klientském počítači, v okně Spustit zadejte **regedit**, a potom stiskněte klávesu ENTER otevřete Editor registru.

2.  V editoru registru přejděte do **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!IMPORTANT]
    > Pokud používáte 32bitové aplikace v počítači se 64bitovou, cesta bude mít takto: 
    > **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3.  Chcete-li vytvořit podklíč ServiceLocation, klikněte pravým tlačítkem na **MSIPC**, přejděte na příkaz **Nový**, klikněte na tlačítko **klíč**, a poté zadejte **ServiceLocation**.

4.  Chcete-li vytvořit podklíč EnterpriseCertification, klikněte pravým tlačítkem na **ServiceLocation**, přejděte na příkaz **Nový**, klikněte na tlačítko **klíč**, a poté zadejte **EnterpriseCertification**.

5.  Nastavit adresu URL organizace certifikace, dvakrát klikněte na položku **(výchozí)** hodnota, v části **EnterpriseCertification** podklíč a pokud **Upravit řetězec** zobrazí se dialogové okno pro **Údaj hodnoty**, typ &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Certification, a potom klikněte na tlačítko **OK**.

6.  Chcete-li vytvořit podklíč EnterprisePublishing, klikněte pravým tlačítkem na **ServiceLocation**, přejděte na příkaz **Nový**, klikněte na tlačítko **klíč**, a poté zadejte EnterprisePublishing.

7.  Chcete-li nastavit enterprise publikování adresa URL, dvakrát klikněte na položku **(výchozí)** , v části **EnterprisePublishing** podklíč a pokud **Upravit řetězec** dialogového okna se zobrazí, zadejte pro **Údaj hodnoty** následující &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Licensing, a potom klikněte na tlačítko **OK**.

8.  Zavřete Editor registru.

Pokud není zadán v registru klienta služby RMS nelze najít spojovací bod služby pomocí dotazu služby Active Directory, se nezdaří volání zjišťování služby pro službu AD RMS.

### Přesměrování licencování provozu serveru
V některých případech je nutné přesměrovat provoz během zjišťování služby, například když jsou sloučeny dvěma organizacemi a původní licenční server v jedné organizaci je zastaralé a klienti musí být přesměrován na nový server správy licencí. Případně můžete provést migraci ze služby AD RMS k Azure RMS. Chcete-li povolit licencování přesměrování, pomocí následujícího postupu.

##### Chcete-li povolit RMS licencování přesměrování pomocí registru systému Windows

1.  Otevřete editor registru systému Windows, Regedit.exe:

    -   V klientském počítači, v okně Spustit zadejte **regedit**, a potom stiskněte klávesu ENTER otevřete Editor registru.

2.  V editoru registru přejděte do jednoho z následujících akcí:

    -   Pro 64bitové verze systému Office na platformě x 64 platformy: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   Pro 32bitové verze systému Office na platformě x 64 platformy: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Vytvořit podklíč LicensingRedirection, kliknutím pravým tlačítkem myši **Servicelocation**, přejděte na příkaz **Nový**, klikněte na tlačítko **klíč**, a poté zadejte **LicensingRedirection**.

4.  Chcete-li nastavit licencování přesměrování, klikněte pravým tlačítkem myši **LicensingRedirection** podklíč, vyberte možnost **Nový**, a potom vyberte **Hodnota typu řetězec**.  Pro **název**, zadejte předchozí server licencování adresy URL a pro **hodnotu** zadejte nový server licencování adresy URL.

    Přesměrovat služby Licencování ze serveru Contoso.com postupně Fabrikam.com, je můžete například zadat následující hodnoty:

    **Název:** `https://contoso.com/_wmcs/licensing`

    **Hodnota:** `https://fabrikam.com/_wmcs/licensing`

    > [!NOTE]
    > Má-li původní licenční server intranetové a extranetové adresy URL potom zadat nový název a hodnotu mapování musí být nastavena pro obě tyto adresy URL v klíči LicensingRedirection.

5.  Opakujte předchozí krok pro všechny servery, které potřebují k přesměrování.

6.  Zavřete Editor registru.

