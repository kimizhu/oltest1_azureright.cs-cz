---
description: na
keywords: na
title: Requirements for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Požadavky pro Azure Rights Management
K nasazení aplikace Microsoft Azure Rights Management (Azure RMS) ve vaší organizaci, ujistěte se, že máte následující požadavky. Pak můžete použít [Plán nasazení Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) nasazení Rights Management pro vaši organizaci.

|Požadavek|Další informace|
|-------------|-------------------|
|Odběr cloudu pro server RMS|Vaše organizace musí mít cloudu odběr, který podporuje službu RMS.<br /><br />Informace o licencích, naleznete v části [Cloud odběry, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) v tomto tématu.|
|Adresář Azure AD|Vaše organizace musí mít adresáři služby Azure AD pro podporu ověření uživatele pro službu RMS. Kromě toho pokud chcete použít vaše uživatelské účty z vaší místní služby directory (AD DS), je nutné také nakonfigurovat Integrace adresářové.<br /><br />Vícefaktorového ověřování (MFA) je podporován službou Azure RMS, pokud máte požadovaný klientský software a správně nakonfigurovaná podpůrná infrastruktura vícefaktorového ověřování.<br /><br />Další informace naleznete v tématu [Adresář Azure AD](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_AzureADTenant) v tomto tématu.|
|Klientská zařízení|Uživatelé musí mít zařízení klienta (počítače nebo mobilního zařízení), která spouštějí operační systém podporující RMS.<br /><br />Další informace naleznete v tématu [Klientská zařízení, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) v tomto tématu.|
|Aplikace|Uživatelé musí spouštět aplikace, které podporují služby RMS.<br /><br />Další informace naleznete v tématu [Aplikace, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) v tomto tématu.|
|Infrastrukturu, která podporuje připojení k Internetu a závislých cloudových služeb|Pokud máte bránu firewall nebo podobné zasahující síťová zařízení, které musí být nakonfigurován na povolit konkrétní připojení naleznete v tématu [rozsahů adres IP a adres URL 356 Office](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Seznam adres URL a IP adresy ve **Office 356 portálu a identity** část vztahuje na portálu Office 365, prostředků Azure Active Directory a Azure Rights Management. Postupujte podle pokynů v tomto článku k udržování aktuálnosti pomocí změny k těmto informacím přihlášením odběru informačního kanálu RSS.<br /><br />Kromě informací v článku Office specifické pro službu Azure RMS:<br /><br />-   Připojení klienta služby TLS (např. Chcete-li provést kontrolu úrovni paketů) není ukončit. Tím dojde k narušení certifikát přídavné, že RMS klienti používat s certifikačními autoritami spravované Microsoft k zabezpečení jejich komunikace s Azure RMS.<br />-   Nepoužívejte konfigurace webového proxy serveru, který ověřuje jménem uživatele.|

Pokud chcete pomocí Azure RMS na místní servery, jsou podporovány následující produkty:

-   Exchange Server

-   SharePoint Server

-   Windows Server souborové servery, které podporují infrastrukturu klasifikace souboru

Informace o požadavcích na další Azure RMS v tomto scénáři naleznete v tématu [Na místní servery, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedServers) v tomto tématu.

> [!IMPORTANT]
> Následující scénář nasazení není podporován:
> 
> -   Spuštění služby AD RMS a Azure RMS side-by-side ve stejné organizaci, s výjimkou během migrace, jak je popsáno v [Migrace ze služby AD RMS na Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).
> 
> Neexistuje cesta podporovaných migračních [ze služby AD RMS na službu Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx), a z [Azure RMS na službu AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Pokud nasazení Azure RMS a rozhodněte se, že již nechcete používání této cloudové služby naleznete v tématu [Vyřazování z provozu a deaktivace Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Další informace o požadavcích na Azure RMS pomocí následujících částí.

## <a name="BKMK_SupportedSubscriptions"></a>Cloud odběry, které podporují službu Azure RMS
Pokud chcete používat Azure RMS, vaše organizace musí mít alespoň jeden z následujících předplatná s dostatečný počet licencí pro uživatele a služby, které bude chránit soubory a e-mailové zprávy. Pokud používáte službu, která bude platit ochrana pro uživatele (vlastníci souborů nebo e-mailové zprávy), tito uživatelé vyžadují jednu z těchto licencí. Uživatelé, kteří pouze spotřebuje (například číst a upravovat) této chráněných dat není nutné licenci.

-   Office 365

-   Azure Rights Management Premium (dříve Azure RMS samostatný)

-   Sada Enterprise Mobility

-   RMS pro jednotlivce

Pomocí následujících částí Další informace a možnosti přihlášení.

Licencování porovnání Azure RMS funkcionality placené předplatné, naleznete v části [Rights Management Services (RMS)-porovnání nabídek](http://technet.microsoft.com/dn858608).

### Předplatné pro Office 365
[Bezplatné 30denní zkušební verze: Enterprise E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

Tento odběr je určen pro organizace, kteří chtějí používat služby Office online a používat jejich funkce správy práv, který používá Azure RMS. Ne všechny odběry Office 365 však zahrnovat Azure RMS.

|Volby správy licencí|Office 365 obchodní Essentials|Office 365 obchodní Premium|Office 365 Enterprise E1<br /><br />A1 vzdělávání Office 365|Office 365 Enterprise E3<br /><br />A3 vzdělávání Office 365<br /><br />Státní G3 Office 365|Office 365 Enterprise E4<br /><br />A4 vzdělávání Office 365<br /><br />Státní G4 Office 365|Office 365 Enterprise K1|Plán SharePoint 1<br />SharePoint plánu 2|Exchange Online plán 1<br />Exchange Online plánu 2|
|------------------------|----------------------------------|-------------------------------|--------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------------------------------------------------------|----------------------------|-----------------------------------------|---------------------------------------------------|
|Informace o ochrany práv (k informacím IRM)|Ne|Ne|Ne|Ano|Ano|Ne|Ne|Ne|

### Předplatné Azure Rights Management Premium
[Bezplatné 30denní zkušební verze](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

Toto předplatné byla dříve označována jako samostatný Azure RMS a je určena pro organizace, které chcete použít Azure RMS, ale nemáte předplatné, které obsahuje Azure RMS. Například, pokud máte předplatné pro Office 365 obchodní Essentials nebo Office 365 Enterprise E1, tyto odběry nezahrnujte Azure RMS (viz tabulka v předchozím oddílu). Pomocí Azure RMS, vám může Zakupte si předplatné Azure Rights Management Premium (nebo zakoupit další předplatné, jako je Office 365 Enterprise E4, která zahrnuje Azure RMS).

Další informace naleznete v tématu [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management).

Toto předplatné nabízí také na zkušební dobu můžete vyzkoušet Azure RMS pro 25 uživatelů zdarma. Pokud předplatné vyprší Zakupte si předplatné nahrazení, naleznete v následující části "co se stane, když vyprší platnost zkušební předplatné?"

|Volby správy licencí|Office 365 obchodní Essentials|Office 365 obchodní Premium|Office 365 Enterprise E1<br /><br />A1 vzdělávání Office 365|Office 365 Enterprise E3<br /><br />A3 vzdělávání Office 365<br /><br />Státní G3 Office 365|Office 365 Enterprise E4<br /><br />A4 vzdělávání Office 365<br /><br />Státní G4 Office 365|Office 365 Enterprise K1|Plán SharePoint 1<br />SharePoint plánu 2|Exchange Online plán 1<br />Exchange Online plánu 2|
|------------------------|----------------------------------|-------------------------------|--------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------------------------------------------------------|----------------------------|-----------------------------------------|---------------------------------------------------|
|Informace o ochrany práv (k informacím IRM)|Ano|Yes <sup>1</sup>|Ano|Ano|Ano|Ano|Ano|Ano|
<sup>1</sup> obchodní Premium, jsou některá omezení klienta: Můžete chránit obsah a využívat obsah chráněný službou RMS pomocí aplikace Outlook Web App a aplikace sdílení RMS. Využívají chráněný obsah pomocí všech aplikací, které zahrnuje Office Online a klientských aplikací pro Office 365 obchodní Premium.

#### <a name="BKMK_TrialExpiryBehavior"></a>Co se stane, když vyprší platnost zkušební předplatné?
Pokud vaše zkušební předplatné vyprší, ztratí přístup k obsahu, který byl chráněn pomocí zkušebního předplatného pro Azure RMS. Nicméně pokud si pak koupíte odběr, který podporuje Azure RMS, přístup, je automaticky obnovena.

Výjimka ztrátě přístupu po uplynutí doby je, pokud vaše organizace používat Azure RMS pro RMS pro jednotlivce předplatné před získat zkušební předplatné. Poté přístup k dříve chráněný obsah zůstane, i když vyprší platnost zkušební předplatné.

### Sada Enterprise Mobility předplatného
[Bezplatné 30denní zkušební verze](http://go.microsoft.com/fwlink/?LinkId=615385)

Toto předplatné je určený pro organizace, kteří chtějí používat kombinací Azure Active Directory Premium, Windows Intune a Azure Rights Management. Další informace naleznete v tématu [Microsoft Enterprise Mobility přehled](http://go.microsoft.com/fwlink/?LinkId=615386).

|Volby správy licencí|Office 365 obchodní Essentials|Office 365 obchodní Premium|Office 365 Enterprise E1<br /><br />A1 vzdělávání Office 365|Office 365 Enterprise E3<br /><br />A3 vzdělávání Office 365<br /><br />Státní G3 Office 365|Office 365 Enterprise E4<br /><br />A4 vzdělávání Office 365<br /><br />Státní G4 Office 365|Office 365 Enterprise K1|Plán SharePoint 1<br />SharePoint plánu 2|Exchange Online plán 1<br />Exchange Online plánu 2|
|------------------------|----------------------------------|-------------------------------|--------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------------------------------------------------------|----------------------------|-----------------------------------------|---------------------------------------------------|
|Informace o ochrany práv (k informacím IRM)|Ano|Yes <sup>1</sup>|Ano|Ano|Ano|Ano|Ano|Ano|
<sup>1</sup> obchodní Premium, jsou některá omezení klienta: Můžete chránit obsah a využívat obsah chráněný službou RMS pomocí aplikace Outlook Web App a aplikace sdílení RMS. Využívají chráněný obsah pomocí všech aplikací, které zahrnuje Office Online a klientských aplikací pro Office 365 obchodní Premium.

### RMS pro jednotlivce předplatné
Tento odběr je určen pro jednotlivce v organizaci, která nebyla nasazena Azure RMS nebo AD RMS. Umožňuje, aby tito lidé číst obsah, který je chráněn v organizaci, která používá Azure RMS a může také chránit své vlastní obsah.

Další informace naleznete v tématu [RMS pro jednotlivce i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## <a name="BKMK_AzureADTenant"></a>Adresář Azure AD
Musí mít adresáři služby Azure AD používat Azure RMS. Váš účet organizace pro tento adresář je použít pro přihlášení k portálu Azure Management Portal, kde, například můžete konfigurovat a spravovat šablony Rights Management.

Pokud již jste předplatné Azure pro vaši organizaci, můžete získat po přihlášení se k bezplatné zkušební verze.: Přejděte na stránku [Azure získat spuštěna](https://account.windowsazure.com/organization) stránce a postupujte podle pokynů.

Další informace naleznete v následujících zdrojích v dokumentaci k Azure Active Directory:

-   [Co je adresář služby Azure AD?](http://msdn.microsoft.com/en-us/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Jak předplatná Azure, které jsou spojeny s Azure AD](http://msdn.microsoft.com/en-us/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Pokud chcete integrovat do vašeho místního adresáře Azure AD najdete v části doménových struktur služby AD, [Integrace Directory](http://msdn.microsoft.com/en-us/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8).

> [!NOTE]
> Pokud máte mobilní zařízení nebo místní ověřování pomocí služby AD FS nebo zprostředkovatel ekvivalentní ověřování počítačů se systémem Mac:
> 
> -   Je nutné použít službu AD FS na server minimální verzi **Windows Server 2012 R2**, nebo zprostředkovatel alternativní ověřování, který podporuje protokol OAuth 2.0.

### <a name="BKMK_MFA"></a>Vícefaktorového ověřování (MFA) a Azure RMS
Použití vícefaktorového ověřování (MFA) s Azure RMS vyžaduje alespoň jeden z následujících akcí:

-   Office 2013 (minimální verze):

    -   Pokud máte Office 2013, je také nutné nainstalovat [9. června 2015 aktualizace pro Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). Další informace o této aktualizaci a o moderní ověřování přináší na základě Active Directory ověřování knihovnu ADAL znak Office 2013, najdete v části [Office 2013 moderní ověřování public preview oznamují](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)  na blogu Office.

-   Sdílení obsahu Rights Management aplikace pro Windows:

    -   Minimální verze 1.0.1908.0, což může být potvrzen pomocí ovládacích panelů, programy a funkce musí mít nainstalován. Další informace o aplikaci pro sdílení obsahu naleznete v tématu  [Sdílení obsahu aplikace pro systém Windows Rights Management](../Topic/Rights_Management_Sharing_Application_for_Windows.md).

-   Sdílení obsahu Rights Management aplikace pro mobilní zařízení a počítačů se systémem Mac:

    -   Ujistěte se, že máte nejnovější nainstalovaná verze. Podpora vícefaktorového ověřování přešel do září 2015 vydání aplikace sdílení RMS.

Poté nakonfigurujte řešení vícefaktorového ověřování:

-   Pro spravované Microsoft klienty (máte Azure Active Directory nebo Office 365):

    -   Konfigurace vícefaktorového ověřování Azure k vynucení vícefaktorového ověřování pro uživatele. Pokyny naleznete v tématu [Začínáme s Azure Multi-Factor Authentication v cloudu](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/) z Azure dokumentace.

        Další informace o Azure vícefaktorového ověřování najdete v části [Co je Azure Multi-Factor Authentication?](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)

-   Pro federované klienty (provozujete federační servery místně):

    -   Konfigurace federační servery pro Azure Active Directory nebo Office 365. Například pokud používáte službu AD FS, přečtěte si téma [konfigurovat další metody ověřování pro AD FS](https://technet.microsoft.com/library/dn758113.aspx) na webu TechNet.

        Další informace o tomto scénáři naleznete v tématu  [The funguje s Office 365 – Identity program teď zjednoduší,](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) na blogu Office.

## <a name="BKMK_SupportedDevices"></a>Klientská zařízení, které podporují službu Azure RMS
Pomocí následujících částí k identifikaci zařízení, která podporují Azure Rights Management (RMS) a které funkce RMS podporují:

-   [Počítače](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedComputers)

-   [Mobilní zařízení](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedMobileDevices)

-   [Možnosti zařízení klienta](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>Počítače
Následující operační systémy počítače podporují Azure Rights Management:

-   **Windows 7** (x 86, x 64)

-   **Windows 8** (x 86, x 64)

-   **Windows 8.1** (x 86, x 64)

-   **Windows 10** (x 86, x 64)

-   **Systému Mac OS X**: Minimální verze systému Mac OS X 10.8 (Horská Lion)

### <a name="BKMK_RMSSupportedMobileDevices"></a>Mobilní zařízení
Následující operační systémy mobilních zařízení podporují Azure Rights Management:

-   **Windows Phone**: Windows Phone 8.1

-   **Android telefonů a tabletů**: Minimální verze Android 4.0.3

-   **iPhone a iPad**: Minimální verze iOS 7.0

-   **Tablety, Windows RT**: Windows 8 RT, Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>Možnosti zařízení klienta
Ne všechny podporované klientské zařízení aktuálně podporují všechny možnosti RMS. Následující tabulku použijte k určení, které aplikace podporují možnosti RMS a výjimky.

Pokud není uvedeno jinak, platí podporované možnosti pro Azure RMS a AD RMS. Kromě toho podpora služby AD RMS na iOS, Android, OS X a Windows Phone 8.1 vyžaduje [rozšíření Active Directory Rights Management služby mobilní zařízení](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341).

Informace o sloupcích tabulky:

-   **Chráněný PDF**: Soubory, které mají příponu názvu souboru .ppdf a která jsou vytvořena automaticky při použití aplikace sdílení RMS sdílet Office soubory a soubory PDF e-mailem. Aplikace sdílení RMS zahrnuje čtečky pro chráněné soubory PDF. Dříve Pokud jste vytvořili soubory PDF, které chráněné pomocí Azure RMS nebo AD RMS, můžete ke čtení těchto souborů v systému Windows, iOS a zařízení se systémem Android pomocí čtečky Foxit a Nitro Pro.

-   **E-mailu:** E-mailoví klienti uvedené může chránit e-mailové zprávy, samotného, která bude automaticky chránit všechny připojené soubory. V tomto scénáři funkce Náhled klienta zobrazit chráněný obsah (zprávu a přílohy) pro oprávnění příjemci. Pokud e-mailové zprávy, sama není chráněný, ale chráněná příloha, nelze zobrazit funkce Náhled klienta však chráněná příloha autorizovaný příjemcům.

-   **Jiných typů souborů**: Textové a obrázkové soubory obsahovat soubory, které mají příponu názvu souboru, jako je například TXT, XML, JPG, jpeg .a. Tyto soubory změnit přípony názvu souboru po jsou nativně chráněný službou RMS a jen pro čtení. Soubory, které se nedají nativně chránit mít příponu názvu souboru .pfile po obecně chráněné službou RMS. Další informace naleznete v tématu [úrovně ochrany – nativní a Obecné](https://technet.microsoft.com/library/dn339003.aspx) a [podporované typy souborů a přípony názvů souborů](https://technet.microsoft.com/library/dn339003.aspx) částech z [Příručka správce aplikace pro sdílení obsahu Rights Management](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx).

|**Operační systém zařízení**|Aplikace Word, Excel, PowerPoint|Chráněný PDF|E-mailu|Jiné typy souborů|
|--------------------------------|------------------------------------|----------------|-----------|---------------------|
|**Systém Windows**|Office 2010<br /><br />Office 2013<br /><br />Mobilní aplikace Office (pouze Azure RMS)<sup>1</sup><br /><br />Office Online<sup>2</sup>|Gaaiho Doc<br /><br />GigaTrust Desktop Client PDF pro Adobe<br /><br />Čtečky Foxit<br /><br />Čtení souborů PDF nitro<br /><br />Aplikace sdílení RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Outlook Web App (OWA)<br /><br />Program Windows Mail<sup>3</sup>|Aplikace sdílení RMS pro Windows: Text, obrázky, pfile<br /><br />Siemens JT2Go: JT soubory (jenom Windows 10)|
|**iOS**|Office pro iPad a iPhone<sup>4</sup><br /><br />Office Online<sup>2</sup><br /><br />TITUS dokumenty|Čtečky Foxit<br /><br />Aplikace sdílení RMS<sup>1</sup><br /><br />TITUS dokumenty|NitroDesk<br /><br />Aplikace Outlook pro iPad a iPhone<sup>3</sup><br /><br />Aplikace OWA pro iOS<br /><br />Secure IQProtector ostrovy<sup>1</sup><br /><br />TITUS pošty|Aplikace sdílení RMS<sup>1</sup>: Text, obrázky, pfile<br /><br />TITUS dokumenty: Pfile|
|**Android**|GigaTrust aplikace pro Android<br /><br />Office Online<sup>2</sup>|GigaTrust aplikace pro Android<br /><br />Čtečky Foxit<br /><br />Aplikace sdílení RMS<sup>1</sup>|9Folders<br /><br />GigaTrust aplikace pro Android<br /><br />NitroDesk<br /><br />Aplikace OWA pro Android<sup>5</sup><br /><br />E-mailu Samsung (S3 a novější)<br /><br />Secure IQProtector ostrovy<sup>1</sup><br /><br />Klasifikace TITUS pro mobilní zařízení|Aplikace sdílení RMS<sup>1</sup>: Text, obrázky, pfile|
|**OS X**|Office 2011 (pouze služby AD RMS)<br /><br />2016 Office for Mac<br /><br />Office Online<sup>2</sup>|Čtečky Foxit<br /><br />Aplikace sdílení RMS<sup>1</sup>|Aplikace Outlook 2011 (pouze služby AD RMS)<br /><br />2016 aplikace Outlook pro počítače Mac<br /><br />Aplikace Outlook pro počítače Mac|Aplikace sdílení RMS<sup>1</sup>: Text, obrázky, pfile|
|**Windows RT**|Office 2013 RT<br /><br />Office Online<sup>2</sup>|Není podporované|Aplikace Outlook 2013 RT<br /><br />Aplikace pošta pro Windows<br /><br />Program Windows Mail<sup>3</sup>|Siemens JT2Go: JT soubory|
|**Windows Phone 8.1**|Office Mobile (AD RMS pouze)|Aplikace sdílení RMS<sup>1</sup>|Mobilní aplikace Outlook|Aplikace sdílení RMS<sup>1</sup>: Text, obrázky, pfile|
|**BlackBerry 10**|Není podporované|Není podporované|E-mailu BlackBerry<sup>3</sup>|Není podporované|
<sup>1</sup> podporuje zobrazení chráněného obsahu.

<sup>2</sup> podporuje zobrazení chráněného obsahu v SharePoint Online, OneDrive pro firmy a aplikace Outlook Web Access.

<sup>3</sup> používá Exchange ActiveSync IRM, který musí být povolen správcem serveru Exchange. Uživatelé mohou zobrazit, odpovědět a odpovědět, že všechny chráněné e-mailové zprávy, ale uživatelé nemůže chránit nové e-mailové zprávy, sami.

<sup>4</sup> podporuje prohlížení a úpravám chráněné dokumenty. Další informace najdete v následujících příspěvku na blogu Office: [Podporu systému Azure Rights Management je teď k dispozici Office pro iPad a iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<sup>5</sup> Další informace najdete v následujících příspěvku na blogu Office: [Aplikace OWA pro Android teď dostupná na zařízeních, vyberte možnost](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> Další informace o nadcházející podpora služby RMS v sadě Office pro různé platformy najdete v následujících příspěvku z blogu Office: [Všude, Office všude, kde šifrování](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>Aplikace, které podporují službu Azure RMS
Následující aplikace nativně podporují Azure RMS, což znamená, že RMS je úzce integrována do těchto aplikací pomocí rozhraní API služby RMS pro podporu omezení použití. Tyto aplikace jsou označovány také jako podporující RMS:

-   **Aplikace Microsoft Office** (Word, Excel, PowerPoint a Outlook) z následujících sad můžete chránit obsah pomocí Azure RMS:

    -   Office 365 ProPlus

    -   Office 365 Enterprise E3

    -   Office 365 Enterprise E4

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Jiné edice sady Office (s výjimkou Office 2007) můžete využívají chráněný obsah.

    > [!NOTE]
    > Azure RMS s Office Professional Plus 2010 nebo Office Professional 2010:
    > 
    > -   Vyžaduje aplikace pro systém Windows pro sdílení obsahu Rights Management
    > -   Nepodporované ve Windows 10

-   **Aplikace pro systém Windows pro sdílení obsahu Rights Management**

    Další informace o aplikace pro sdílení obsahu Rights Management pro Windows naleznete v následujících zdrojích:

    -   [Rights Management příručka aplikace pro sdílení správce](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Sdílení aplikace uživatelská příručka Rights Management](http://technet.microsoft.com/library/dn339006.aspx)

-   **Aplikace pro mobilní platformy pro sdílení obsahu Rights Management**

    Další informace o aplikace pro sdílení obsahu Rights Management pro mobilní platformy naleznete v následujících zdrojích:

    -   Stáhnout relevantní aplikaci pomocí odkazů na [stránky Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

    -   Pokud spravujete mobilní zařízení pomocí Microsoft Intune, můžete nasadit a nakonfigurovat aplikaci na [iOS a zařízení se systémem Android jako zásady spravované aplikace](https://technet.microsoft.com/library/dn878026.aspx).

    -   [Nejčastější dotazy k používání aplikace pro mobilní platformy pro sdílení obsahu Microsoft Rights Management](http://technet.microsoft.com/dn451248)

-   **Jiné aplikace, které podporují rozhraní API služby RMS**:

    -   Obchodní aplikace, které jsou zapsány interně pomocí RMS SDK

    -   Aplikace od dodavatelů softwaru, které jsou zapsány pomocí RMS SDK

    Další informace o sadě SDK naleznete v tématu [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

> [!IMPORTANT]
> Následující aplikace nejsou aktuálně podporovány službou Azure RMS:
> 
> -   Aplikace Microsoft Office for Mac 2011
> -   Microsoft OneDrive pro firmy pro SharePoint Server 2013
> -   Prohlížeč XPS
> 
> Kromě toho aplikace sdílení RMS má následující omezení:
> 
> -   Pro počítače se systémem Windows: Vyžaduje minimální verzi Windows 7 Service Pack 1

Další informace o tom, jak tyto aplikace podporovat Azure RMS naleznete v tématu [Jak aplikace podporují Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Informace o tom, jak je nakonfigurovat, najdete v části [Konfigurace aplikací pro Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## <a name="BKMK_SupportedServers"></a>Na místní servery, které podporují službu Azure RMS
Následující produkty místní server jsou podporovány službou Azure RMS, při použití konektoru Azure RMS, který se chová jako komunikační rozhraní (předávání) mezi místními servery a Azure RMS. Kromě toho tato konfigurace vyžaduje, že nakonfigurujete synchronizaci adresářů mezi doménovými strukturami služby Active Directory a Azure Active Directory.

-   **Exchange Server**:

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Souborové servery, které používají systém Windows Server a souboru klasifikace infrastruktury (FCI)**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Vzhledem k tomu, že souborové servery se systémem Windows Server 2008 R2 nemají vestavěné soubor akce úlohy správy umožňuje použít ochranu RMS, nelze použít konektor služby RMS pro tento scénář. Můžete ale použít soubor klasifikace infrastruktury a Azure RMS v těchto operačních systémech-li konfigurovat úlohu správy vlastní soubor spustit spustitelný soubor nebo skript, který lze chránit soubory pomocí Azure RMS. Například skript prostředí Windows PowerShell, který používá [ochranu RMS rutin](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > Tyto rutiny můžete použít také servery se systémem novější verze systému Windows Server s výhodu, že tyto rutiny můžete chránit všechny typy souborů. Konektor služby RMS chrání pouze soubory sady Office. Postupy: pokyny naleznete v tématu [Ochrana RMS pomocí systému Windows Server soubor klasifikace infrastruktury &#40;FCI&#41;](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

Konektor služby RMS je podporován v systému Windows Server 2012 R2, Windows Server 2012 a Windows Server 2008 R2.

Další informace o tom, jak nakonfigurovat konektor služby RMS pro tyto servery místně, naleznete v části [Nasazení konektoru Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Viz také
[Začínáme s Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

