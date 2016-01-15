---
description: na
keywords: na
title: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
---
# Migrace ze služby AD RMS na Azure Rights Management
Použijte následující sady pokyny k migraci Active Directory Rights Management Services (AD RMS) nasazení do Azure Rights Management (Azure RMS). Po migraci uživatelé budou mít stále přístup k dokumentům a e-mailové zprávy, že vaše organizace chráněné pomocí služby AD RMS a nově chráněný obsah bude používat Azure RMS.

Nejste si jisti, zda je tato migrace služby AD RMS pro organizaci správné?

-   Úvod do Azure RMS, obchodních problémů, které lze vyřešit, bude vypadat takto správcům a uživatelům, a jak funguje naleznete v části [Co je Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

-   Porovnání Azure RMS pomocí služby AD RMS, naleznete v části [Porovnání Azure Rights Management a služby AD RMS](../Topic/Comparing_Azure_Rights_Management_and_AD_RMS.md).

## Požadavky pro migraci služby AD RMS na službu Azure RMS
Před zahájením migrace do Azure RMS, ujistěte se, že jsou splněny následující požadavky a že chápete žádné omezení.

|Požadavek|Další informace|
|-------------|-------------------|
|Podporované nasazení služby RMS|Všechny verze služby AD RMS ze systému Windows Server 2008 prostřednictvím systému Windows Server 2012 R2 podporuje migraci na službu Azure RMS:<br /><br />-   Windows Server 2008 (x 86 nebo x 64)<br />-   Windows Server 2008 R2 (x 64)<br />-   Windows Server 2012 (x 64)<br />-   Windows Server 2012 R2 (x 64) **Note:** Pokud používáte Windows RMS na Windows Server 2003, tuto verzi operačního systému bude mimo podporu během 2015. Tato verze služby RMS můžete migrovat do Azure RMS, ale tento proces je podporována pouze v případě, že operační systém je stále podporován. Problém odstraníte může importovat vaší důvěryhodné domény publikování (důvěryhodné domény publikování) na verzi služby AD RMS, který je podporován a znovu importujte důvěryhodné domény publikování bez možnosti kompatibility RMS 1.0. Další informace o důvěryhodných domén publikování naleznete v tématu [Důvěryhodné domény publikování](http://technet.microsoft.com/library/dd996639%28v=ws.10%29.aspx)<br />Jsou podporovány všechny platné topologie služby AD RMS:<br /><br />-   Jediná doménová struktura, jednoduché RMS cluster<br />-   Jedna doménová struktura více clusterů RMS jen pro licencování<br />-   Více doménových struktur, více clusterů RMS **Note:** Ve výchozím nastavení více clusterů RMS migrovat do jednoho klienta Azure RMS. Pokud chcete klientům různé RMS, je nutné považovat jako jiný migrace. Klíč z jednoho clusteru RMS nelze importovat do více než jeden klienta Azure RMS.|
|Všechny požadavky na spuštění Azure RMS, včetně klienta Azure RMS (není aktivováno)|Viz [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />I když klient Azure RMS musí mít před migrací ze služby AD RMS, doporučujeme, abyste aktivaci služby Rights Management před migrací. Proces migrace zahrnuje tento krok po exportován klíče a šablony ze služby AD RMS a importovat je do Azure RMS. Nicméně pokud je již aktivován Azure RMS, můžete stále migrovat ze služby AD RMS.|
|Příprava pro službu Azure RMS:<br /><br />-   Synchronizaci adresářů mezi vaším místním adresářem a Azure Active Directory<br />-   Poštovní skupiny v Azure Active Directory|Viz [Příprava na Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).|
|Pokud jste použili funkci Správa informačních práv (IRM) systému Exchange Server (například přenosová pravidla a aplikace Outlook Web Access) nebo Server služby SharePoint pomocí služby AD RMS:<br /><br />-   Plán pro krátké době, kdy nebudou mít k dispozici na těchto serverech IRM|Můžete nadále používat IRM na těchto serverech službou Azure RMS po migraci. Jeden z kroků migrace je však dočasně zakázat službu IRM, instalace a konfigurace konektoru, překonfigurujte servery a znovu povolit IRM.<br /><br />Toto je pouze přerušení služby během procesu migrace.|
Omezení:

-   Přestože proces migrace podporuje migraci serveru licencí klíče certifikátu (pro vystavování) do modulu hardwarového zabezpečení (hardwarového zabezpečení) pro službu Azure RMS, Exchange Online aktuálně nepodporuje tuto konfiguraci. Pokud chcete plnou funkčnost IRM se systémem Exchange Online po dokončení migrace do Azure RMS, musí být váš klíč klienta Azure RMS [spravuje Microsoft](http://technet.microsoft.com/library/dn440580.aspx). Alternativně můžete spustit IRM se sníženou funkčností v systému Exchange Online, můžete (BYOK) je spravován vašeho klienta Azure RMS. Další informace o použití Exchange Online službou Azure RMS najdete v části [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration) v těchto pokynů.

-   Pokud máte software a klienti, kteří nejsou podporovány službou Azure RMS, nebudou moci chránit nebo využívat obsah, který je chráněný službou Azure RMS. Zkontrolujte podporovaných aplikací a klienti v oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu.

-   Pokud importujete klíč místně do Azure RMS jako archivují (nenastavíte důvěryhodné domény publikování být aktivní během procesu importu) a migraci uživatelů v dávkách pro Rozfázovaná migrace, obsah, který je nově chráněný migrovaných uživateli nebude dostupný uživatelům, kteří budou nadále služby AD RMS. V tomto scénáři kdykoli je to možné, udržovat krátké době migrace a migraci uživatelů v dávkách logické tak, že pokud spolupráce mezi sebou, jsou migrovány společně.

    Toto omezení se nevztahují při nastavení důvěryhodné domény publikování na aktivní během procesu importu, protože všichni uživatelé budou chránit obsah pomocí stejný klíč. Doporučujeme tuto konfiguraci, protože umožňuje migraci všech uživatelů nezávisle a vlastním tempem.

-   Pokud spolupracovat s externími partnery (například pomocí důvěryhodné domény uživatelů nebo federation), musí také migrovat do Azure RMS buď ve stejnou dobu jako migrace nebo co nejdříve poté. Chcete-li získat přístup k obsahu, které vaše organizace dříve chráněné pomocí služby AD RMS, musí provedou klienta změny konfigurace, které jsou podobné těm, které provedete a zahrnuty v tomto dokumentu.

    Z důvodu variant možné konfigurace, které mohou mít vašich partnerů přesné pokyny pro změnu konfigurace jsou mimo rozsah tohoto dokumentu. O pomoc obraťte se na služby podpory zákazníků společnosti Microsoft (CSS).

## Postup pro migraci služby AD RMS Azure RMS

|Krok migrace|Další informace|
|----------------|-------------------|
|**1. Stáhnout nástroje pro správu Management Azure RMS**|Pokyny naleznete v tématu [Step 1: Download the Azure Rights Management Administration Tool](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step1Migration).|
|**2. Export konfiguračních dat ze služby AD RMS a naimportujte ho do Azure RMS**|Exportovat data konfigurace (klíče, šablony, adresy URL) ze služby AD RMS do souboru XML a odešlete tento soubor do Azure RMS pomocí rutiny prostředí Windows PowerShell pro Import AadrmTpd. Bude nutné provést další kroky v závislosti na konfiguraci klíče služby AD RMS:<br /><br />-   Software chráněn klíč software chráněn klíče migrace: Centrálně spravovány na základě hesla klíče ve službě AD RMS na klíč klienta spravovaného Microsoft Azure RMS. Toto je nejjednodušší způsob migrace a jsou vyžadovány žádné další kroky.<br />-   Chráněné hardwarového zabezpečení klíč chráněné hardwarového zabezpečení klíče migrace: Klíče uložené modul hardwarového zabezpečení pro službu AD RMS na spravované zákazníka klíč klienta Azure RMS ("přineste vlastní klíč" nebo BYOK scénář). To vyžaduje další kroky pro přenos klíče z hardwarového zabezpečení vaší místní společnosti Thales do hardwarového zabezpečení Azure RMS.<br />-   Software chráněn klíč chráněné hardwarového zabezpečení klíče migrace: Centrálně spravovány na základě hesla klíče do služby AD RMS na spravované zákazníka klíč klienta Azure RMS ("přineste vlastní klíč" nebo BYOK scénář). To vyžaduje většina konfigurace, protože musíte nejprve extrahovat softwarový klíč a importovat do modul hardwarového zabezpečení místní a potom proveďte další kroky k přenosu klíč z hardwarového zabezpečení vaší místní společnosti Thales do hardwarového zabezpečení Azure RMS.<br /><br />Pokyny naleznete v tématu [Step 2. Export configuration data from AD RMS and import it to Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step2Migration).|
|**3. Aktivaci vašeho klienta služby RMS**|Pokud je to možné proveďte tento krok po dokončení procesu importu a ne dříve než.<br /><br />Další informace a pokyny naleznete v tématu [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).|
|**4. Konfigurovat importované šablony**|Při importu šablony zásad práv bude archivován jejich stav. Pokud chcete, aby uživatelé mohli zobrazit a jejich použití, musíte změnit na publikovaném na portálu Azure klasické stavu šablony.<br /><br />Pokyny naleznete v tématu [Step 4. Configure imported templates](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step4Migration).|
|**5. Překonfigurujte klientům používat Azure RMS**|Stávající počítače se systémem Windows je třeba nakonfigurovat službu Azure RMS použít namísto služby AD RMS. Tento krok se vztahuje na počítačích ve vaší organizaci a na počítače v partnerských organizací. Jestliže mají spolupracovali s nimi současně byly spuštěny služby AD RMS.<br /><br />Kromě toho, pokud jste nasadili [rozšíření mobilního zařízení](http://technet.microsoft.com/library/dn673574.aspx) pro podporu mobilních zařízení, jako je například telefony iOS a Ipady, Android telefony a tablety, Windows phone a počítače se systémem Mac, je třeba odebrat záznamy SRV služby DNS, které přesměrováno tito klienti používat službu AD RMS.<br /><br />Pokyny naleznete v tématu [Step 5. Reconfigure clients to use Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step5Migration).|
|**6. Konfigurace IRM integrace se systémem Exchange Online**|Tento krok je vyžadován, pokud chcete použít Exchange Online službou Azure RMS.<br /><br />Pokyny naleznete v tématu [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration).|
|**7. Nasazení služby RMS konektoru**|Tento krok je vyžadován, pokud chcete používat kterýkoli z následujících služeb místní službou Azure RMS:<br /><br />-   Exchange Server (například přenosová pravidla a aplikace Outlook Web Access)<br />-   SharePoint Server<br />-   Windows Server, který spouští soubor klasifikace infrastruktury<br /><br />Pokyny naleznete v tématu [Step 7. Deploy the RMS connector](#BKMK_Step7Migration).|
|**8. Vyřazení z provozu služby AD RMS**|Pokud jste potvrdili, že všichni klienti používají Azure RMS a již přístupu k serverům služby AD RMS, můžete vyřadit vaše nasazení služby AD RMS.<br /><br />Pokyny naleznete v tématu [Step 8. Decommission AD RMS](#BKMK_Step8Migration).|
|**9. Znovu klíč klíč klienta Azure RMS**|Tento krok je vyžadován, pokud nebyly systémem v Kryptografickém režimu 2, před migrací a volitelné, ale doporučuje pro všechny migrace k ochraně zabezpečení klíč klienta Azure RMS.<br /><br />Pokyny naleznete v tématu [Step 9. Re-key your Azure RMS tenant key](#BKMK_Step9Migration).|

### <a name="BKMK_Step1Migration"></a>Krok 1: Stáhněte si nástroj pro správu Azure Rights Management
Přejděte na webu Microsoft Download Center a stáhněte [– Nástroj pro správu Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721), která obsahuje modulu správy Azure RMS pro prostředí Windows PowerShell.

### <a name="BKMK_Step2Migration"></a>Krok 2. Export konfiguračních dat ze služby AD RMS a naimportujte ho do Azure RMS
Tento krok je proces dvě části:

1.  Exportujte konfiguračních dat ze služby AD RMS pomocí exportu důvěryhodné domény publikování (důvěryhodné) do souboru XML. Tento proces je stejná pro všechny migrace.

2.  V importu konfiguračních dat pro službu Azure RMS. Existují různé procesy pro tento krok, v závislosti na aktuální konfiguraci nasazení služby AD RMS a topologii upřednostňovaný pro klíč klienta Azure RMS.

#### Export konfiguračních dat ze služby AD RMS
Následující postup na všech clusterech služby AD RMS pro všechny důvěryhodné domény publikování, které mají chráněného obsahu pro vaši organizaci. Nemusíte ji spustit v clusterech jen pro licencování.

> [!NOTE]
> Pokud používáte systém Windows Server 2003 Rights Management, namísto tyto pokyny, postupujte podle pokynů [pro Export vystavování, důvěryhodné domény uživatele, důvěryhodné domény publikování a RMS privátní klíč](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) z [migrace ze systému Windows služby RMS do služby AD RMS v různých infrastruktury](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) tématu.

###### Export dat konfigurace (důvěryhodná publikování informací o domény)

1.  Přihlaste se na cluster AD RMS jako uživatel s AD RMS oprávnění pro správu.

2.  Z konzoly Správa služby AD RMS (**Active Directory Rights Management Services**), rozbalte název clusteru služby AD RMS, rozbalte položku **Zásady důvěryhodnosti**, a potom klikněte na tlačítko **Důvěryhodné domény publikování**.

3.  V podokně výsledků vyberte důvěryhodné domény publikování a potom v podokně Akce klikněte na **Export důvěryhodné domény publikování**.

4.  V **Export důvěryhodné domény publikování** dialogové okno:

    -   Klikněte na tlačítko **Uložit jako** a uložte do cesty a názvu souboru podle vašeho výběru. Nezapomeňte určit **.xml** jako příponu názvu souboru (to nejsou automaticky připojeny).

    -   Zadejte a potvrďte spolehlivé heslo. Vzhledem k tomu, že bude nutné ho později, při importu konfiguračních dat do Azure RMS, mějte na paměti Toto heslo.

    -   Nezaškrtávejte políčko pro uložení souboru důvěryhodné domény v RMS verze 1.0.

Při exportu všechny důvěryhodné domény publikování budete připraveni ke spuštění procedury k importu dat do Azure RMS.

#### V importu konfiguračních dat pro službu Azure RMS
Přesné postupy pro tento krok závisí na aktuální konfiguraci nasazení služby AD RMS a topologii upřednostňovaný pro klíč klienta Azure RMS.

Vaše aktuální nasazení služby AD RMS budou používat jeden z následujících konfigurací pro klíč certifikátu (pro vystavování) poskytuje licence serveru:

-   Ochrana hesla v databázi služby AD RMS. Toto je výchozí konfigurace.

-   Ochrana hardwarového zabezpečení pomocí modulu hardwarového zabezpečení společnosti Thales (hardwarového zabezpečení).

-   Ochrana hardwarového zabezpečení pomocí modulu hardwarového zabezpečení (hardwarového zabezpečení) od dodavatele než společnosti Thales.

-   Heslo chráněn s využitím externí zprostředkovatele kryptografických služeb.

> [!NOTE]
> Další informace o použití modulů hardwaru zabezpečení pomocí služby AD RMS najdete v části [pomocí služby AD RMS s moduly zabezpečení hardwaru](http://technet.microsoft.com/library/jj651024.aspx).

Jsou dvě možnosti klíče topologie klienta Azure RMS: Microsoft spravuje vaše klíč klienta (**Microsoft spravované**) nebo spravovat váš uživatelský klíč pro klienta (**zákazníka spravované**). Když spravujete vlastní klíč klienta Azure RMS, někdy označuje jako "přineste vlastní klíč" (BYOK) a vyžaduje modulu hardwarového zabezpečení (hardwarového zabezpečení) od společnosti Thales. Další informace naleznete v tématu [Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey) v oddílu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tématu.

> [!IMPORTANT]
> Exchange Online není momentálně kompatibilní s Azure RMS BYOK.  Pokud chcete použít BYOK po migraci a plánujete používat Exchange Online, ujistěte se, pochopit, jak tuto konfiguraci omezuje funkčnost IRM pro Exchange Online. Projděte si informace v [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) v oddílu  [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tématu vám pomůžou vybrat nejlepší Azure RMS klienta klíče topologie pro migraci.

Následující tabulku použijte k určení které postup pro migraci. Kombinace, které nejsou uvedeny nejsou podporovány.

|Aktuální nasazení služby AD RMS|Topologie klíče klienta zvolenou Azure RMS|Pokyny k migraci|
|-----------------------------------|----------------------------------------------|--------------------|
|Ochranu heslem v databázi služby AD RMS|Spravované společnosti Microsoft|Viz **Software chráněn klíč software chráněn klíče migrace** postupu po této tabulce.<br /><br />Toto je nejjednodušší cesta migrace a vyžaduje pouze přenosu konfigurační data do Azure RMS.|
|Ochrana hardwarového zabezpečení pomocí modulu hardwarového zabezpečení nShield společnosti Thales (hardwarového zabezpečení)|Spravované zákazníka (BYOK)|Naleznete v části **hardwarového zabezpečení chráněné klíč chráněné hardwarového zabezpečení klíče migrace** postupu po této tabulce.<br /><br />To vyžaduje BYOK sadu nástrojů a dvě sady kroků pro přenos klíče z vaší místní hardwarového zabezpečení do služby RMS Azure, moduly hardwarového zabezpečení a poté přenést konfigurační data na Azure RMS.|
|Ochranu heslem v databázi služby AD RMS|Spravované zákazníka (BYOK)|Viz **Software chráněn klíč chráněné hardwarového zabezpečení klíče migrace** postupu po této tabulce.<br /><br />To vyžaduje, aby se sada nástrojů BYOK a tři sady postup první extrahovat klíče softwaru a importovat jej do modul hardwarového zabezpečení místní poté přenést klíč z vaší místní hardwarového zabezpečení RMS Azure, moduly hardwarového zabezpečení a nakonec přenosu konfigurační data do Azure RMS.|
|Ochrana hardwarového zabezpečení pomocí modulu hardwarového zabezpečení (hardwarového zabezpečení) od dodavatele než společnosti Thales|Spravované zákazníka (BYOK)|Obraťte se na dodavatele pro vás hardwarového zabezpečení pokyny jak přenést váš klíč z tohoto hardwarového zabezpečení do společnosti Thales nShield modulu hardwarového zabezpečení hardwaru (zabezpečení). Postupujte podle pokynů pro **hardwarového zabezpečení chráněné klíč chráněné hardwarového zabezpečení klíče migrace** postupu po této tabulce.|
|Heslo, které jsou chráněné pomocí externího zprostředkovatele kryptografických služeb|Spravované zákazníka (BYOK)|Kontaktujte dodavatele můžete zprostředkovatele kryptografických služeb pokyny jak přenést váš klíč do modulu hardwarového zabezpečení nShield společnosti Thales (hardwarového zabezpečení). Postupujte podle pokynů pro **hardwarového zabezpečení chráněné klíč chráněné hardwarového zabezpečení klíče migrace** postupu po této tabulce.|
Než zahájíte tyto postupy, ujistěte se, že mají přístup k soubory XML, které jste vytvořili dříve při exportu důvěryhodné domény publikování. Například tyto je uložen na USB Flash disk, který přesunete ze serveru služby AD RMS pracovní stanice připojená k Internetu.

> [!NOTE]
> Však uložit tyto soubory, použijte osvědčené postupy zabezpečení pro jejich ochranu, protože tato data zahrnují soukromý klíč.

##### Software chráněn klíč software chráněn klíče migrace
Pomocí tohoto postupu pro import konfigurace služby AD RMS na službu Azure RMS za následek klíč klienta Azure RMS, který je spravovaný nástrojem Microsoft.

###### K importu konfiguračních dat do Azure RMS

1.  Na workstation připojená k Internetu, stáhněte a nainstalujte modul Windows PowerShell pro službu Azure RMS (minimální verze 2.1.0.0), která zahrnuje [Import AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) rutiny.

    > [!TIP]
    > Pokud jste dříve stáhli a nainstalován modul, zkontrolujte číslo verze spuštěním: `(Get-Module aadrm -ListAvailable).Version`

    Instalační pokyny naleznete v tématu [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

2.  Spusťte prostředí Windows PowerShell se **Spustit jako správce** možnost a použít [AadrmService připojit](http://msdn.microsoft.com/library/azure/dn629415.aspx) rutiny připojení ke službě Azure RMS:

    ```
    Connect-AadrmService
    ```
    Po zobrazení výzvy zadejte vaše [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] přihlašovací údaje správce klienta (obvykle použijete účet, který je globální správce pro Azure Active Directory nebo Office 365).

3.  Použití [Import AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) rutiny nahrát první exportovali soubor důvěryhodné domény (XML) publikování. Pokud máte více než jeden soubor .xml, protože mají více důvěryhodných domén pro publikování, zvolte soubor, který obsahuje exportovaný důvěryhodné doméně publikování, kterou chcete použít v Azure RMS k ochraně obsahu po migraci. Pomocí následujícího příkazu:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Příklad: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Po zobrazení výzvy zadejte heslo, které jste dřív zadali a potvrďte, že chcete provést tuto akci.

4.  Po dokončení příkazu, opakujte krok 3 pro každý zbývající soubor .xml, který jste vytvořili pomocí exportu vaší důvěryhodné domény publikování. Tyto soubory nastavení, ale **-Active** k **false** při spuštění příkazu importovat. Příklad: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Použití [odpojení AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) rutiny odpojení od služby Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Nyní jste připraveni k [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Chráněné hardwarového zabezpečení klíč chráněné hardwarového zabezpečení klíče migrace
Je dvě části Postup při importu klíč hardwarového zabezpečení a konfigurace služby AD RMS na službu Azure RMS za následek klíč klienta Azure RMS, který je spravovaný nástrojem je (BYOK).

Nejprve musíte sestavit balíček klíč hardwarového zabezpečení tak, aby byl připraven k přenést Azure RMS a následně ho naimportovat s konfiguračními daty.

###### Část 1: Balíček klíč hardwarového zabezpečení tak, aby byl připraven k přenosu do Azure RMS

1.  Postupujte podle kroků v [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) oddílu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), pomocí postupu **Generovat a přenos váš klient klíčem – přes Internet** s následujícími výjimkami:

    -   Neprovádějte kroky pro **vygenerovat klíč klienta**, protože je již ekvivalent z nasazení služby AD RMS. Je nutné určit klíč používaný serverem služby AD RMS z instalace společnosti Thales a použít tento klíč během migrace. Šifrované soubory klíče jsou obvykle s názvem společnosti Thales **key_(keyAppName)_(keyIdentifier)** místně na serveru.

    -   Neprovádějte kroky pro **přenosu klíč klienta do Azure RMS**, který používá příkaz Přidat AadrmKey.  Místo toho bude přenos klíč připraveného hardwarového zabezpečení při odesílání vašich exportovaný důvěryhodné domény publikování, pomocí příkazu Import AadrmTpd.

2.  Na pracovní stanici připojená k Internetu v relaci prostředí Windows PowerShell, znovu se připojte ke službě Azure RMS.

Teď, když jste připravili klíč hardwarového zabezpečení pro službu Azure RMS, budete připraveni k importu souboru klíče hardwarového zabezpečení a data konfigurace služby AD RMS.

###### Část 2: Importovat hardwarového zabezpečení klíč a konfigurační data do Azure RMS

1.  Stále na pracovní stanici, připojte se k Internetu a v relaci prostředí Windows PowerShell nahrajte první exportovaný soubor důvěryhodné domény publikování (XML). Pokud máte více než jeden soubor .xml, protože mají více důvěryhodných domén pro publikování, zvolte soubor, který obsahuje exportovaný důvěryhodné domény publikování odpovídající klíči hardwarového zabezpečení, který chcete použít v Azure RMS k ochraně obsahu po migraci. Pomocí následujícího příkazu:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Příklad: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Po zobrazení výzvy zadejte heslo, které jste dřív zadali a potvrďte, že chcete provést tuto akci.

2.  Po dokončení příkazu, opakujte krok 1 pro každý zbývající soubor .xml, který jste vytvořili pomocí exportu vaší důvěryhodné domény publikování. Tyto soubory nastavení, ale **-Active** k **false** při spuštění příkazu importovat.  Příklad: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Použití [odpojení AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) rutiny odpojení od služby Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Nyní jste připraveni k [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Software chráněn klíč chráněné hardwarového zabezpečení klíče migrace
Je tři části Postup při importu konfigurace služby AD RMS na službu Azure RMS za následek klíč klienta Azure RMS, který je spravovaný nástrojem je (BYOK).

Musí nejprve extrahovat klíče certifikátu (pro vystavování) vašeho serveru poskytovatel licence z konfiguračních dat a přenos klíče do modul hardwarového zabezpečení společnosti Thales místní pak balíček a přenos vaše hardwarového zabezpečení klíče do služby Azure RMS a poté importovat konfigurační data.

###### Část 1: Extrakce pro vaše vystavování z konfigurační data a importovat klíč do vaší místní hardwarového zabezpečení

1.  Použijte následující kroky v [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) oddílu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tématu:

    -   **Generovat a přenos váš klient klíčem – přes Internet**: **Připravit pracovní stanici připojená k Internetu**

    -   **Generovat a přenos váš klient klíčem – přes Internet**: **Příprava odpojeného pracovní stanice**

    Vzhledem k tomu, že už máte ekvivalent v souboru exportovaný konfigurační data (XML), neprovádějte kroky ke generování klíče vašeho klienta. Místo toho bude spusťte příkaz pro rozbalení tento klíč ze souboru a naimportujte ho do vaší místní hardwarového zabezpečení.

2.  V odpojeném pracovní stanice spusťte následující příkaz:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Například pro Severní Ameriku: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Další informace:

    -   Parametr ImportRmsCentrallyManagedKey znamená, že operace importu pro vystavování klíč.

    -   Pokud nezadáte heslo v příkazu, se výzva k jeho zadání.

    -   Parametr identifikátoru klíče je pro popisný název klíče, který vytvoří název souboru klíče. Je nutné použít pouze malé znaky ASCII.

    -   Parametr ExchangeKeyPackage určuje balíček výměny klíčů specifické pro oblast klíč (KEK), který má název začíná BYOK-KEK - pkg-.

    -   Parametr NewSecurityWorldPackage určuje balíček world specifické pro oblast zabezpečení, který má název začíná BYOK-SecurityWorld - pkg-.

    Tento příkaz způsobí následující:

    -   Soubor klíče hardwarového zabezpečení: %NFAST_KMDATA%\local\key_mscapi_ &lt; ID &gt; klíče

    -   Odebrat datový soubor konfigurace služby RMS pomocí pro vystavování: %NFAST_KMDATA%\local\no_key_tpd_ &lt; ID &gt; klíče .xml

3.  Pokud máte více než jeden RMS konfigurace datové soubory, opakujte krok 2 pro zbývající část těchto souborů.

Vaše pro vystavování extrahovaného tak, aby klíčem na základě hardwarového zabezpečení, můžete začít balíček a přenést na Azure RMS.

###### Část 2: Balíček a přenos vaše hardwarového zabezpečení klíče do služby Azure RMS

1.  Postupujte podle následujících kroků z [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) oddílu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Generovat a přenos váš klient klíčem – přes Internet**: **Připravte váš klíč klienta pro přenos**

    -   **Generovat a přenos váš klient klíčem – přes Internet**: **Přenos vašeho klienta klíče do služby Azure RMS**

Klíč hardwarového zabezpečení jste přenese na Azure RMS, můžete začít importovat konfigurační data služby AD RMS, který obsahuje pouze ukazatel na klíč nově přenesené klienta.

###### Část 3: V importu konfiguračních dat pro službu Azure RMS

1.  Stále na pracovní stanici připojená k Internetu a v relaci prostředí Windows PowerShell zkopírujte přes RMS konfigurační soubory s pro vystavování odebrán (z odpojeného pracovní stanice, %NFAST_KMDATA%\local\no_key_tpd_ &lt; ID &gt; klíče .xml)

2.  První soubor odešlete. Pokud máte více než jeden soubor .xml, protože mají více důvěryhodných domén pro publikování, zvolte soubor, který obsahuje exportovaný důvěryhodné domény publikování odpovídající klíči hardwarového zabezpečení, který chcete použít v Azure RMS k ochraně obsahu po migraci. Pomocí následujícího příkazu:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Příklad: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Po zobrazení výzvy zadejte heslo, které jste dřív zadali a potvrďte, že chcete provést tuto akci.

3.  Po dokončení příkazu, opakujte krok 2 pro každý zbývající soubor .xml, který jste vytvořili pomocí exportu vaší důvěryhodné domény publikování. Tyto soubory nastavení, ale **-Active** k **false** při spuštění příkazu importovat. Příklad: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Použití [odpojení AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) rutiny odpojení od služby Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Nyní jste připraveni k [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

### <a name="BKMK_Step3Migration"></a>Krok 3. Aktivaci vašeho klienta služby RMS
Pokyny pro tento krok jsou plně popsány v [Aktivace Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md) tématu.

> [!TIP]
> Pokud máte předplatné Office 365, můžete aktivovat Azure RMS z centra pro správu služeb Office 365 nebo klasické portálu Azure. Doporučujeme používat portál Azure klasické vzhledem k tomu, že budete používat tento portál pro správu k dokončení na další krok.

**Co dělat, pokud je již aktivován vašeho klienta Azure RMS?** Pokud službu Azure RMS je již aktivován pro vaši organizaci, uživatelé již použili Azure RMS k ochraně obsahu s klíčem automaticky generované klienta (a výchozí šablony) namísto existující klíče (a šablony) ze služby AD RMS. Toto je nepravděpodobné, že probíhat na počítačích, které jsou dobře spravované v síti intranet, protože budou mít automaticky nastaven pro infrastrukturu služby AD RMS. Ale může dojít v počítačích pracovní skupiny nebo počítače, které zřídka připojení k síti intranet. Bohužel je také obtížné určit tyto počítače, což je důvod, proč doporučujeme, abyste že před importem dat konfigurace ze služby AD RMS neaktivujete služby.

Pokud váš klient Azure RMS je již aktivován a můžete určit tyto počítače, ujistěte se, spusťte skript CleanUpRMS_RUN_Elevated.cmd v těchto počítačích, jak je popsáno v kroku 5. Spuštěním tohoto skriptu vynutí je znovu inicializovat uživatelské prostředí, takže stáhnou klíč aktualizované klienta a importované šablony.

### <a name="BKMK_Step4Migration"></a>Krok 4. Konfigurovat importované šablony
Protože šablony, které jste importovali mají výchozí stav **archivované**, je nutné změnit tento stav bude **Publikováno** Pokud chcete, aby uživatelé mohli použít tyto šablony s Azure RMS.

Kromě toho, pokud vaše šablony ve službě AD RMS používat **ANYONE** skupiny, tato skupina automaticky odebrána při importu šablon do Azure RMS, je třeba ručně přidat ekvivalentní skupiny nebo uživatelé a stejná práva na importované šablony. Ekvivalentní skupiny pro službu Azure RMS je s názvem **AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com**. Například tato skupina může vypadat jako následující pro společnosti Contoso: **AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com**.

Pokud si nejste jisti, zda vaše šablony služby AD RMS obsahují skupiny KDOKOLI, rozbalte  [PowerShell script to identify AD RMS templates that include the ANYONE group](#BKMK_ScriptForANYONE) části v tomto kroku kopírovat a používat ukázkový skript PowerShell k identifikaci těchto šablon. Další informace o použití prostředí Windows PowerShell s služby AD RMS naleznete v tématu  [pomocí prostředí Windows PowerShell Správa služby AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Uvidíte organizaci uživatele automaticky vytvořeno skupiny, je-li zkopírovat jeden výchozí šablony zásad práv na portálu Azure klasické a určete, **uživatelské jméno** na **práva** stránky. Však nelze použít na klasické portálu pro tuto skupinu přidat do šablony, která nebyla vytvořena ručně nebo naimportována a místo toho musíte použít jeden z následujících možností Azure RMS PowerShell:

-   Použití [Nový AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) rutiny prostředí PowerShell definovat skupiny "AllStaff" a práva jako objekt definice práva a spusťte tento příkaz znovu pro každou z jiných skupin nebo uživatelů již udělena práva v původní šabloně kromě ANYONE skupiny. Potom přidejte všechny tyto objekty definice práva k šablonám pomocí  [Set AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx) rutiny.

-   Použití [Export AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) rutiny exportovat šablonu, kterou chcete. Soubor XML, který můžete upravit přidat skupinu "AllStaff" a práva k stávajících skupin a oprávnění a pak použít [Import AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) rutiny Import této změny zpět do Azure RMS.

> [!NOTE]
> Tato skupina "AllStaff" ekvivalentní není přesně stejná jako skupina ANYONE ve službě AD RMS:  "AllStaff" skupina zahrnuje všechny uživatele ve vašem klientovi Azure, že skupina každý, KDO zahrnuje všechny ověřeným uživatelům, kteří by mohla být mimo vaši organizaci.
> 
> Tento rozdíl mezi dvěma skupinami je nutné také přidat externí uživatelé kromě skupiny "AllStaff". Externí e-mailové adresy pro skupiny nejsou aktuálně podporovány.

Šablony, které importujete ze služby AD RMS vypadat a fungovat stejně jako vlastní šablony, které můžete vytvářet klasické portálu Azure. Změny importované šablony publikována, a uživatelé mohou vidět a vyberte je z aplikací nebo provádění jiných změn do šablon naleznete v tématu [Konfigurace vlastních šablon pro Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

> [!TIP]
> Pro více jednotné prostředí pro uživatele během procesu migrace neprovádějte změny importované šablony než tyto dvě změny; a není publikovat dvě výchozí šablony, které jsou součástí Azure RMS, nebo vytvořit nové šablony v tomto okamžiku. Místo toho Počkejte, až po dokončení procesu migrace a mít vyřadit z provozu serverů AD RMS.

#### <a name="BKMK_ScriptForANYONE"></a>Ukázkový skript prostředí Windows PowerShell k identifikaci šablony služby AD RMS, které zahrnují ANYONE skupiny
Tato část obsahuje ukázkový skript, které vám pomohou identifikovat šablony služby AD RMS, které mají skupině ANYONE definována, jak je popsáno v předchozím oddílu.

*&#42;&#42;Zřeknutí se práv:&#42;&#42; Tento ukázkový skript není podporován v rámci jakékoli Microsoft standardního programu či služby podpory. Tento ukázkový skript jsou poskytovány tak, jak je bez záruky jakéhokoli druhu.*

```
import-module adrmsadmin New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force $ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate foreach($Template in $ListofTemplates) { $templateID=$Template.id $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright $templateName=$Template.DefaultDisplayName if ($rights.usergroupname -eq "anyone") { $templateName = $Template.defaultdisplayname write-host "Template " -NoNewline write-host -NoNewline $templateName -ForegroundColor Red write-host " contains rights for " -NoNewline write-host ANYONE  -ForegroundColor Red } } Remove-PSDrive MyRmsAdmin -force
```

### <a name="BKMK_Step5Migration"></a>Krok 5. Překonfigurujte klientům používat Azure RMS
Pro klienty systému Windows:

1.  [Stáhnout migrační skripty](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Tyto skripty obnovit konfiguraci v počítačích se systémem Windows, takže budou používat služby Azure RMS místo služby AD RMS.

2.  Postupujte podle pokynů ve skriptu přesměrování (Redirect_OnPrem.cmd) Chcete-li upravit skript tak, aby odkazoval na váš nový klient Azure RMS.

3.  V počítači se systémem Windows spusťte tyto skripty se zvýšenými oprávněními v kontextu uživatele.

Pro klienty mobilních zařízení a počítačů se systémem Mac:

-   Odebrat záznamy SRV služby DNS, které jste vytvořili při nasazení [rozšíření služby AD RMS pro mobilní zařízení](http://technet.microsoft.com/library/dn673574.aspx).

#### Změny provedené při migrační skripty
Tato část obsahuje změny, které provedou migrační skripty. Tyto informace můžete použít pouze pro referenční účely nebo pro řešení potíží nebo pokud chcete tyto změny sami.

CleanUpRMS_RUN_Elevated.cmd:

-   Odstranění obsahu složky %userprofile%\AppData\Local\Microsoft\DRM a %userprofile%\AppData\Local\Microsoft\MSIPC, včetně všech podsložek a souborů s dlouhé názvy souborů.

-   Odstraňte obsah následující klíče registru:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Odstraňte následující hodnoty registru:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Vytvořte následující hodnoty registru pro každou adresu URL zadána jako parametr pod každým z následujících umístění:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Každý záznam obsahuje hodnotu REG_SZ z **https://OldRMSserverURL/_wmcs/licensing** s daty v následujícím formátu: **https://&lt;YourTenantURL&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt; YourTenantURL &gt;* má následující formát: **{GUID} .rms. [Oblast].aadrm.com**.
    > 
    > Příklad:  5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Tuto hodnotu můžete najít určením **RightsManagementServiceId** hodnota při spuštění [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) rutiny pro Azure RMS.

### <a name="BKMK_Step6Migration"></a>Krok 6. Konfigurace integrace IRM pro Exchange Online
Pokud jste dříve naimportovali vaše TDP ze služby AD RMS na Exchange Online, musíte odebrat tato TDP, aby se zabránilo zásady konfliktní šablony a poté, co jste provedli migraci na Azure RMS. Chcete-li to provést, použijte [Odebrat RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) rutiny z Exchange Online.

Pokud jste zvolili Azure RMS klienta klíče topologii **Microsoft spravované**:

-   Naleznete v části [Exchange Online: Konfigurace IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline) v oddílu [Konfigurace aplikací pro Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) tématu. Tato část obsahuje typické příkazy ke spuštění, které připojuje ke službě Exchange Online, naimportuje klíč klienta z Azure RMS a aktivuje funkce IRM pro Exchange Online. Po dokončení těchto kroků bude mít plnou funkčnost serveru RMS se systémem Exchange Online.

Pokud jste zvolili Azure RMS klienta klíče topologii **zákazníka spravované (BYOK)**:

-   Bude mít snížením funkce RMS pomocí Exchange Online, jak je popsáno v [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) v oddílu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tématu.

### <a name="BKMK_Step7Migration"></a>Krok 7. Nasazení služby RMS konektoru
Pokud jste použili funkci Správa informačních práv (IRM) systému Exchange Server nebo Server služby SharePoint pomocí služby AD RMS, musíte nejprve zakázat IRM na těchto serverech a odebrat konfiguraci služby AD RMS. Pak nasaďte konektor Rights Management (RMS), který funguje jako komunikační rozhraní (předávání) mezi místními servery a Azure RMS.

Nakonec pro tento krok, pokud jste importovali více důvěryhodných domén publikování do Azure RMS, které byly použity k ochraně e-mailové zprávy, je nutné ručně upravit registru v počítačích systému Exchange Server přesměrovat všechny adresy URL důvěryhodných domén publikování do konektoru služby RMS.

> [!NOTE]
> Než začnete, zkontrolujte v podporovaných verzích systému na místní servery, které konektor služby RMS podporuje v "místní servery, které podporují Azure RMS" [Aplikace, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu.

##### Zakázat IRM na serverech Exchange a odebrat konfigurace služby AD RMS

1.  Na každý server Exchange, vyhledejte následující složku a odstranit všechny položky v této složce: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Z jednoho z servery Exchange pomocí Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) rutiny nejdříve zakázat IRM funkce pro zprávy, které jsou odeslány příjemcům interní:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Pak pomocí stejné rutiny zakázat funkce IRM pro zprávy, které byly odeslány na externí příjemci:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Dále pomocí stejné rutiny, která můžete zakázat IRM v aplikaci Microsoft Office Outlook Web App a Microsoft Exchange ActiveSync:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Nakonec pomocí stejné rutiny zrušte všechny certifikáty, uložené v mezipaměti:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Na každý Server Exchange nyní obnovit službu IIS, například spuštěním příkazového řádku jako správce a zadáním příkazu **iisreset**.

##### Zakázat IRM na serverech služby SharePoint a odebrat konfigurace služby AD RMS

1.  Ujistěte se, že neexistují žádné dokumenty rezervován z chráněného službou RMS knihoven. Pokud existují, se budou nepřístupné na konci tohoto postupu.

2.  Na SharePoint webové aplikace Centrální správy lokality, ve **Snadné spuštění** klepněte na **zabezpečení**.

3.  Na **zabezpečení** stránce **informace zásady** klepněte na **Konfigurovat správu přístupových práv**.

4.  Na **informace Rights Management** stránce **informace Rights Management** vyberte **nepoužívejte IRM na tomto serveru**, klikněte na tlačítko **OK**.

5.  Na všech počítačích serveru SharePoint, odstraňte obsah složky \ProgramData\Microsoft\MSIPC\Server\*&lt; SID účtu systémem SharePoint Server &gt;*.

##### Nainstalujte a nakonfigurujte konektor server RMS

-   Postupujte podle pokynů v [Nasazení konektoru Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) tématu.

##### Pro výměnu pouze a více důvěryhodných domén publikování: Úprava registru

-   Na každý Server Exchange ručně přidejte následující klíče registru pro každý další důvěryhodné domény publikování, který jste importovali přesměrování adresy URL důvěryhodné domény publikování do konektoru služby RMS. Tyto položky registru jsou specifické pro migraci a nebudou přidány pomocí nástroje Konfigurace serveru pro konektor Microsoft RMS.

    Pokud provedete tyto úpravy registru, použijte následující pokyny:

    -   Nahraďte *ConnectorFQDN* s názvem, který jste definovali ve službě DNS pro konektor. Například **rmsconnector.contoso.com**.

    -   Použijte předponu protokolu HTTP nebo HTTPS pro adresu URL konektor, v závislosti na tom, zda jste nakonfigurovali konektor na používání protokolu HTTP nebo HTTPS pro komunikaci se na místní servery.

    **Pro server Exchange 2013:**

    |Cesta v registru|Typ|Hodnota|Data|
    |--------------------|-------|-----------|--------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|REG_SZ|https://&lt;AD RMS intranetu licencování URL &gt;/_wmcs/licensing|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze systému Exchange server do konektoru služby RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|REG_SZ|Adresa URL pro extranetu licencování RMS https://&lt;AD &gt;/_wmcs/licensing|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze systému Exchange server do konektoru služby RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorFQDN&gt;/_wmcs/licensing|
    **Pro Exchange Server 2010:**

    |Cesta v registru|Typ|Hodnota|Data|
    |--------------------|-------|-----------|--------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|REG_SZ|https://&lt;AD RMS intranetu licencování URL &gt;/_wmcs/licensing|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze systému Exchange server do konektoru služby RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|REG_SZ|Adresa URL pro extranetu licencování RMS https://&lt;AD &gt;/_wmcs/licensing|Jedna z následujících akcí v závislosti na tom, zda používáte protokol HTTP nebo HTTPS ze systému Exchange server do konektoru služby RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|

Po dokončení těchto postupů nezapomeňte si přečíst **Další kroky** v oddílu [Nasazení konektoru Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) tématu.

### <a name="BKMK_Step8Migration"></a>Krok 8. Vyřazení z provozu služby AD RMS
Volitelné: Odeberte bod připojení služby (SCP) ze služby Active Directory pro počítače zabránit zjišťování vaše místní infrastruktura Rights Management. Toto je volitelné kvůli přesměrování, který jste nakonfigurovali v registru (například spuštěním skriptu migrace). Chcete-li odebrat spojovací bod služby, použijte nástroj zaregistrovat spojovací bod služby AD z [Rights Management Services správu Toolkit](http://www.microsoft.com/download/details.aspx?id=1479).

Monitorovat své servery služby AD RMS pro aktivity, například kontrolou [požadavků v sestavě stavu systému](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx),  [tabulky elementu ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) nebo [auditování přístupu uživatelů k chráněného obsahu](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Pokud jste potvrdili, že jsou klienti služby RMS již komunikuje s tyto servery a aby klienti úspěšně používá Azure RMS, můžete odebrat roli serveru služby AD RMS z těchto serveru. Pokud používáte vyhrazené servery, můžete dát přednost vytvořených krok první vypíná servery časovém intervalu a ujistěte se, že neexistují žádné ohlášené problémy, které mohou vyžadovat restartování tyto servery, chcete-li zajistit kontinuitu služeb, zatímco prozkoumat proč klienti nepoužíváte Azure RMS.

Po vyřazení z provozu vaše servery služby AD RMS, můžete chtít využijte příležitosti a zkontrolujte své šablony portálu Azure klasické a konsolidovat je, aby uživatelé měli méně volit mezi, nebo je překonfigurujte nebo dokonce přidat nové šablony. To by také včas publikovat výchozí šablony. Další informace naleznete v tématu [Konfigurace vlastních šablon pro Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

### <a name="BKMK_Step9Migration"></a>Krok 9. Znovu klíč klíč klienta Azure RMS
Tento krok je vyžadován po dokončení migrace používáte-li vaše nasazení služby AD RMS byl RMS kryptografických režimu 1, protože opětovného zadávání vytvoří nový klíč klienta, který používá RMS kryptografický režim 2. Azure RMS pomocí kryptografických režimu 1 je podporována pouze během procesu migrace.

Tento krok je nepovinný, ale doporučuje při dokončení migrace i v případě, že byly spuštěny v RMS Kryptografickém režimu 2, protože pomáhá zabezpečit klíč klienta Azure RMS z možných porušení zabezpečení služby AD RMS klíč. Když znovu klíč klíč klienta Azure RMS (také označované jako "postupných klíč"), je vytvořen nový klíč a původní klíč bude archivován. Vzhledem k tomu, že přesunutí z jeden klíč na jiný nejsou provedeny okamžitě, ale během několika týdnů, není Počkejte, dokud však podezření, že porušení původní klíč ale co nejdříve po dokončení migrace znovu klíč klíč klienta služby RMS.

Chcete-li znovu klíč klíč klienta Azure RMS:

-   Pokud váš klíč klienta služby RMS je spravováno společností Microsoft: Volání služby podpory zákazníků společnosti Microsoft (CSS) a prokázat, že jste správce klienta služby RMS.

-   Pokud váš klíč klienta služby RMS spravuje můžete (BYOK): Opakujte postup BYOK generovat a vytvořte nový klíč přes Internet nebo osobní.

Další informace o správě klíč klienta služby RMS najdete v části [Operace pro klíč klienta Azure Rights Management](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

