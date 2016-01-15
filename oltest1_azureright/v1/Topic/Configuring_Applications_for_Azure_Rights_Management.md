---
description: na
keywords: na
title: Configuring Applications for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
---
# Konfigurace aplikac&#237; pro Azure Rights Management
> [!NOTE]
> Tyto informace jsou pro správci IT a konzultanty, kteří nainstalovali Azure Rights Management. Pokud hledáte Nápověda pro uživatele a informace o použití Rights Management pro konkrétní aplikace nebo otevření souboru, který je chráněného právy pomocí nápovědy a pokyny, který doprovází vaší aplikace.
> 
> Například pro aplikace systému Office, klikněte na ikonu Nápověda a zadejte hledané výrazy jako **Rights Management** nebo **IRM**. Sdílení obsahu RMS aplikace pro Windows, naleznete v části [Rights Management sdílení aplikace uživatelské příručce](http://technet.microsoft.com/library/dn339006.aspx).

Po nasazení Azure Rights Management (Azure RMS) pro vaši organizaci, použijte následující informace ke konfiguraci aplikace a služby pro podporu Azure RMS. Patří aplikace Office, například Word 2013 a Word 2010 a služby, například systému Exchange Online (přenos pravidla, zabránění ztrátě dat, se dál a šifrování zpráv) a služby SharePoint Online (chráněné knihoven). Informace o tom, jak tyto aplikace a služby podpory Rights Management, naleznete v tématu [Jak aplikace podporují Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

> [!IMPORTANT]
> Informace o podporované verze a dalších požadavcích naleznete v tématu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

-   [Office 365: Konfigurace pro klienty a online služeb](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365)

    -   [Exchange Online: Konfigurace IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline)

    -   [SharePoint Online a Onedrivem pro společnost: Konfigurace IRM](#BKMK_SharePointOnline)

-   [Office 2016 a Office 2013: Konfigurace klientů](#BKMK_Office2013Configuration)

-   [Systém Office 2010: Konfigurace klientů](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_Office2010Configuration)

-   [Služba Rights Management, aplikace pro sdílení: Instalace a konfigurace klientů](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp)

    -   [Aplikace pro systém Windows pro sdílení obsahu RMS: Instalace a konfigurace](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingAppforWindows)

    -   [Aplikace pro mobilní platformy pro sdílení obsahu RMS: Instalace](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingAppMovileDevices)

-   [Jiné aplikace, které podporují rozhraní API služby RMS: Instalace a konfigurace](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_RMSAPIs)

Konfiguraci na místní servery, jako je například Exchange Server a SharePoint Server naleznete v tématu [Nasazení konektoru Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!TIP]
> Příklady vysoké úrovně a snímky obrazovky konfigurován pro použití Azure RMS aplikací naleznete v tématu [Azure RMS v akci: Co správci a uživatelé v tématu](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) oddíl z [Co je Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tématu.

## <a name="BKMK_O365"></a>Office 365: Konfigurace pro klienty a online služeb
Vzhledem k tomu, že služeb Office 365 nativně podporuje Azure RMS, není vyžadována pro podporu funkcí informace rights management (IRM) pro aplikace, jako je například Word, Excel, PowerPoint, aplikace Outlook a webové aplikace Outlook žádná konfigurace počítače klienta. Všichni uživatelé mají provést se přihlaste se k jejich aplikace Office s jejich [!INCLUDE[o365_1](../Token/o365_1_md.md)] pověření a jejich lze chránit soubory a e-mailů a používat soubory a e-mailů, které bylo chráněno ostatním uživatelům.

Doporučujeme však doplnit tyto aplikace Rights Management sdílení aplikací, tak, aby uživatelé těžit z kanceláře doplněk. Další informace naleznete [Služba Rights Management, aplikace pro sdílení: Instalace a konfigurace klientů](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) v tomto tématu.

### <a name="BKMK_ExchangeOnline"></a>Exchange Online: Konfigurace IRM
Konfigurace systému Exchange Online podporu Azure RMS, musíte nakonfigurovat službu informace rights management (IRM) pro systému Exchange Online. Chcete-li to provést, použijete prostředí Windows PowerShell (není třeba instalovat samostatné modulu) a potom spusťte [Příkazy prostředí PowerShell pro službu Exchange Online](https://technet.microsoft.com/library/jj200677.aspx).

> [!NOTE]
> Nelze konfigurovat aktuálně systému Exchange Online podporu Azure RMS, pokud používáte klíč zákazníka spravovaného klienta (BYOK) pro Azure RMS, nikoli výchozí konfigurace klíče Microsoft spravovaného klienta. Další informace naleznete v tématu [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) v oddílu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tématu.
> 
> Pokud pokus o konfiguraci systému Exchange Online, když je Azure RMS pomocí BYOK, příkaz Import klíče (krok 5, v následujícím postupu) nezdaří, zobrazí se chybová zpráva **[FailureCategory = rutina FailedToGetTrustedPublishingDomainFromRmsOnlineException]**.

Následující kroky poskytují typickou sadu příkazů, které by byl spuštěn, chcete-li povolit systému Exchange Online používat Azure RMS:

1.  Pokud je to poprvé, že jste použili prostředí Windows PowerShell pro službu Exchange Online ve vašem počítači, je nutné nakonfigurovat ke spuštění podepsaný skriptů prostředí Windows PowerShell. Spuštění relace prostředí Windows PowerShell pomocí **Spustit jako správce** možnost a potom zadejte:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  V relaci prostředí Windows PowerShell Přihlaste se k systému Exchange Online pomocí účtu, který je povolen pro vzdálený přístup prostředí. Ve výchozím nastavení jsou povoleny všechny účty, které jsou vytvořeny v systému Exchange Online pro vzdálený přístup prostředí, ale to může být zakázány (a povoleno) s použitím   [sady uživatele &lt; identity uživatele &gt; - RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx) příkazu.

    Chcete-li se přihlásit, zadejte:

    ```
    $Cred = Get-Credential
    ```
    V **prostředí Windows PowerShell pověření požadavku** dialogové okno pole, zadejte služeb Office 365 uživatelské jméno a heslo.

3.  Připojte k systému Exchange Online službě spuštěním následujících příkazů:

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  Zadejte umístění klíče klienta Azure RMS, podle vaší oblasti:

    Severní Amerika (a státní správa odběrů):

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Pro Evropa:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Pro Asie:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Pro Jižní Ameriky:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  Importovat konfigurační data ze služby Azure RMS na serveru Exchange Online ve formě důvěryhodné domény publikování (důvěryhodné domény publikování). Jedná se o klíč klienta Azure RMS a Azure RMS šablony:

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    V tomto příkazu jsme použili název **RMS Online** pro základní název důvěryhodné domény publikování pro Azure RMS v systému Exchange Online. Po importu důvěryhodné domény publikování, se nazývá **RMS Online - 1** v systému Exchange Online.

6.  Povolení funkce Azure RMS tak, aby IRM funkce jsou k dispozici pro systému Exchange Online:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    Po spuštění tohoto příkazu, je automaticky povolen Rights Management pro klienta aplikace Outlook, aplikace Outlook Web a protokolu Exchange Active Sync.

7.  V případě potřeby testování, že tato konfigurace byla úspěšně dokončena s použitím následujícího příkazu:

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Příklad: **Test-IRMConfiguration -Sender  adams@contoso.com**

    Tento příkaz spustí posloupnost kontrol, který zahrnuje ověření připojení ke službě, načítání konfigurace, načítá identifikátory URI, licence a všechny šablony. V relaci prostředí Windows PowerShell zobrazí se výsledky jednotlivých a na konci, pokud všechno, co projde těmto kontrolám: **CELKOVÝ VÝSLEDEK: PRŮCHOD**

8.  Odpojení vzdálené relaci prostředí PowerShell:

    ```
    Remove-PSSession $Session
    ```

Uživatelé mohou nyní chránit jejich e-mailové zprávy pomocí Azure RMS. Ve webové aplikaci Outlook, vyberte například **nastavit oprávnění** z nabídky delší (**...**) a poté zvolte možnost **dál** nebo jeden z dostupných šablon pro použití ochrany informace o e-mailové zprávě a všechny přílohy. Vzhledem k tomu, že webové aplikace Outlook ukládá do mezipaměti uživatelského rozhraní pro jeden den, počkejte však zvoleném časovém období uplynout, než se pokusíte ochrana údajů vztahujících se e-mailové zprávy a po spuštění tyto příkazy konfigurace. Předtím, než aby odpovídalo nové konfigurace aktualizuje uživatelské rozhraní, se nezobrazí žádné možnosti z **nastavit oprávnění** nabídky.

> [!IMPORTANT]
> Je-li vytvořit nový [vlastní šablony](https://technet.microsoft.com/library/dn642472.aspx) pro Azure RMS nebo aktualizace šablony, pokaždé, když, je nutné spustit příkaz prostředí PowerShell Online Exchange (Pokud potřeby spustit kroky 2 a 3 nejprve) pro synchronizaci těchto změn systému Exchange Online: `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Jako správce serveru Exchange, můžete nakonfigurovat funkce, které automaticky, použít ochrany informace, jako [přenosu pravidla](https://technet.microsoft.com/library/dd302432.aspx), [zásady prevence (DLP) ztrátě dat](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx), a [chráněný hlasová pošta](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).

Podrobné pokyny ke konfiguraci systému Exchange Online, chcete-li povolit funkcí služby IRM naleznete v dokumentaci v knihovně Exchange. Příklad:

-   [Připojit k systému Exchange Online pomocí vzdáleného prostředí PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.160%29.aspx)

-   [Konfigurovat IRM používat Azure Rights Management](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)

#### Šifrování zpráv Office 365
Spusťte stejné kroky, jak je uvedeno v předchozím oddílu, ale pokud nechcete, aby šablony, který se má zobrazit před krok 6, spusťte následující příkaz zabránit IRM šablony k dispozici v aplikaci Outlook webovou aplikaci a klient aplikace Outlook: `Set-IRMConfiguration -ClientAccessServerEnabled $false`

Pak budete připraveni ke konfiguraci [přenosu pravidla](https://technet.microsoft.com/library/dd302432.aspx) automaticky upravit zprávu zabezpečení při příjemců, kterým se nacházejí mimo organizaci a vyberte možnost **použít šifrování zpráv Office 365** možnost.

Další informace o šifrování zpráv naleznete v tématu [šifrování ve službách Office 365](https://technet.microsoft.com/library/dn569286.aspx) v knihovně Exchange.

### <a name="BKMK_SharePointOnline"></a>SharePoint Online a Onedrivem pro společnost: Konfigurace IRM
Ke konfiguraci služby SharePoint Online a Onedrivem pro společnost pro podporu Azure RMS, je třeba nejprve povolit službu informace práva management (IRM) pro službu SharePoint Online pomocí Centrum správy služby SharePoint. Potom vlastníci webu mohou IRM chránit jejich seznamy služby SharePoint a knihoven dokumentů a uživatelé mohou IRM chránit jejich Onedrivem pro knihovnu obchodní tak, aby dokumenty, které jsou zde uloženy a sdílet s ostatními, jsou automaticky chráněné službou Azure RMS.

Povolit službu informace rights management (IRM) pro službu SharePoint Online, postupujte podle následujících pokynů z webu Office:

-   [Sada nahoru Správa informačních práv (IRM) v Centrum správy služby SharePoint](http://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx)

Tato konfigurace se provádí správce služeb Office 365.

#### Konfigurace IRM pro seznamy a knihovny
Poté, co povolíte službu IRM pro službu SharePoint, mohou vlastníci webu IRM chránit jejich knihoven dokumentů služby SharePoint a seznamy. Pokyny naleznete v tématu následující z webu Office:

-   [Použít službu Rights Management informace do seznamu nebo knihovny](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

Tato konfigurace se provádí správce webu služby SharePoint.

#### <a name="BKMK_OneDrive"></a>Konfigurace IRM pro Onedrivem pro podnik
Poté, co povolíte službu IRM pro SharePoint Online, Onedrivem uživatelů pro knihovnu dokumentů obchodní mohou být konfigurovány pro ochranu Rights Management.  Uživatelé mohou konfigurovat to pro sebe pomocí **Nastavení** ikonu v jejich Onedrivem. I když správci nelze nakonfigurovat službu Rights Management pro Onedrivem uživatelů pro obchodní pomocí Centrum správy služby SharePoint, můžete tuto operaci provést pomocí prostředí Windows PowerShell.

> [!NOTE]
> Další informace o konfiguraci Onedrivem pro firmu, naleznete v dokumentaci Office[nastavit Onedrivem pro společnost ve službách Office 365](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb).

##### Konfigurace pro uživatele
Uživatelům tyto pokyny, aby jejich Onedrivem, mohou nastavit pro podnikové a IRM chránit jejich obchodní soubory.

1.  V Onedrivem, klepněte **Nastavení** ikonu, otevřete nabídku nastavení, a potom klikněte na tlačítko **obsah webu**.

2.  Přesunutí ukazatele myši nad **Dokumenty** vedle sebe, zvolili elipsy (**...**) a potom klikněte na tlačítko **nastavení.**

3.  Na **Nastavení** stránky v **oprávnění a správa** klikněte na tlačítko **informace Rights Management**.

4.  Na **informace o nastavení správy přístupových práv** stránky, vyberte možnost **omezit oprávnění v této knihovně při stažení** zaškrtnutí políčka, zadejte svého výběru: název a popis pro oprávnění a volitelně, klikněte na tlačítko **Zobrazit volby** ke konfiguraci volitelné konfigurace a potom klikněte na tlačítko **OK**.

    Další informace o možnostech konfigurace naleznete v pokynech v [použít informace Rights Management do seznamu nebo knihovny](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1) z dokumentace Office.

Vzhledem k tomu, že tato konfigurace závisí na uživatelům, nikoli správce IRM chránit jejich Onedrivem pro knihovnu obchodní, informovat uživatele o výhodách chránit jejich soubory a jak na to. Vysvětlují například, že při sdílení dokumentu z Onedrivem pro firmu, pouze uživatelé, kterým udělí oprávnění k němu přístup s nějaká omezení, které konfigurují i v případě, že soubor přejmenován a zkopírovaných jinde.

##### Konfigurace pro správce
Přestože IRM nelze nakonfigurovat pro Onedrivem uživatelů pro obchodní pomocí Centrum správy služby SharePoint, můžete tuto operaci provést pomocí prostředí Windows PowerShell. Chcete-li povolit IRM pro tyto knihovny, postupujte takto:

1.  Stáhněte si a nainstalujte [SharePoint Online Client Components SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038).

2.  Stáhněte si a nainstalujte [SharePoint Online Management Shell](http://www.microsoft.com/en-us/download/details.aspx?id=35588).

3.  Zkopírujte obsah následující skript a zadejte název souboru sady IRMOnOneDriveForBusiness.ps1 ve vašem počítači.

    *&#42;&#42;Zřeknutí se&#42;&#42;*: Tento ukázkový skript není podporován v rámci jakékoli program standardní odborná pomoc společnosti Microsoft nebo služby. Tento ukázkový skript jsou poskytovány tak, jak je bez záruky jakéhokoli druhu.

    ```
    # Requires Windows PowerShell version 3 <# Description: Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> # URL will be in the format https://<tenant-name>-admin.sharepoint.com $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.com" $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com", "https://contoso-my.sharepoint.com/personal/user2_contoso_com", "https://contoso-my.sharepoint.com/personal/user3_contoso_com") <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row). Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv" #> $listTitle = "Documents" function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Set-IrmConfiguration { [cmdletbinding()] param( [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List, [parameter(Mandatory=$true)][string]$PolicyTitle, [parameter(Mandatory=$true)][string]$PolicyDescription, [parameter(Mandatory=$false)][switch]$IrmReject, [parameter(Mandatory=$false)][DateTime]$ProtectionExpirationDate, [parameter(Mandatory=$false)][switch]$DisableDocumentBrowserView, [parameter(Mandatory=$false)][switch]$AllowPrint, [parameter(Mandatory=$false)][switch]$AllowScript, [parameter(Mandatory=$false)][switch]$AllowWriteCopy, [parameter(Mandatory=$false)][int]$DocumentAccessExpireDays, [parameter(Mandatory=$false)][int]$LicenseCacheExpireDays, [parameter(Mandatory=$false)][string]$GroupName ) process { Write-Verbose "Applying IRM Configuration on '$($List.Title)'" # reset the value to the default settings $list.InformationRightsManagementSettings.Reset() $list.IrmEnabled = $true # IRM Policy title and description $list.InformationRightsManagementSettings.PolicyTitle       = $PolicyTitle $list.InformationRightsManagementSettings.PolicyDescription = $PolicyDescription # Set additional IRM library settings # Do not allow users to upload documents that do not support IRM $list.IrmReject = $IrmReject.IsPresent $parsedDate = Get-Date if([DateTime]::TryParse($ProtectionExpirationDate, [ref]$parsedDate)) { # Stop restricting access to the library at <date> $list.IrmExpire = $true $list.InformationRightsManagementSettings.DocumentLibraryProtectionExpireDate = $ProtectionExpirationDate } # Prevent opening documents in the browser for this Document Library $list.InformationRightsManagementSettings.DisableDocumentBrowserView = $DisableDocumentBrowserView.IsPresent # Configure document access rights # Allow viewers to print $list.InformationRightsManagementSettings.AllowPrint = $AllowPrint.IsPresent # Allow viewers to run script and screen reader to function on downloaded documents $list.InformationRightsManagementSettings.AllowScript = $AllowScript.IsPresent # Allow viewers to write on a copy of the downloaded document $list.InformationRightsManagementSettings.AllowWriteCopy = $AllowWriteCopy.IsPresent if($DocumentAccessExpireDays) { # After download, document access rights will expire after these number of days (1-365) $list.InformationRightsManagementSettings.EnableDocumentAccessExpire = $true $list.InformationRightsManagementSettings.DocumentAccessExpireDays   = $DocumentAccessExpireDays } # Set group protection and credentials interval if($LicenseCacheExpireDays) { # Users must verify their credentials using this interval (days) $list.InformationRightsManagementSettings.EnableLicenseCacheExpire = $true $list.InformationRightsManagementSettings.LicenseCacheExpireDays   = $LicenseCacheExpireDays } if($GroupName) { # Allow group protection. Default group: $list.InformationRightsManagementSettings.EnableGroupProtection = $true $list.InformationRightsManagementSettings.GroupName             = $GroupName } } end { if($list) { Write-Verbose "Committing IRM configuration settings on '$($list.Title)'" $list.InformationRightsManagementSettings.Update() $list.Update() $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() } } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # connect to Office365 first, required for SharePoint Online cmdlets to run Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential # enumerate each of the specified site URLs foreach($webUrl in $webUrls) { $grantedSiteCollectionAdmin = $false try { # establish the client context and set the credentials to connect to the site $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl) $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # initialize the site and web context $script:clientContext.Load($script:clientContext.Site) $script:clientContext.Load($script:clientContext.Web) $script:clientContext.ExecuteQuery() # load and ensure the tenant admin user account if present on the target SharePoint site $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName) $script:clientContext.Load($tenantAdminUser) $script:clientContext.ExecuteQuery() # check if the tenant admin is a site admin if( -not $tenantAdminUser.IsSiteAdmin ) { try { # grant the tenant admin temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null $grantedSiteCollectionAdmin = $true } catch { Write-Error $_.Exception return } } try { # load the list orlibrary using CSOM $list = $null $list = $script:clientContext.Web.Lists.GetByTitle($listTitle) $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() # **************  ADMIN INSTRUCTIONS  ************** # If necessary, modify the following Set-IrmConfiguration parameters to match your required values # The supplied options and values are for example only # Example that shows the Set-IrmConfiguration command with all parameters: Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" -IrmReject -ProtectionExpirationDate $(Get-Date).AddDays(180) -DisableDocumentBrowserView -AllowPrint -AllowScript -AllowWriteCopy -LicenseCacheExpireDays 25 -DocumentAccessExpireDays 90 Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" } catch { Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())" } } finally { if($grantedSiteCollectionAdmin) { # remove the temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null } } } Disconnect-SPOService -ErrorAction SilentlyContinue
    ```

4.  Zkontrolujte skript a provést následující změny:

    1.  Hledat `$sharepointAdminCenterUrl` a nahraďte hodnotu příklad vlastní adresa URL služby SharePoint správce center.

        Zjistíte, tato hodnota jako základní adresu URL při přechodu do Centrum správy služby SharePoint, která je v následujícím formátu: https://*&lt; tenant_name &gt;*-admin.sharepoint.com

        Například pokud je název klienta "contoso", pak by zadáte: **https://contoso-admin.sharepoint.com**

    2.  Hledat `$tenantAdmin` a nahraďte hodnotu příklad s účtem plně kvalifikovaný globálního správce pro Office 365.

        Tato hodnota je stejný jako ten, můžete použít k přihlášení k portálu pro správce služeb Office 365 jako globálního správce a má následující formát: uživatelské_jméno @*&lt; název domény klienta &gt;*.com

        Například pokud uživatelské jméno globálního správce služeb Office 365 "admin" pro doménu klienta "contoso.com", zadáte: **admin@contoso.com**

    3.  Hledat `$webUrls` a nahraďte hodnoty příklad vaši uživatelé Onedrivem pro obchodní adres URL webových, přidávat a odstraňovat libovolný počet položek, podle potřeby.

        Můžete si také přečíst komentáře ve skriptu o tom, jak nahradit toto pole pomocí importu. Soubor CSV, který obsahuje všechny adresy URL, je nutné nakonfigurovat.  Jsme jste poskytli další ukázkový skript automatické vyhledávání a extrahovat adresy URL k naplnění to. Soubor CSV. Až budete připraveni k tomu, rozbalte [Další skript pro výstup firemní adres URL pro všechny Onedrivem. Soubor CSV](#BKMK_Script_OD4B_URLS) části bezprostředně po provedení těchto kroků.

        Web je adresa URL pro daného uživatele Onedrivem pro společnost v následujícím formátu: https://*&lt; název klienta &gt;*-my.sharepoint.com/personal/*&lt; uživatelské_jméno &gt;*_*&lt; název klienta &gt;*_com

        Například pokud má uživatel v rámci klienta contoso uživatelské jméno v "rsimone", zadáte: **https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**

    4.  Vzhledem k tomu, že používáme skript nakonfigurovat Onedrivem pro firmu, neměňte hodnotu **Documents** pro `$listTitle` proměnné.

    5.  Hledat `ADMIN INSTRUCTIONS`. Pokud žádné změny provedené v této části, bude nakonfigurován Onedrivem uživatele pro obchodní pro IRM s názvem zásady "Chráněných souborů" a "Tato zásada omezuje přístup na autorizované uživatele" popis.  Žádné další možnosti IRM nebudou nastaveny, což je pravděpodobně vhodné pro většinu prostředí. Můžete však změnit navrhované zásady název a popis a také přidat další možnosti IRM, které jsou vhodné pro vaše prostředí. Viz příklad komentářem ve skriptu umožní vytvořit vlastní sadu parametrů pro příkaz IrmConfiguration sadu.

5.  Uložit skript a jej podepsat. Pokud není uživatel skriptu (bezpečnější), musí být v tomto počítači ke spouštění skriptů bez znaménka nakonfigurována prostředí Windows PowerShell. Chcete-li to provést, spusťte relaci prostředí Windows PowerShell s **Spustit jako správce** a zadejte: **Set-ExecutionPolicy Unrestricted**. Tato konfigurace však umožní všechny nepodepsané skripty spustit (méně bezpečné).

    Další informace o podepisování skriptů prostředí Windows PowerShell, naleznete v části [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) v knihovně dokumentace nástroje prostředí PowerShell.

6.  Spustit skript a pokud se zobrazí výzva, zadejte heslo pro účet správce služeb Office 365. Je-li upravit skript a potom ho spusťte ve stejné relaci prostředí Windows PowerShell, nebudou vyzváni k zadání pověření.

> [!TIP]
> Tento skript lze také použít ke konfiguraci IRM pro knihovnu služby SharePoint Online. Pro tuto konfiguraci, bude pravděpodobně chcete povolit další možnost **Nepovolit uživatelům odesílat dokumenty, které nepodporují technologii IRM**, aby bylo zajištěno, že knihovna obsahuje pouze dokumentů chráněných.    To lze provést, přidejte `-IrmReject` parametr příkazu sady IrmConfiguration ve skriptu.
> 
> Je třeba také změnit `$webUrls` proměnné (například **https://contoso.sharepoint.com**) a  `$listTitle` proměnné (například **$Reports**).

Pokud je třeba zakázat IRM pro daného uživatele Onedrivem pro obchodní knihovnách, rozbalte [Skript zakázání IRM pro Onedrivem pro podnik](#BKMK_Script_OD4B_DisableIRM) oddílu.

###### <a name="BKMK_Script_OD4B_URLS"></a>Další skript pro výstup firemní adres URL pro všechny Onedrivem. Soubor CSV
V kroku 4c výše uvedené slouží k extrakci adresy URL pro všechny uživatele Onedrivem pro obchodní knihovny, které lze potom zkontrolujte, v případě potřeby upravit a poté proveďte import do hlavního skriptu následující skript prostředí Windows PowerShell.

Tento skript také vyžaduje, aby [SharePoint Online Client Components SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038) a [SharePoint Online Management Shell](http://www.microsoft.com/en-us/download/details.aspx?id=35588). Postupujte podle pokynů stejné a zkopírovat a vložit, uložte soubor místně (například "sestavy-OneDriveForBusinessSiteInfo.ps1"), změňte   `$sharepointAdminCenterUrl` a `$tenantAdmin` před hodnoty jako a potom spusťte skript.

*&#42;&#42;Zřeknutí se&#42;&#42;*: Tento ukázkový skript není podporován v rámci jakékoli program standardní odborná pomoc společnosti Microsoft nebo služby. Tento ukázkový skript jsou poskytovány tak, jak je bez záruky jakéhokoli druhu.

```
# Requires Windows PowerShell version 3 <# Description: Queries the search service of an Office 365 tenant to retrieve all OneDrive for Business sites. Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_<date>.csv"). Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> # URL will be in the format https://<tenant-name>-admin.sharepoint.com $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.onmicrosoft.com" $reportName = "OneDriveForBusinessSiteInfo_$((Get-Date).ToString("yyyy-MM-dd_hh.mm.ss")).csv" $oneDriveForBusinessSiteUrls= @() $resultsProcessed = 0 function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # establish the client context and set the credentials to connect to the site $clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($sharepointAdminCenterUrl) $clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # run a query against the Office 365 tenant search service to retrieve all OneDrive for Business URLs do { # build the query object $query = New-Object Microsoft.SharePoint.Client.Search.Query.KeywordQuery($clientContext) $query.TrimDuplicates        = $false $query.RowLimit              = 500 $query.QueryText             = "SPSiteUrl:'/personal/' AND contentclass:STS_Site" $query.StartRow              = $resultsProcessed $query.TotalRowsExactMinimum = 500000 # run the query $searchExecutor = New-Object Microsoft.SharePoint.Client.Search.Query.SearchExecutor($clientContext) $queryResults = $searchExecutor.ExecuteQuery($query) $clientContext.ExecuteQuery() # enumerate the search results and store the site URLs $queryResults.Value[0].ResultRows | % { $oneDriveForBusinessSiteUrls += $_.Path $resultsProcessed++ } } while($resultsProcessed -lt $queryResults.Value.TotalRows) $oneDriveForBusinessSiteUrls | Out-File -FilePath $reportName
```

###### <a name="BKMK_Script_OD4B_DisableIRM"></a>Skript zakázání IRM pro Onedrivem pro podnik
Použijte následující ukázkový skript, pokud je třeba zakázat IRM pro Onedrivem uživatelů pro firmu.

Tento skript také vyžaduje, aby [SharePoint Online Client Components SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038) a [SharePoint Online Management Shell](http://www.microsoft.com/en-us/download/details.aspx?id=35588). Zkopírovat a vložit obsah, uložte soubor místně (například "Disable-IRMOnOneDriveForBusiness.ps1") a upravit   `$sharepointAdminCenterUrl` a `$tenantAdmin` hodnoty. Ručně zadat Onedrivem pro adresy URL obchodní nebo použít skript v předchozím oddílu, aby mohli naimportovat a poté spustit skript.

*&#42;&#42;Zřeknutí se&#42;&#42;*: Tento ukázkový skript není podporován v rámci jakékoli program standardní odborná pomoc společnosti Microsoft nebo služby. Tento ukázkový skript jsou poskytovány tak, jak je bez záruky jakéhokoli druhu.

```
# Requires Windows PowerShell version 3 <# Description: Disables IRM for OneDrive for Business and can also be used for SharePoint Online libraries and lists Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.com" $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com", "https://contoso-my.sharepoint.com/personal/user2_contoso_com", "https://contoso-my.sharepoint.com/personal/person3_contoso_com") <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row). Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv" #> $listTitle = "Documents" function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Remove-IrmConfiguration { [cmdletbinding()] param( [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List ) process { Write-Verbose "Disabling IRM Configuration on '$($List.Title)'" $List.IrmEnabled = $false $List.IrmExpire  = $false $List.IrmReject  = $false $List.InformationRightsManagementSettings.Reset() } end { if($List) { Write-Verbose "Committing IRM configuration settings on '$($list.Title)'" $list.InformationRightsManagementSettings.Update() $list.Update() $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() } } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # connect to Office365 first, required for SharePoint Online cmdlets to run Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential # enumerate each of the specified site URLs foreach($webUrl in $webUrls) { $grantedSiteCollectionAdmin = $false try { # establish the client context and set the credentials to connect to the site $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl) $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # initialize the site and web context $script:clientContext.Load($script:clientContext.Site) $script:clientContext.Load($script:clientContext.Web) $script:clientContext.ExecuteQuery() # load and ensure the tenant admin user account if present on the target SharePoint site $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName) $script:clientContext.Load($tenantAdminUser) $script:clientContext.ExecuteQuery() # check if the tenant admin is a site admin if( -not $tenantAdminUser.IsSiteAdmin ) { try { # grant the tenant admin temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null $grantedSiteCollectionAdmin = $true } catch { Write-Error $_.Exception return } } try { # load the list orlibrary using CSOM $list = $null $list = $script:clientContext.Web.Lists.GetByTitle($listTitle) $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() Remove-IrmConfiguration -List $list } catch { Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())" } } finally { if($grantedSiteCollectionAdmin) { # remove the temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null } } } Disconnect-SPOService -ErrorAction SilentlyContinue
```

## <a name="BKMK_Office2013Configuration"></a>Office 2016 a Office 2013: Konfigurace klientů
Vzhledem k tomu, že tyto novější verze systému Office podporovaly Azure RMS, není vyžadována pro podporu funkcí informace rights management (IRM) pro aplikace, jako je například Word, Excel, PowerPoint, aplikace Outlook a webové aplikace Outlook žádná konfigurace počítače klienta. Všichni uživatelé mají provést se přihlaste se k jejich aplikace Office s jejich [!INCLUDE[o365_1](../Token/o365_1_md.md)] pověření a jejich lze chránit soubory a e-mailů a používat soubory a e-mailů, které bylo chráněno ostatním uživatelům.

Doporučujeme však doplnit tyto aplikace Rights Management sdílení aplikací, tak, aby uživatelé těžit z kanceláře doplněk. Další informace naleznete [Služba Rights Management, aplikace pro sdílení: Instalace a konfigurace klientů](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) v tomto tématu.

## <a name="BKMK_Office2010Configuration"></a>Systém Office 2010: Konfigurace klientů
Pro klientské počítače Azure RMS pomocí systému Office 2010 že jste nainstalovali Rights Management sdílení aplikace pro systém Windows. Není vyžadována žádná další konfigurace jiných než uživatelé třeba se přihlásit s jejich [!INCLUDE[o365_1](../Token/o365_1_md.md)] pověření a jejich poté mohou chránit soubory a používat soubory, které bylo chráněno ostatním uživatelům.

Další informace o Rights Management, aplikace pro sdílení, naleznete [Služba Rights Management, aplikace pro sdílení: Instalace a konfigurace klientů](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) v tomto tématu.

## <a name="BKMK_SharingApp"></a>Služba Rights Management, aplikace pro sdílení: Instalace a konfigurace klientů
Správa práv (RMS), které jsou aplikace pro sdílení je vyžadována pro klientské počítače Azure RMS pomocí systému Office 2010 a doporučuje pro všechny počítače a mobilní zařízení, které podporují Azure RMS. Aplikace pro sdílení obsahu RMS lze integrovat s Office aplikací pomocí instalace Office doplněk tak, aby uživatelé mohli snadno chránit soubory a e-mailů přímo z pásu karet. Nabízí také obecný ochrany pro typy souborů, které nejsou podporovány nativně Azure RMS a dokumentu sledování webu pro uživatele, který můžete sledovat a odvolání soubory, které se mají chráněny.

### <a name="BKMK_SharingAppforWindows"></a>Aplikace pro systém Windows pro sdílení obsahu RMS: Instalace a konfigurace
Chcete-li nainstalovat a nakonfigurovat aplikaci pro systém Windows pro nasazení v podnikovém prostředí pro sdílení obsahu RMS, podívejte se na téma [Rights Management sdílení aplikace Správce průvodce](http://technet.microsoft.com/library/dn339003.aspx).

> [!TIP]
> Pokud chcete rychle instalovat a testovat aplikace pro jeden počítač pro sdílení obsahu RMS naleznete v tématu [Stáhnout a nainstalovat Rights Management, aplikace pro sdílení](http://technet.microsoft.com/library/dn574734.aspx) z [Rights Management sdílení aplikace uživatelské příručce](http://technet.microsoft.com/library/dn339006.aspx).

### <a name="BKMK_SharingAppMovileDevices"></a>Aplikace pro mobilní platformy pro sdílení obsahu RMS: Instalace
Chcete-li nainstalovat aplikaci pro mobilní platformy pro sdílení obsahu RMS, můžete stáhnout relevantní aplikace pomocí odkazů na [Microsoft Rights Management stránky](http://go.microsoft.com/fwlink/?LinkId=303970). Chcete-li používat Azure RMS pomocí této aplikace není nutná žádná konfigurace.

## <a name="BKMK_RMSAPIs"></a>Jiné aplikace, které podporují rozhraní API služby RMS: Instalace a konfigurace
Tato kategorie obsahuje – podnikových aplikací, které jsou zapsány interně pomocí sady SDK služby RMS a aplikace z dodavateli softwaru, které byly vytvořeny pomocí sady SDK služby RMS. Pro tyto aplikace postupujte podle pokynů, které jsou k dispozici v aplikaci.

## Další kroky
Po dokončení konfigurace aplikace podporovat Azure Rights Management, použijte [Plán nasazení Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) Chcete-li zkontrolovat, zda jsou další kroky konfigurace, které chcete provést předtím, než můžete přejít na [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] uživatelům a správcům. Pokud ne, naleznete v části [Použití služby Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) pro vaše další kroky.

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

