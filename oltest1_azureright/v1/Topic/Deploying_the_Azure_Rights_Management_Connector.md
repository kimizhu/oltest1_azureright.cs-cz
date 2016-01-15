---
description: na
keywords: na
title: Deploying the Azure Rights Management Connector
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
---
# Nasazen&#237; konektoru Azure Rights Management
Tyto informace použijte další informace o konektoru Microsoft Rights Management (RMS) a jeho použití pro poskytování ochrany informace s existující místní nasazení, které používají Microsoft Exchange Server, Microsoft SharePoint Server nebo souborové servery, které používají systém Windows Server a schopností soubor klasifikace infrastruktury (FCI) ze Správce prostředků souborového serveru.

> [!TIP]
> Nejdůležitější ukázkový scénář s snímky obrazovky, naleznete v části [Automaticky chrání soubory na souborových serverech se systémem Windows Server a souboru klasifikace infrastruktury](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Example_FCI) v oddílu [Co je Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tématu.

## <a name="OverviewConnector"></a>Přehled konektor Microsoft Rights Management
Konektor Microsoft Rights Management (RMS) umožňuje rychle povolit existující na místní servery jejich funkce Správa informačních práv (IRM) pomocí (Azure RMS) cloudové služby Microsoft Rights Management. Pomocí této funkce IT a uživatelé mohli snadno chránit dokumenty a obrázky ve vaší organizaci a vně, aniž byste museli instalovat další infrastruktury nebo navazování vztahů důvěryhodnosti s dalšími organizacemi. I v případě, že někteří uživatelé se připojují k online službám ve scénáři hybridní, můžete použít tento konektor. Například použijte někteří uživatelé poštovních schránek Exchange Online a poštovních schránek někteří uživatelé používají Exchange Server. Po instalaci konektoru služby RMS všichni uživatelé lze chránit a využívat e-maily a přílohy pomocí Azure RMS, a ochrana informací funguje bez problémů mezi konfigurací dvě nasazení.

Konektor služby RMS je služba malé nárokům nainstalovat místně, na serverech se systémem Windows Server 2012 R2, Windows Server 2012 nebo Windows Server 2008 R2. Kromě spuštěna konektor na fyzické počítače, jej můžete spustit také na virtuálních počítačů, včetně virtuálních počítačích Azure IaaS. Po instalaci a konfiguraci konektoru, funguje jako komunikační rozhraní (předávání) mezi servery pro místní a cloudové služby.

Pokud spravujete klíč klienta pro službu Azure RMS (používání, které vlastníte klíč nebo BYOK scénář), konektor služby RMS a na místní servery, které ji používají nemají přístup k hardwaru zabezpečení modul (hardwarového zabezpečení), který obsahuje klíč klienta. Toto je vzhledem k tomu, že všechny kryptografické operace, které používají klienta klíč jsou prováděny v Azure RMS a není místní.

![](../Image/RMS_connector.png)

Konektor služby RMS podporuje následující na místní servery: Exchange Server, SharePoint Server a souborové servery, které používají systém Windows Server a souboru klasifikace infrastruktury pro klasifikaci a aplikovat zásady do dokumentů Office ve složce. Pokud chcete chránit všechny typy souborů pomocí souboru klasifikace, nepoužívejte konektor služby RMS, ale místo toho použijte [ochranu RMS rutin](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> Podporované verze těchto na místní servery, naleznete v části "místní servery, které podporují Azure RMS" v [Aplikace, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu.

V následujících částech použijte při plánování, instalaci a konfiguraci konektoru služby RMS. Poté je nutné provést některé konfigurace instalace příspěvek tak, aby vaše servery můžete použít konektor.

-   [Prerequisites for the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_Prereqs)

-   **Krok 1:**  [Installing the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_InstallingConnector)

-   **Krok 2:**  [Entering credentials](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#EnteringCredentials)

-   **Krok 3:**  [Authorizing servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#AuthorizingServers)

-   **Krok 4:**  [Configuring load balancing and high availability](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#ConfiguringConnector)

-   Volitelné: [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS)

-   Volitelné: [Configuring the RMS connector for a web proxy server](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringWebProxy)

-   Volitelné: [Installing the RMS connector administration tool on administrative computers](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_InstallingStandaloneTool)

-   **Krok 5:**  [Configuring servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#ConfiguringServers)

    -   [Configuring an Exchange server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ExchangeServer)

    -   [Configuring a SharePoint server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringSharePoint)

    -   [Configuring a file server for File Classification Infrastructure to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_FileServer)

-   [Next steps](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_NextSteps)

## <a name="BKMK_Prereqs"></a>Požadavky na konektor služby RMS
Před instalací konektoru služby RMS, ujistěte se, že jsou splněny následující požadavky.

|Požadavek|Další informace|
|-------------|-------------------|
|Aktivaci služby Rights Management (RMS)|[Aktivace Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md)|
|Synchronizaci adresářů mezi doménovými strukturami služby Active Directory a Azure Active Directory|Po aktivaci služby RMS Azure Active Directory byla nakonfigurována pro práci s uživateli a skupinami v databázi služby Active Directory. **Important:** Je nutné provést tento krok synchronizace adresáře pro konektor RMS pro práci i pro testovací síť. I když Office 365 a Azure Active Directory můžete používat pomocí účtů, které ručně vytvořit ve službě Azure Active Directory, vyžaduje tento konektor, že účty v Azure Active Directory jsou synchronizovány s Active Directory Domain Services; Synchronizace hesel ruční není dostatečná.<br />Další informace naleznete v následujících zdrojích:<br /><br />-   [Pokyny ke konfiguraci klientovi Azure AD](http://technet.microsoft.com/library/hh967611.aspx)<br />-   [Pokyny k povolení synchronizace adresáře s AAD pomocí DirSync](http://technet.microsoft.com/library/hh967642.aspx)|
|Volitelné, ale doporučené:<br /><br />-   Povolit federaci mezi místní služby Active Directory a Azure Active Directory|Můžete povolit federaci identit mezi vaším místním adresářem a Azure Active Directory. Tato konfigurace umožňuje lepší zkušenosti uživatele pomocí jednotného přihlášení ke službě RMS. Bez jednotné přihlašování uživatelé jsou výzva k zadání přihlašovacích údajů před použitím obsahu chráněného právy.<br /><br />Pokyny ke konfiguraci federace pomocí služby Active Directory Federation Services (AD FS) mezi Active Directory Domain Services a Azure Active Directory naleznete v tématu [Kontrolní seznam: Pomocí služby AD FS implementace a Správa jednotného přihlašování](http://technet.microsoft.com/library/jj205462.aspx) v knihovně Windows Server.|
|Nejméně dva členské počítače, na který chcete nainstalovat konektor služby RMS:<br /><br /><ul><li>64-bit fyzický nebo virtuální počítač spuštěn jeden z následujících operačních systémů:<br /><br /><ul><li>Windows Server 2012 R2</li><li>Windows Server 2012</li><li>Windows Server 2008 R2</li></ul></li><li>Alespoň 1 GB paměti RAM</li><li>Minimálně 64 GB místa na disku</li><li>Nejméně jedno síťové rozhraní</li><li>Přístup k Internetu prostřednictvím brány firewall (nebo webový proxy server), který nevyžaduje ověření</li><li>Musí být v doméně, která důvěřuje jiných doménových strukturách v organizaci, které obsahují instalace serverů Exchange nebo služby SharePoint, které chcete používat s konektorem služby RMS nebo doménové struktury</li></ul>|Pro vysokou dostupnost a odolnost proti chybám je třeba nainstalovat konektor služby RMS na nejméně dva počítače. **Tip:** Pokud používáte aplikaci Outlook Web Access nebo mobilní zařízení, které používají technologii Exchange ActiveSync IRM a je velmi důležité udržovat přístup k e-mailů a příloh, které jsou chráněné službou Azure RMS, doporučujeme vám, že nasadíte skupinu s vyrovnáváním zatížení serverů konektor k zajištění vysoké dostupnosti.<br />Není nutné vyhrazené servery pro spuštění konektoru, ale je nutné nainstalovat do samostatného počítače ze serverů, které budou používat konektor. **Important:** Neinstalujte konektoru na počítači se systémem Exchange Server, SharePoint Server nebo souborový server, který je nakonfigurován pro soubor klasifikace infrastruktury, pokud chcete použít funkci z těchto služeb službou Azure RMS. Tento konektor také neinstalujte na řadiči domény.|

## <a name="BKMK_InstallingConnector"></a>Instalace konektoru služby RMS
Po potvrzení předpokladů v předchozí části, použijte následující pokyny k instalaci konektoru služby RMS:

1.  Zjistěte, které budou spuštěny služby RMS konektor počítače (nejméně dva). Musí splňovat minimální specifikace uvedené v předchozím oddílu.

    > [!NOTE]
    > Jeden konektor služby RMS (který se skládá z více serverů pro zajištění vysoké dostupnosti) nainstaluje na klienta (Office 365 klienta nebo klienta Azure AD). Na rozdíl od Active Directory RMS není nutné instalovat konektoru služby RMS v každé doménové struktuře.

2.  Stáhnout zdrojové soubory pro konektor služby RMS z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

    Pokud chcete nainstalovat konektor služby RMS, stáhněte si RMSConnectorSetup.exe.

    Navíc platí:

    -   Pokud chcete později ke konfiguraci konektoru z 32bitového počítače, také stáhněte RMSConnectorAdminToolSetup_x86.exe.

    -   Pokud chcete pomocí nástroje Konfigurace serveru pro konektor služby RMS, k automatické konfiguraci nastavení registru na můžete na místní servery, také stáhněte GenConnectorConfig.ps1.

3.  V počítači, na kterém chcete nainstalovat konektor služby RMS, spusťte **RMSConnectorSetup.exe** s oprávněními správce.

4.  Na stránce Vítejte Microsoft Rights Management konektor instalační stránce vyberte **nainstalovat Microsoft Rights Management konektoru na počítači**, a potom klikněte na tlačítko **Další**.

5.  Číst a souhlasím s podmínkami licenční konektor služby RMS a potom klikněte na tlačítko **Další**.

Chcete-li pokračovat, zadejte účet a heslo ke konfiguraci konektoru služby RMS.

## <a name="EnteringCredentials"></a>Zadání pověření
Před konfigurací konektoru služby RMS, musí zadat pověření pro účet, který má dostatečná oprávnění ke konfiguraci konektoru služby RMS.

Kromě toho, pokud jste implementovali [Registrace ovládacích prvků](https://technet.microsoft.com/library/jj658941.aspx), ujistěte se, že účet zadáte moci chránit obsah. Například pokud jste omezili možnost chránit obsah do skupiny "IT oddělení", účet, který zde zadáte musí být členy této skupiny. Pokud tomu tak není, zobrazí se chybová zpráva: **Zjistit umístění služby správy a organizace se nezdařilo. Zkontrolujte, zda je povolena služba Microsoft Rights Management pro vaši organizaci.**

Můžete použít účet, který má jednu z následujících oprávnění:

-   **Správce klienta office 365**: Účet, který je globální správce pro vašeho klienta Office 365.

-   **Globální správce azure Rights Management**: Účet s oprávněními správce pro klienta Azure RMS.

-   **Konektor Microsoft RMS správce**: Účet v Azure Active Directory, které bylo uděleno oprávnění k instalaci a správě konektor služby RMS vaší organizace.

    > [!NOTE]
    > Pokud chcete použít konektor Microsoft RMS účet správce, je nutné provést následující přiřazení role správce konektor služby RMS:
    > 
    > 1.  Ve stejném počítači stáhněte a nainstalujte prostředí Windows PowerShell pro Rights Management. Další informace naleznete v tématu [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 
    >     Spusťte prostředí Windows PowerShell se **Spustit jako správce** příkazů a připojit ke službě Azure RMS pomocí [Připojit AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) příkaz:
    > 
    >     ```
    >     Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  Spusťte [Přidat AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) příkaz, pomocí právě jeden z následujících parametrů:
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
    >     ```
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
    >     ```
    > 
    >     ```
    >     Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
    >     ```
    >     Například zadejte: **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role " ConnectorAdministrator "**
    > 
    >     Přestože tyto příkazy používat ConnectorAdministrator role, můžete také použít GlobalAdministrator role zde také.

Během procesu instalace konektoru služby RMS je ověřen a nainstalován veškerý požadovaný software, Internetové informační služby (IIS) je nainstalována Pokud již nejsou přítomny a software konektoru je nainstalován a nakonfigurován. Kromě toho Azure RMS je připraven pro konfiguraci vytvořením následující:

-   Prázdná tabulka serverů, které jsou oprávnění k používání konektoru ke komunikaci s Azure RMS. Servery budou v této tabulce přidat později.

-   Sada tokeny zabezpečení pro konektor nástroje, které povolují operace s Azure RMS. Tyto tokeny jsou staženy z Azure RMS a nainstalován v místním počítači v registru. Jsou chráněny pomocí pověření účtu Local System a rozhraní data protection application programming interface (DPAPI).

Na poslední stránce průvodce proveďte následující a potom klikněte na tlačítko **Dokončit**:

-   Pokud je to první konektor, který jste nainstalovali, nevybírejte **spuštění konzoly Správce konektoru ověřovat servery** v tomto okamžiku. Tuto možnost vyberete po instalaci konektoru RMS vaší druhý (nebo finální). Místo toho spusťte znovu Průvodce alespoň jeden další počítače. Je nutné nainstalovat minimálně dva konektory.

-   Pokud jste nainstalovali konektor nástroje druhý (nebo poslední), vyberte možnost **spuštění konzoly Správce konektoru ověřovat servery**.

> [!TIP]
> V tomto okamžiku je ověřovací test, kterou lze provést testování, zda jsou funkční webové služby pro konektor služby RMS:
> 
> -   Z webového prohlížeče připojit k **http://&lt;connectoraddress&gt;/_wmcs/certification/servercertification.asmx**, nahrazení *&lt; connectoraddress &gt;* adresu serveru nebo název, který má RMS konektor nainstalován. Zobrazuje úspěšné připojení **ServerCertificationWebService** stránky.

Pokud je potřeba odinstalovat konektor služby RMS, spusťte průvodce znovu a vyberte možnost odinstalovat.

## <a name="AuthorizingServers"></a>Ověřování serverů k používání konektoru služby RMS
Pokud jste nainstalovali konektor služby RMS na nejméně dva počítače, budete chtít povolit servery a služby, které chcete použít konektor služby RMS. Například servery se systémem Exchange Server 2013 nebo SharePoint Server 2013.

Pokud chcete definovat tyto servery, spusťte nástroj pro správu konektoru služby RMS a přidání položky do seznamu povolených serverů. Tento nástroj můžete spustit, když vyberete **spuštění konzoly pro správu konektoru ověřovat servery** na konci konektor Microsoft Rights Management nastavení průvodce, nebo jej lze spustit samostatně z průvodce.

Když autorizujete tyto servery, mějte na paměti následující pokyny:

-   Servery, které přidáte, budou udělena zvláštní oprávnění. Všechny účty, které zadáte pro roli serveru Exchange Server v konfiguraci konektoru bude udělen [superuživatele role](https://technet.microsoft.com/library/mt147272.aspx) v Azure RMS, která jim uděluje přístup k celému obsahu pro tohoto klienta služby RMS. Funkci superuživatele automaticky povolena v tomto okamžiku v případě potřeby. Aby se zabránilo bezpečnostní riziko zvýšení oprávnění, dejte pozor, abyste zadejte pouze účty, které jsou používány servery Exchange v organizaci. Všechny servery, které jsou nakonfigurovány jako servery SharePoint nebo souborové servery, které používají FCI bude udělen pravidelné uživatelská oprávnění.

-   Můžete přidat více serverů jako jediná položky zadáním zabezpečení služby Active Directory nebo distribuční skupinu nebo účet služby, který je používán pro více než jeden server. Při použití této konfigurace skupiny serverů budou sdílet stejnou certifikáty služby RMS a budou všechny považovány za vlastníky pro obsah, který některého z nich chráněna. Chcete-li minimalizovat správní režie, doporučujeme použití této konfigurace do jedné skupiny, nikoli jednotlivých serverů autorizovat servery Exchange v organizaci nebo serverové farmy služby SharePoint.

Na **servery povoleno využívat konektor** klikněte na tlačítko **Přidat**.

### <a name="BKMK_AddServer"></a>Přidání serveru do seznamu povolených serverů
Na **Povolit server využívat konektor** stránky, zadejte název objektu nebo procházením určete objekt, který chcete povolit.

Je důležité, že povolit správný objekt. Pro server k používání konektoru je třeba vybrat účet, který spouští službu na místě (například Exchange nebo SharePoint) pro autorizaci. Například pokud je služba spuštěna jako účet konfigurovaných služeb, přidejte do seznamu název tohoto účtu služby. Pokud je služba spuštěna jako místní systém, přidejte název objektu počítače (například SERVERNAME$). Jako nejlepší postup vytvoření skupiny, která obsahuje tyto účty a zadejte skupinu namísto názvy jednotlivých serverů.

Další informace o rolích jiný server:

-   U serverů se systémem Exchange: Je nutné zadat skupinu zabezpečení a můžete použít výchozí skupiny (**servery Exchange**), Exchange automaticky vytvoří a udržuje ve všech serverech Exchange v doménové struktuře.

-   U serverů se systémem SharePoint:

    -   Pokud server služby SharePoint 2010 je konfigurován pro spouštět jako místní systém (není pomocí účtu služby), ručně vytvořte skupinu zabezpečení ve službě Active Directory Domain Services a přidejte objekt názvu počítače pro server v této konfiguraci do této skupiny.

    -   Pokud SharePoint server je konfigurován pro použití účtu služby (doporučený postup pro SharePoint 2010) a jedinou možností pro SharePoint 2013, postupujte takto:

        1.  Přidejte účet služby, který spouští službu Centrální správa SharePoint k povolení služby SharePoint nakonfigurováno z konzoly pro správu.

        2.  Přidejte účet, který je nakonfigurován pro fond aplikací služby SharePoint.

        > [!TIP]
        > Pokud tyto dva účty jsou odlišné, zvažte vytvoření jedné skupiny, který obsahuje oba účty minimalizovat správní režie.

-   Pro souborové servery používající soubor klasifikace infrastrukturu přidružené služby spustit jako účet místní systém, je nutné autorizovat účet počítače pro souborové servery (například SERVERNAME$) nebo skupiny, která obsahuje tyto účty počítačů.

Po dokončení přidávání serverů do seznamu, klikněte na tlačítko **Zavřít**.

Pokud jste tak již neučinili, musíte nyní konfigurace vyrovnávání zatížení pro servery, které mají nainstalovaný konektor služby RMS a zvážit, zda chcete používat protokol HTTPS pro připojení mezi tyto servery a servery, které jste právě autorizovali.

## <a name="ConfiguringConnector"></a>Konfigurace zatížení vyrovnávání a vysokou dostupnost
Po instalaci druhý nebo konečné instanci konektoru služby RMS definovat název konektoru adresa URL serveru a konfigurovat systém Vyrovnávání zatížení.

Název konektoru adresa URL serveru může být jakýkoli název v rámci oboru názvů, který ovládáte. Můžete například vytvořit položku v systému DNS pro **rmsconnector.contoso.com** a nakonfigurujte tuto položku použít IP adresu v systému Vyrovnávání zatížení. Neexistují žádné zvláštní požadavky pro tento název a není třeba konfigurovat pro samotné servery konektor. Pokud vaše servery Exchange a SharePoint se chystáte komunikovat s konektorem přes Internet, tento název nemusí vyřešit na Internetu.

> [!IMPORTANT]
> Doporučujeme neměnit tento název po konfiguraci serverů Exchange nebo SharePoint pro použití konektoru, protože je nutné tyto servery všechny konfigurace IRM zrušte zaškrtnutí a potom znovu nakonfigurovat.

Po názvu je vytvořena ve službě DNS a je nakonfigurován pro IP adresu, nakonfigurujte Vyrovnávání zatížení pro tuto adresu, která bude směrovat přenosy do konektoru serverů. Můžete použít libovolný nástroj pro vyrovnávání zatížení založené na protokolu IP pro tento účel, který obsahuje funkci Network Load Balancing (NLB) v systému Windows Server. Další informace naleznete v tématu [Průvodce nasazením Vyrovnávání zatížení](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx).

Chcete-li konfigurovat cluster vyrovnávání zatížení sítě, použijte následující nastavení:

-   Porty: 80 (pro protokol HTTP) nebo 443 (pro protokol HTTPS)

    Další informace o tom, zda je k použití protokolu HTTP nebo HTTPS naleznete v další části.

-   Spřažení: Žádná

-   Metoda distribuce: Rovná

Tento název, který definujete pro systém s vyrovnáváním zatížení (pro servery používající službu konektoru služby RMS) je název konektoru RMS vaší organizace, který budete používat později, při konfiguraci na místní servery používat Azure RMS.

## <a name="BKMK_ConfiguringHTTPS"></a>Konfigurace služby RMS konektor na používání protokolu HTTPS
> [!NOTE]
> Tento krok konfigurace je volitelná, avšak doporučená další úroveň zabezpečení.

Ačkoli použití protokolu TLS nebo SSL je volitelné pro konektor služby RMS, doporučujeme jej na jakoukoli službu citlivé na zabezpečení založené na protokolu HTTP. Tato konfigurace se ověřuje servery se spuštěnou službou konektoru na serverech Exchange a SharePoint, která používají konektor. Kromě toho je zašifrován všechna data, která je odeslána z těchto serverů s konektorem.

Chcete-li povolit konektor služby RMS na používání protokolu TLS, na každém serveru, který spouští konektor služby RMS nainstalujte certifikát ověření serveru, který obsahuje název, který bude používat pro konektor. Například, pokud název vaší RMS konektoru, které definované v DNS je **rmsconnector.contoso.com**, nasaďte certifikát ověření serveru, který obsahuje **rmsconnector.contoso.com** v předmětu certifikátu jako běžný název. Nebo zadejte **rmsconnector.contoso.com** v alternativním názvu certifikátu jako hodnota DNS. Certifikát není nutné zahrnují název serveru. Ve službě IIS, tento certifikát pak vazbu pro výchozí webový server.

Pokud použijete možnost HTTPS, ujistěte se, zda mají všechny servery, které spuštění konektoru platný server ověřování certifikátu, který je zřetězen do kořenové CA, které vaše servery Exchange a SharePoint důvěřovat. Kromě toho pokud certifikační autorita (CA), která vydala certifikáty pro servery konektor publikuje seznam odvolaných certifikátů (CRL), serverů Exchange a SharePoint musí být schopen stáhnout tento seznam odvolaných certifikátů.

> [!TIP]
> Můžete požadovat a nainstalovat certifikát ověření serveru a tento certifikát vazbu na výchozí web ve službě IIS, můžete použít následující informace a prostředky:
> 
> -   Používáte-li nasadit tyto certifikáty pro ověřování serveru služby Active Directory Certificate Services (AD CS) a certifikační autority rozlehlé sítě (CA), můžete replikovat a potom pomocí šablony certifikátu webového serveru. Tato šablona certifikátu používá **dodán v žádosti** název subjektu certifikátu, což znamená, plně kvalifikovaný název domény název konektoru služby RMS pro název subjektu certifikátu nebo alternativní název předmětu můžete zadat, když žádost o certifikát.
> -   Pokud používáte samostatné certifikační Autority nebo zakoupit tento certifikát od jiné společnosti, naleznete v části [Konfigurace certifikátů serveru Internet (IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) v [webového serveru (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) knihovna dokumentace na webu TechNet.
> -   Konfiguraci služby IIS na použití certifikátu naleznete v tématu [Přidat vazbu k serveru (IIS 7)](http://technet.microsoft.com/library/cc731692.aspx) v v [webového serveru (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) knihovna dokumentace na webu TechNet.

## <a name="BKMK_ConfiguringWebProxy"></a>Konfigurace služby RMS konektor pro webový proxy server
Pokud vaše servery konektor jsou nainstalovány v síti, která nemá přímé připojení k Internetu a vyžaduje ruční konfigurace webového proxy serveru pro odchozí přístup k Internetu, musíte nakonfigurovat v registru na tyto servery pro konektor služby RMS.

#### Ke konfiguraci konektoru služby RMS použití webového proxy serveru

1.  Na každý server spouštějící konektor služby RMS otevřete editor registru, jako je například Regedit.

2.  Přejděte do **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**

3.  Přidat hodnotu řetězce **ProxyAddress** a poté nastavte Data pro tuto hodnotu být **http://&lt;MyProxyDomainOrIPaddress&gt;:&lt;MyProxyPort&gt;**

    Příklad: **http://proxyserver.contoso.com:8080**

4.  Zavřete editor registru a restartujte server nebo proveďte příkaz IISReset restartování služby IIS.

## <a name="BKMK_InstallingStandaloneTool"></a>Instalace nástroje pro správu konektoru služby RMS na počítače pro správu
Nástroj pro správu konektoru služby RMS můžete spustit z počítače, který nemá RMS konektor nainstalován, pokud tento počítač splňuje následující požadavky:

-   Fyzický nebo virtuální počítač se systémem Windows Server 2012 nebo Windows Server 2012 R2 (všechny edice), Windows Server 2008 R2 nebo Windows Server 2008 R2 Service Pack 1 (všechny edice), Windows 8.1, Windows 8 nebo Windows 7.

-   Alespoň 1 GB paměti RAM.

-   Minimální 64 GB místa na disku.

-   Nejméně jedno síťové rozhraní.

-   Přístup k Internetu prostřednictvím brány firewall (nebo webový proxy server).

Chcete-li nainstalovat nástroj pro správu konektoru služby RMS, spusťte následující soubory:

-   32bitový počítač: RMSConnectorAdminToolSetup_x86.exe

-   Pro 64bitový počítač: RMSConnectorSetup.exe

Pokud tyto soubory nebyly staženy, můžete tak učinit z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

## <a name="ConfiguringServers"></a>Konfigurace serverů k používání konektoru služby RMS
Po instalaci a nakonfigurování konektoru služby RMS, jste připraveni ke konfiguraci vaší na místní servery, které budou používat Rights Management a připojte se k Azure RMS pomocí konektoru. To znamená, konfigurace následujících serverů:

-   Pro server Exchange 2013: Client access server a Server poštovních schránek

-   Pro systém Exchange 2010: Client access server a servery hub transport

-   Pro službu SharePoint: Webservers front-end služby SharePoint, včetně těch, který je hostitelem serveru centrální správy

-   Pro infrastrukturu klasifikace souboru: Windows Server počítače, které jste nainstalovali Správce prostředků souborového

Tato konfigurace vyžaduje nastavení registru. Chcete-li to provést, máte dvě možnosti:

|Možnost konfigurace|Výhody|Nevýhody|
|-----------------------|----------|------------|
|Automaticky pomocí nástroje Konfigurace serveru pro konektor Microsoft RMS|Žádné přímé úpravy registru. Automatizované je pro vás pomocí skriptu.<br /><br />Není nutné spustit rutiny prostředí Windows PowerShell získat adresu URL svého Microsoft RMS.<br /><br />Požadavky jsou pro vás automaticky checked (ale nebude automaticky opravují) Pokud byste ho spustit místně.|Když spustíte nástroj, je třeba připojení k serveru, který je již spuštěn konektor služby RMS.|
|Ručně pomocí úpravy registru|Žádné připojení k serveru se službou RMS konektoru je vyžadován.|Další správní režie, které jsou náchylná k chybám<br /><br />Je nutné získat vaše aplikace Microsoft RMS adresu URL, která vyžaduje spuštění příkazu prostředí Windows PowerShell.<br /><br />Je nutné vždy provést všechny požadované součásti kontroly sami.|
> [!IMPORTANT]
> V obou případech musíte ručně nainstalovat požadované součásti a konfigurace serveru Exchange, SharePoint a infrastruktury klasifikace souboru použít Rights Management.

Pro většinu organizací bude automatická konfigurace pomocí nástroje Konfigurace serveru pro konektor Microsoft RMS lepší volbou, protože poskytuje vyšší efektivitu a spolehlivost než ruční konfigurace.

Po provedení změny konfigurace na těchto serverech, musíte je restartovat, pokud mají systém Exchange nebo služby SharePoint a dříve konfigurovaná pro použití služby AD RMS. Není nutné tyto servery restartovat, pokud konfigurujete je Rights Management první. Vždy je nutné restartovat souborový server, který je konfigurován pro použití souboru klasifikace infrastruktury po provedení těchto změn konfigurace.

#### Tom, jak pomocí nástroje Konfigurace serveru pro konektor Microsoft RMS

1.  Pokud již nebyly staženy skriptu pro nástroje Konfigurace serveru pro konektor Microsoft RMS (GenConnectorConfig.ps1), ji stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=314106).

2.  Uložte soubor GenConnectorConfig.ps1 v počítači, kde jste spustili nástroj. Chcete-li spustit nástroj místně, musí se jednat serveru, který chcete konfigurovat pro komunikaci s konektorem služby RMS. Jinak můžete uložit na libovolném počítači.

3.  Rozhodněte se, jak spustit nástroj:

    -   **Místně**: Interaktivně, můžete spustit nástroj na serveru a být nakonfigurován pro komunikaci s konektorem služby RMS. To je užitečné pro jednorázová konfigurace, například testovací prostředí.

    -   **Nasazení softwaru**: Je-li spustit nástroj pro vytvoření souborů registru, které pak nasadit na jeden nebo více příslušných serverů pomocí aplikace pro správu systémů, který podporuje nasazení softwaru, jako je například System Center Configuration Manager.

    -   **Zásad skupiny**: Je-li spustit nástroj a vytvořit skript, který předat správce, který můžete vytvořit objekty zásad skupiny pro servery, které chcete konfigurovat. Tento skript vytvoří jeden objekt zásad skupiny pro každý typ server má být konfigurována, který pak může správce přiřadit odpovídající servery.

    > [!NOTE]
    > Tento nástroj lze konfigurovat servery, které budou komunikovat s konektoru služby RMS a uvedené na začátku této části. Nespouštějte tento nástroj na servery, které spouští konektor služby RMS.

4.  Spusťte prostředí Windows PowerShell s **Spustit jako správce** možnost a pomocí příkazu Get-help přečíst pokyny jak používat nástroj pro vaše metoda zvolené konfigurace:

    ```
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

Pro spuštění skriptu, musí zadejte adresu URL konektoru služby RMS vaší organizace. Zadejte název konektoru, který jste definovali ve službě DNS pro adresu s vyrovnáváním zatížení konektor nástroje a předpony protokolu (HTTP:// nebo HTTPS://). Například https://connector.contoso.com. Tento nástroj poté používá tuto adresu URL ke kontaktování servery se spuštěnou službou konektoru služby RMS a získat další parametry, které se používají k vytvoření požadované konfigurace.

> [!IMPORTANT]
> Spustíte-li tento nástroj, ujistěte se, zadejte název konektoru s vyrovnáváním zatížení služby RMS vaší organizace, a ne název jednoho serveru se spuštěnou službou konektoru služby RMS.

Konkrétní informace pro každý typ služby použijte v následujících částech:

-   [Configuring an Exchange server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ExchangeServer)

-   [Configuring a SharePoint server to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringSharePoint)

-   [Configuring a file server for File Classification Infrastructure to use the connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_FileServer)

> [!NOTE]
> Poté, co tyto servery jsou nakonfigurovány k používání konektoru, nemusí fungovat klientských aplikací, které jsou nainstalovány místně na tyto servery pomocí RMS. V takovém případě je to, protože aplikace pokusí použít konektor místo použít přímo, RMS, což není podporováno.
> 
> Kromě toho pokud Office 2010 je nainstalován místně na serveru Exchange server, funkce IRM klientskou aplikaci může být z tohoto počítače po fungovat server je nakonfigurován k používání konektoru, ale to není podporováno.
> 
> V obou případech musí nainstalovat klientské aplikace na samostatných počítačích, které nejsou nakonfigurovány k používání konektoru. Budou poté správně používat RMS přímo.

### <a name="BKMK_ExchangeServer"></a>Konfigurace serveru Exchange k používání konektoru
Následující role serveru Exchange komunikují s konektorem služby RMS:

-   Pro server Exchange 2013: Server Client access server a server poštovní schránky

-   Pro systém Exchange 2010: Server Client access server a server přenos rozbočovače

K používání konektoru služby RMS, tyto servery se systémem Exchange Server musí používat jeden z následujících verzí softwaru:

-   Exchange Server 2013 s kumulativní aktualizací 3 Exchange 2013

-   Exchange Server 2010 s kumulativní aktualizací Exchange 2010 Service Pack 3 6

Budete také muset nainstalovat na těchto serverech, na verzi klienta služby RMS, který zahrnuje podporu pro kryptografický režim 2 RMS. Minimální verze, která je podporována v systému Windows Server 2008 je zahrnuta v opravu hotfix, která si můžete stáhnout z [Délka klíče RSA je zvýšena na 2 048 bitů pro službu AD RMS v systému Windows Server 2008 R2 a Windows Server 2008](http://support.microsoft.com/kb/2627272). Minimální verze systému Windows Server 2008 R2 lze stáhnout z [Délka klíče RSA je zvýšena na 2 048 bitů pro službu AD RMS v systému Windows 7 nebo Windows Server 2008 R2](http://support.microsoft.com/kb/2627273). Windows Server 2012 a Windows Server 2012 R2 nativně podporují kryptografický režim 2.

> [!IMPORTANT]
> Pokud nejsou nainstalovány tyto verze nebo novější verze systému Exchange a klient služby RMS, nebudete moci konfigurovat Exchange k používání konektoru. Zkontrolujte, zda jsou nainstalovány tyto verze, než budete pokračovat.

##### Chcete-li konfigurovat servery Exchange k používání konektoru

1.  Na role serveru Exchange, které komunikují pomocí konektoru služby RMS proveďte jednu z následujících akcí:

    -   Server spusťte nástroj konfigurace pro konektor Microsoft RMS. Další informace naleznete v tématu [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) v tomto tématu.

        Chcete-li například spustit nástroj místně a konfigurace serveru se systémem Exchange 2013:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013
        ```

    -   Proveďte ruční registru úpravy pomocí tabulek v následujících částech ručně přidat nastavení registru na serverech.

2.  Povolte funkci IRM v systému Exchange. Další informace naleznete v tématu [informace Rights Management postupy](https://technet.microsoft.com/library/dd351212%28v=exchg.150%29.aspx) v knihovně serveru Exchange.

Tabulky v následujících částech použijte, pouze pokud chcete ručně přidat nebo zkontrolovat nastavení registru na těchto serverech, které lze konfigurovat servery, které chcete použít konektor služby RMS. Pokyny pro při použití těchto tabulek:

-   *MicrosoftRMSURL* je adresa URL služby Microsoft RMS vaší organizace. Chcete-li najít tuto hodnotu:

    1.  Spuštění [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) rutiny pro Azure RMS. Pokud jste ještě nenainstalovali modul prostředí Windows PowerShell pro službu Azure RMS, naleznete v části [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

    2.  Z výstupu, určete **LicensingIntranetDistributionPointUrl** hodnotu.

        Příklad: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Od hodnoty, odeberte **/_wmcs/licensing** z tohoto řetězce. Zbývající řetězec je adresa URL aplikace Microsoft RMS. V našem příkladu adresu URL aplikace Microsoft RMS by byl následující hodnotu:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.RMS.na.aadrm.com**

-   *ConnectorFQDN* je název služby Vyrovnávání zatížení, který jste definovali ve službě DNS pro konektor. Například **rmsconnector.contoso.com**.

-   Použijte předponu HTTPS pro adresu URL konektor, pokud jste nakonfigurovali konektor na používání HTTPS ke komunikaci se na místní servery. Další informace naleznete v tématu [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) v tomto tématu. Adresy URL služby RMS Microsoft vždy používat protokol HTTPS.

#### Tabulku pro nastavení registru serveru Exchange 2013

|Cesta v registru|Typ|Hodnota|Data|
|--------------------|-------|-----------|--------|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation|REG_SZ|Výchozí|https://*MicrosoftRMSURL/_wmcs/certification*|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|REG_SZ|Výchozí|https://MicrosoftRMSURL/_wmcs/licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection|REG_SZ|https://*MicrosoftRMSURL*|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze systému Exchange server do konektoru služby RMS:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|REG_SZ|https://*MicrosoftRMSURL*|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze systému Exchange server do konektoru služby RMS:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|

#### Tabulku pro nastavení registru Exchange 2010

|Cesta v registru|Typ|Hodnota|Data|
|--------------------|-------|-----------|--------|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation|REG_SZ|Výchozí|https://*MicrosoftRMSURL*/_wmcs/certification|
|HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|REG_SZ|Výchozí|https://*MicrosoftRMSURL*/_wmcs/Licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection|REG_SZ|https://*MicrosoftRMSURL*|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze systému Exchange server do konektoru služby RMS:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|REG_SZ|https://*MicrosoftRMSURL*|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze systému Exchange server do konektoru služby RMS:<br /><br />-   http://*ConnectorFQDN*<br />-   https://*ConnectorFQDN*|

### <a name="BKMK_ConfiguringSharePoint"></a>Konfigurace serveru služby SharePoint k používání konektoru
Následující role SharePoint komunikují s konektorem služby RMS:

-   Webservers front-end služby SharePoint, včetně těch, který je hostitelem serveru centrální správy

K používání konektoru služby RMS, tyto servery se systémem SharePoint musí používat jeden z následujících verzí softwaru:

-   SharePoint Server 2013

-   SharePoint Server 2010

Server SharePoint 2013 musí být také spuštěná verze klienta MSIPC 2.1, který je from1.0.622.34 prostřednictvím 1.0.10907.0.

> [!WARNING]
> Existuje více verzích klienta MSIPC 2.1, takže Zkontrolujte instalaci verze odkazuje v tomto článku.
> 
> Verze klienta můžete ověřit kontrolou číslo verze MSIPC.dll, který je umístěn ve **\Program Files\Active Directory Rights Management Services Client 2.1**. Dialogové okno Vlastnosti se zobrazuje číslo verze klienta MSIPC 2.1.

Tyto servery se systémem SharePoint 2010 musí mít nainstalovanou verzi MSDRM klienta, který zahrnuje podporu pro kryptografický režim 2 RMS. Minimální verze, která je podporována v systému Windows Server 2008 je zahrnuta v opravu hotfix, která si můžete stáhnout z [Délka klíče RSA je zvýšena na 2 048 bitů pro službu AD RMS v systému Windows Server 2008 R2 a Windows Server 2008](http://support.microsoft.com/kb/2627272), a minimální verze systému Windows Server 2008 R2 lze stáhnout z [Délka klíče RSA je zvýšena na 2 048 bitů pro službu AD RMS v systému Windows 7 nebo Windows Server 2008 R2](http://support.microsoft.com/kb/2627273). Windows Server 2012 a Windows Server 2012 R2 nativně podporují kryptografický režim 2.

##### Ke konfiguraci serverů služby SharePoint k používání konektoru

1.  Na serverech SharePoint, které komunikují pomocí konektoru služby RMS proveďte jednu z následujících akcí:

    -   Server spusťte nástroj konfigurace pro konektor Microsoft RMS. Další informace naleznete v tématu [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) v tomto tématu.

        Chcete-li například spustit nástroj místně na server se službou SharePoint 2013 konfigurovat:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013
        ```

    -   Pokud používáte SharePoint 2013, proveďte ruční registru úpravy pomocí tabulky v následující části ručně přidat nastavení registru na serverech.

2.  Povolte IRM ve službě SharePoint. Další informace naleznete v tématu [Konfigurovat správu přístupových práv (SharePoint Server 2010)](https://technet.microsoft.com/library/hh545607%28v=office.14%29.aspx) v knihovně služby SharePoint.

    Pokud budete postupovat podle těchto pokynů, je nutné nakonfigurovat služby SharePoint k používání konektoru zadáním **použít tento server RMS**, a pak zadejte URL konektor služby Vyrovnávání zatížení, kterou jste nakonfigurovali. Zadejte název konektoru, který jste definovali ve službě DNS pro adresu s vyrovnáváním zatížení konektor nástroje a předpony protokolu (HTTP:// nebo HTTPS://). Například pokud je název konektoru https://connector.contoso.com, konfigurace bude vypadat jako na následujícím obrázku:

    ![](../Image/AzRMS_SharePointConnector.png)

    Po povolení správy Přístupových práv na farmu služby SharePoint, můžete povolit IRM na jednotlivých knihoven pomocí **informace Rights Management** možnost na **Nastavení knihovny** stránky pro každou knihoven.

    > [!IMPORTANT]
    > Pro službu SharePoint pro přístup k serveru RMS pomocí konektoru je nutné autorizovat odpovídající účty nástroje pro správu konektoru služby RMS. Pokud jste tak dosud neučinili, naleznete v části [Authorizing servers to use the RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#AuthorizingServers) v tomto tématu.

V následující části pomocí tabulky, pouze pokud chcete ručně přidat nebo zkontrolovat nastavení registru na serveru se systémem SharePoint 2013.

#### Tabulka pro SharePoint 2013 nastavení registru
Pokyny pro při použití této tabulce:

-   *MicrosoftRMSURL* je adresa URL služby Microsoft RMS vaší organizace. Chcete-li najít tuto hodnotu:

    1.  Spuštění [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) rutiny pro Azure RMS. Pokud jste ještě nenainstalovali modul prostředí Windows PowerShell pro službu Azure RMS, naleznete v části [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

    2.  Z výstupu, určete **LicensingIntranetDistributionPointUrl** hodnotu.

        Příklad: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Od hodnoty, odeberte **/_wmcs/licensing** z tohoto řetězce. Zbývající řetězec je adresa URL aplikace Microsoft RMS. V našem příkladu adresu URL aplikace Microsoft RMS by byl následující hodnotu:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.RMS.na.aadrm.com**

-   *ConnectorFQDN* je název služby Vyrovnávání zatížení, který jste definovali ve službě DNS pro konektor. Například **rmsconnector.contoso.com**.

-   Použijte předponu HTTPS pro adresu URL konektor, pokud jste nakonfigurovali konektor na používání HTTPS ke komunikaci se na místní servery. Další informace naleznete v tématu [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) v tomto tématu. Adresy URL služby RMS Microsoft vždy používat protokol HTTPS.

|Cesta v registru|Typ|Hodnota|Data|
|--------------------|-------|-----------|--------|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection|REG_SZ|https://*MicrosoftRMSURL*/_wmcs/licensing|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze serveru služby SharePoint do konektoru služby RMS:<br /><br />-   http://*ConnectorFQDN*/_wmcs/licensing<br />-   https://*ConnectorFQDN*/_wmcs/licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification|REG_SZ|Výchozí|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze serveru služby SharePoint do konektoru služby RMS:<br /><br />-   http://*ConnectorFQDN*/_wmcs/certification<br />-   https://*ConnectorFQDN*/_wmcs/certification|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing|REG_SZ|Výchozí|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze serveru služby SharePoint do konektoru služby RMS:<br /><br />-   http://*ConnectorFQDN*/_wmcs/licensing<br />-   https://*ConnectorFQDN*/_wmcs/licensing|

### <a name="BKMK_FileServer"></a>Konfigurace souborového serveru pro soubor klasifikace infrastrukturu k používání konektoru
Chcete-li chránit dokumenty sady Office pomocí konektoru služby RMS a soubor klasifikace infrastruktury, souborový server musí používat jeden z následujících operačních systémů:

-   Windows Server 2012 R2

-   Windows Server 2012

##### Konfigurace souborové servery k používání konektoru

1.  Na souborových serverech nakonfigurovaná pro klasifikaci infrastruktury souboru a že budou komunikovat s konektorem služby RMS, proveďte jednu z následujících akcí:

    -   Server spusťte nástroj konfigurace pro konektor Microsoft RMS. Další informace naleznete v tématu [How to use the server configuration tool for Microsoft RMS connector](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_HowToRunTheTool) v tomto tématu.

        Chcete-li například spustit nástroj místně a konfigurovat souborový server s FCI:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012
        ```

    -   Proveďte ruční registru úpravy pomocí tabulky v následující části ručně přidat nastavení registru na serverech.

2.  Vytvořit klasifikace pravidla a úlohy správy souborů k ochraně dokumentů s šifrování služby RMS a pak zadejte šablonu služby RMS automaticky uplatnit zásady RMS. Další informace naleznete v tématu [Přehled Správce prostředků souborového serveru](http://technet.microsoft.com/library/hh831701.aspx) v knihovně dokumentace k systému Windows Server.

Pouze v případě, že chcete ručně přidat nebo zkontrolovat nastavení registru na souborový server, který využívá infrastrukturu klasifikace soubor chránit dokumenty pomocí tabulky v následující části.

#### Tabulka pro souborový server a nastavení registru souboru klasifikace infrastruktury
Pokyny pro při použití této tabulce:

-   *ConnectorFQDN* je název služby Vyrovnávání zatížení, který jste definovali ve službě DNS pro konektor. Například **rmsconnector.contoso.com**.

-   Použijte předponu HTTPS pro adresu URL konektor, pokud jste nakonfigurovali konektor na používání HTTPS ke komunikaci se na místní servery. Další informace naleznete v tématu [Configuring the RMS connector to use HTTPS](../Topic/Deploying_the_Azure_Rights_Management_Connector.md#BKMK_ConfiguringHTTPS) v tomto tématu. Adresy URL služby RMS Microsoft vždy používat protokol HTTPS.

|Cesta v registru|Typ|Hodnota|Data|
|--------------------|-------|-----------|--------|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing|REG_SZ|Výchozí|http://*ConnectorFQDN*/_wmcs/licensing|
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation|REG_SZ|Výchozí|http://*ConnectorFQDN*/_wmcs/certification|

## <a name="BKMK_NextSteps"></a>Další kroky
Nyní, je nainstalován a nakonfigurován konektor služby RMS a vaše servery jsou nakonfigurovány pro použití ji, správci IT a uživatelé může chránit a využívat e-mailové zprávy a dokumenty pomocí Azure RMS. Chcete-li to snadné pro uživatele, nasaďte aplikaci, která nainstaluje doplněk pro sadu Office a přidává nové možnosti klikněte pravým tlačítkem do Průzkumníka souborů sdílení RMS. Další informace naleznete v tématu [Příručka správce aplikace pro sdílení obsahu Rights Management](http://technet.microsoft.com/library/%20dn339003%28v=ws.10%29.aspx).

Kromě toho můžete zvážit následující vám pomohou monitorovat konektor služby RMS a využití vaší organizace Azure RMS:

-   Vestavěné **Konektor Microsoft Rights Management** čítače výkonu.

-   [Nástroj Analyzátor RMS](https://www.microsoft.com/en-us/download/details.aspx?id=46437), pomocí možnosti RMS konektor vám pomohou sledovat stav konektoru a identifikovat problémy s konfigurací.

-   [Protokolování a analýza využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md)

Můžete použít [Plán nasazení Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) Zkontrolovat, zda jsou ostatní kroky konfigurace, které chcete provést předtím, než můžete přejít na [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] uživatelům a správcům. Pokud neexistují žádné další kroky konfigurace, které je třeba provést, naleznete v části [Použití služby Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) provozní pokyny pro podporu úspěšné nasazení pro vaši organizaci.

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

