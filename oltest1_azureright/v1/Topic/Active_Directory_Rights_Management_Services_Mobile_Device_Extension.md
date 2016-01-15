---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Rozš&#237;řen&#237; služby AD RMS (Active Directory Rights Management Services) pro mobiln&#237; zař&#237;zen&#237;
Rozšíření služby AD RMS (Active Directory Rights Management Services) pro mobilní zařízení běží nad stávajícím nasazením služby AD RMS. Pokud mobilní zařízení uživatele podporuje nejnovějšího klienta služby RMS a používá aplikace podporující RMS, může uživatel chránit a využívat citlivá data. Uživatelé takových zařízení například můžou:

-   Pomocí aplikace Sdílení RMS využívat chráněné textové soubory v různých formátech (včetně .txt, .csv a .xml).

-   Pomocí aplikace Sdílení RMS využívat chráněné soubory obrázků (včetně .jpg, .gif, and .tif).

-   Pomocí aplikace Sdílení RMS otevřít libovolný obecně chráněný soubor (ve formátu .pfile).

-   Pomocí aplikace Sdílení RMS chránit na zařízení soubory obrázků.

-   Pomocí prohlížeče PDF pro mobilní zařízení podporujícího RMS otvírat soubory PDF, které jsou chráněné aplikací Sdílení RMS pro Windows nebo jinou aplikací podporující RMS.

-   Používat jiné aplikace od dodavatelů softwaru, kteří nabízejí aplikace podporující RMS, jež podporují typy souborů nativně podporující RMS.

-   Používat interně vytvořené aplikace podporující RMS, které jsou napsané pomocí sady RMS SDK.

> [!NOTE]
> Aplikaci Sdílení RMS si můžete stáhnout ze stránky [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) na webu Microsoftu.
> 
> Další informace o různých typech souborů podporovaných službou RMS najdete v části [Podporované typy souborů a přípon názvů souborů](http://technet.microsoft.com/library/dn339003.aspx) příručky pro správce aplikace pro sdílení obsahu Rights Management.

Pokud na zařízení používáte poštovní aplikaci podporující technologii Exchange ActiveSync IRM, nepotřebujete rozšíření pro mobilní zařízení, abyste mohli využívat nebo vytvářet chráněný e-mail. Tato nativní podpora služby RMS a mobilních zařízení se zavedla s aktualizací Exchange 2010 Service Pack 1.

Pokyny k nasazení rozšíření služby AD RMS (Active Directory Rights Management Services) pro mobilní zařízení najdete v následujících částech:

-   [Prerequisites for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [Specifying the DNS SRV records for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [Deploying the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>Předpoklady pro rozšíření služby AD RMS pro mobilní zařízení
Před instalací rozšíření služby AD RMS pro mobilní zařízení musí být splněné tyto předpoklady.

|Požadavek|Další informace|
|-------------|-------------------|
|Stávající nasazení služby AD RMS na Windows Serveru 2012 R2 nebo Windows Serveru 2012. **Note:** Služba AD RMS musí používat úplnou databázi založenou na Microsoft SQL Serveru, která je na samostatném serveru, a ne interní databázi Windows, která se často používá k testování na stejném serveru.|Dokumentaci ke službě AD RMS najdete v článku [Služba AD RMS (Active Directory Rights Management Services)](http://technet.microsoft.com/library/hh831364.aspx) v knihovně k Windows Serveru.|
|Služba AD FS nasazená na Windows Serveru 2012 R2|Dokumentaci ke službě AD FS najdete v článku [Průvodce nasazením služby AD FS v systému Windows Server 2012 R2](http://technet.microsoft.com/library/dn486820.aspx) v knihovně k Windows Serveru.<br /><br />Služba AD FS musí být nakonfigurovaná na rozšíření pro mobilní zařízení. Pokyny najdete v části [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS) v tomto tématu.|
|Záznamy SRV v DNS|Vytvořte jeden nebo víc záznamů SRV v doméně nebo doménách vaší společnosti:<br /><br />-   Jeden záznam pro každou příponu e-mailové domény, kterou budou uživatelé používat<br />-   Jeden záznam pro každý plně kvalifikovaný název domény používaný vašimi clustery RMS k ochraně obsahu<br /><br />Když uživatelé na mobilním zařízení zadají e-mailovou adresu, podle přípony domény se zjistí, jestli mají použít infrastrukturu služby AD RMS nebo Azure RMS. Pokud se najde záznam SRV, klienti budou přesměrovaní na server AD RMS, který odpovídá této adrese URL.<br /><br />Když uživatelé na mobilním zařízení využívají chráněný obsah, klientská aplikace vyhledá v systému DNS záznam odpovídající plně kvalifikovanému názvu domény, který obsah ochránil. Zařízení je pak přesměrované na cluster AD RMS určený v záznamu DNS a získá povolení k otevření obsahu. Tento cluster RMS je většinou stejný cluster RMS, který obsah ochránil.<br /><br />Informace o tom, jak vytvořit záznamy SRV, najdete v části [Specifying the DNS SRV Records for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV) v tomto tématu.|
|Aktuálně podporovaní klienti:<br /><br />-   Zařízení s Androidem, která používají nejnovější verzi aplikace Sdílení RMS pro Android|Minimální verze Android 4.0.3.<br /><br />Stáhněte si aplikaci Sdílení RMS pro Android z webu [Microsoft Connect](https://connect.microsoft.com/site1170/Downloads) a zkušebně si ji nainstalujte na zařízení.|

### <a name="BKMK_ADFS"></a>Konfigurace služby AD FS pro rozšíření služby AD RMS pro mobilní zařízení
Nejdřív musíte nakonfigurovat službu AD FS a potom budete autorizovat aplikaci Sdílení RMS pro Android.

##### Krok 1: Konfigurace služby AD FS

-   Buď můžete spustit skript Windows PowerShellu, který automaticky nakonfiguruje službu AD FS na podporu rozšíření služby AD RMS pro mobilní zařízení, nebo můžete ručně zadat možnosti a hodnoty konfigurace:

    -   Pokud chcete službu AD FS nakonfigurovat automaticky, zkopírujte si následující kód do souboru skriptu Windows PowerShellu a spusťte ho:

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   Pokud chcete službu AD FS nakonfigurovat ručně, použijte tato nastavení:

        |Konfigurace|Hodnota|
        |---------------|-----------|
        |**Vztah důvěryhodnosti předávající strany**|api.rms.rest.com|
        |**Pravidlo deklarace identity**|**Úložiště atributů**:  Active Directory<br /><br />**E-mailové adresy**:  e-mailová adresa<br /><br />**Hlavní název uživatele**:  UPN<br /><br />**Adresa proxy serveru**:  https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### Krok 2: Autorizace aplikace Sdílení RMS pro Android

-   Podporu pro zařízení s Androidem přidáte spuštěním následujícího příkazu Windows PowerShellu:

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>Vytvoření záznamů SRV služby DNS pro rozšíření služby AD RMS pro mobilní zařízení
Pro každou e-mailovou doménu, kterou budou uživatelé používat, musíte vytvořit záznamy SRV služby DNS. Pokud všichni uživatelé používají podřízené domény z jedné nadřazené domény a všichni uživatelé z tohoto souvislého oboru názvů používají stejný cluster RMS, můžete použít jenom jeden záznam SRV v nadřazené doméně a služba RMS najde odpovídající záznamy DNS.

Záznamy SRV mají tento formát: _rmsdisco._http._tcp. *&lt;přípona_e-mailu&gt;**&lt;číslo_portu&gt;**&lt;plně_kvalifikovaný_název_domény_clusteru_RMS&gt;*

Pokud například vaše organizace má uživatele s těmito e-mailovými adresami:

-   uživatel@contoso.com

-   uživatel@sales.contoso.com

-   uživatel@fabrikam.com

– a pro doménu contoso.com nejsou žádné další podřízené domény používající jiný cluster RMS než cluster s názvem **rmsserver.contoso.com**, vytvořte dva záznamy SRV služby DNS s těmito hodnotami:

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

Kromě těchto záznamů SRV služby DNS pro vaše e-mailové domény musíte vytvořit další záznam SRV služby DNS v doménách uživatelů. Tento záznam musí určovat adresy URL clusteru RMS, který chrání obsah. Každý soubor, který je chráněný službou RMS, zahrnuje adresu URL clusteru, který tento soubor ochránil. Mobilní zařízení pomocí záznamu SRV služby DNS a plně kvalifikovaného názvu domény URL zadaného v záznamu najdou příslušný cluster RMS, který může podporovat mobilní zařízení.

Pokud je váš cluster RMS třeba **rmsserver.contoso.com**, vytvořte záznam SRV služby DNS s těmito hodnotami: **_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>Nasazení rozšíření služby AD RMS pro mobilní zařízení
Než budete rozšíření služby AD RMS pro mobilní zařízení instalovat, musíte splnit předpoklady z předchozí části a znát adresu URL serveru AD FS. Pak udělejte tyto kroky:

1.  Stáhněte si rozšíření služby AD RMS pro mobilní zařízení z webu [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=397245).

2.  Spusťte Setup.exe. Tím spustíte průvodce instalací rozšíření služby AD RMS (Active Directory Rights Management Services) pro mobilní zařízení.

3.  Po zobrazení výzvy zadejte adresu URL serveru AD FS, který jste nakonfigurovali dřív.

4.  Dokončete průvodce.

Spusťte tohoto průvodce na všech uzlech v clusteru RMS.

