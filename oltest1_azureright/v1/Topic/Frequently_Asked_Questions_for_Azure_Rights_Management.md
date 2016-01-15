---
description: na
keywords: na
title: Frequently Asked Questions for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Nejčastějš&#237; dotazy pro Azure Rights Management
Některé nejčastější dotazy pro Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], označovaný také jako Azure RMS:

## Co je třeba nasadit Azure RMS a jak I začít?
Nejprve, zkontrolujte [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md), který má informace o možnosti odběru cloudu, použití serverů místní službou Azure RMS, které scénáře nasazení není aktuálně podporována, zařízení, která a podpora aplikace Azure RMS a odkaz Pokud potřebujete seznam IP adres a názvů domén pro brány firewall nebo proxy servery. Můžete také vrátit se změnami v ostatních tématech [Začínáme s Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md) části, chcete-li získat základní znalosti o tom, jak [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] může pomoci chránit data vaší organizace, jak funguje s aplikacemi, jak porovnává s místní verzí služby Active Directory Rights Management a pochopit podmínky a zkratky, které jsou specifické pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Pak když budete chtít test Azure RMS pro sebe, nebo ho nasadit pro vaši organizaci, použít [Plán nasazení Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) seznam kroky s odkazy na další informace a postupy pokyny.

Pokud potřebujete další informace, materiály a možnosti podpory, najdete v části [Informace a podpora nástroje Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Můžete integrovat Azure RMS se mé na místní servery?
(Ano). Azure RMS lze integrovat s vaší místní serverů, například souborové servery Exchange Server, SharePoint a systému Windows. Chcete-li to provést, použijte [konektor Rights Management](https://technet.microsoft.com/library/dn375964.aspx). Nebo, pokud vás zajímá pouze pomocí souboru klasifikace infrastruktury (FC) v systému Windows Server, můžete použít [ochranu RMS rutin](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). Můžete synchronizovat a vytvořit federaci řadičích domény služby Active Directory s Azure AD pro lepší zkušenosti ověřování pro uživatele, například pomocí [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Azure RMS automaticky generuje a spravuje certifikáty XrML podle potřeby, takže nepoužívá k místní PKI. Další informace o tom, jak Azure RMS používá certifikáty naleznete v tématu [Návod, jak pracuje Azure RMS: Nejprve použít, obsahu ochrany obsahu spotřeba](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Walthrough) v oddílu [Co je Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tématu.

## Hybridní nasazení systému Exchange je nutné s některým uživatelům na Exchange Online a ostatním uživatelům na serveru Exchange Server – je to podporován službou Azure RMS?
Absolutně a dobrý věc je, že uživatelé budou moci bez problémů chránit a využívat chráněné e-maily a přílohy přes dvě nasazení systému Exchange. Pro tuto konfiguraci [Aktivovat Azure RMS](https://technet.microsoft.com/library/jj658941.aspx) a [Povolit IRM pro Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), pak [nasazení a konfigurace konektoru služby RMS](https://technet.microsoft.com/library/dn375964.aspx) for Exchange Server.

## Je-li nasadit službu Azure RMS v produkčním prostředí, je naše společnost pak uzamčen do řešení nebo riziko ztráty přístupu k obsahu, který jsme chráněné službou Azure RMS?
Ne, je vždy zůstávají v ovládacím prvku dat a můžete nadále přistupovat, i když se rozhodnete již nebudete používat Azure RMS. Další informace naleznete v tématu [Vyřazování z provozu a deaktivace Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Nicméně před vyřazení z provozu Azure RMS nasazení rádi bychom znát váš názor a pochopit, proč jste provedli toto rozhodnutí. Pokud Azure RMS nesplňuje požadavky vaší organizace, kontaktujte nás v případě, že je plánováno nové funkce pro téměř budoucnost, nebo pokud existují alternativy. Odeslat e-mailovou zprávu na [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) a jsme bude potěšením prodiskutovat vašim technickou a podnikovým požadavkům.

## Můžete ovládat, který vlastní uživatelé používají Azure RMS k ochraně obsahu?
Ano, Azure RMS má uživatelské ovládací prvky registrace pro tento scénář. Další informace naleznete v tématu [Registrace ovládacích prvků pro dvoufázové nasazení konfigurace](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) v oddílu [Aktivace Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md) tématu.

## Můžete zabránit uživatelům v sdílení chráněné dokumenty s konkrétní organizace?
Jednou z největších výhod Azure RMS je, aniž by bylo nutné konfigurovat explicitní vztahy důvěryhodnosti pro každou organizaci partnera, protože Azure AD postará ověřování pro vás podpora obchodní obchodní spolupráci.

Neexistuje žádná možnost správy uživatelům zabránit v bezpečně sdílení dokumentů s konkrétní organizace. Například chcete zablokovat organizace, která nedůvěřujete nebo má konkurenčních business. Brání odeslání chráněné dokumenty uživatelům v těchto Azure RMS organizace by smysl vzhledem k tomu, že uživatelé by pak sdílet své dokumenty nechráněné, což je pravděpodobně poslední věcí, kterou se má stát v tomto scénáři! Například nebude moci zjistit, kdo je sdílení společnosti důvěrné dokumenty s kteří uživatelé v těchto organizací, které můžete dělat při dokumentu (nebo e-mailu) je chráněné službou Azure RMS.

## Při sdílení chráněný dokument s někým nepracují ve firmě, jak tento uživatel získat ověřený?
Azure RMS vždy používá účet Azure Active Directory a přidružené e-mailovou adresu pro ověření uživatele, díky bezproblémové spolupráci business business pro správce. Pokud organizace používá služby Azure, uživatelé již mají účty v Azure Active Directory, i když tyto účty jsou vytvořeny a spravovaný na místní a potom synchronizovat do Azure.  Pokud je v organizaci služeb Office 365 pod kapotou architektury, tato služba také používá Azure Active Directory pro uživatelské účty.  Pokud organizace uživatele nemá spravované účty v Azure, uživatelé si zaregistrovat [RMS pro jednotlivce](https://technet.microsoft.com/library/dn592127.aspx), což vytvoří adresář pro organizaci a technologie nespravované klientovi Azure pomocí účtu pro uživatele, tak, aby tohoto uživatele mohou být ověřeny pak pro Azure RMS.

Metoda ověřování u těchto účtů se může lišit v závislosti na konfiguraci správce v jiné organizaci účty Azure Active Directory. Například může používají hesla, které byly vytvořeny pro tyto účty, vícefaktorového ověřování (MFA), federace nebo hesla, které byly vytvořeny ve službě Active Directory Domain Services a potom synchronizovat do Azure Active Directory.

## Můžete přidat uživatele z nepracují ve firmě na vlastní šablony?
(Ano).  Vytváření vlastních šablon, které můžete vybrat koncoví uživatelé (a správci) z aplikací, které umožňuje rychlý a snadno používat ochrana informací pomocí předdefinovaných zásad, které zadáte. Jedním z nastavení v šabloně je, kdo má přístup k obsahu a můžete určit uživatele a skupiny z v rámci vaší organizace a uživatele z mimo vaši organizaci.

Chcete-li určit uživatele z mimo vaši organizaci, použijte [modul Windows PowerShell pro Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx). Můžete použít jednu z těchto možností:

-   **Exportu, úpravy a importu aktualizované šablony**:  Toto je nejjednodušší způsob, pokud chcete přidat do existující šablonu, která zahrnuje další skupiny tyto externí uživatelé. Použití [Export AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) rutiny exportovat šablonu, kterou chcete. Soubor CSV, který lze upravovat přidat externí e-mailové adresy tito uživatelé a jejich práva na stávajících skupin a oprávnění. Potom pomocí [Import AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) rutiny Import této změny zpět do Azure RMS.

-   **Použití definice objektu práva k vytvoření nebo aktualizace šablony**:    Zadejte externí e-mailové adresy a jejich práva v definici objektu práva, které poté můžete vytvořit nebo aktualizovat šablonu. Zadejte definici objektu práva pomocí [Nový AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) rutiny vytvořit proměnnou a poté poskytnout tuto proměnnou na parametr - RightsDefinition s [Přidat AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) rutiny (pro novou šablonu) nebo [Set AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) rutiny (Pokud modifikujete existující šablony). Nicméně pokud přidáváte tito uživatelé do stávající šablony, budete muset definice práva definice objektů pro stávajících skupin v šablonách a nikoli pouze externí uživatelé.

Další informace o vlastních šablon naleznete v tématu [Konfigurace vlastních šablon pro Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

## Jaká zařízení a které typy souborů jsou podporovány službou Azure RMS?
Seznam podporovaných zařízení najdete v části [Klientská zařízení, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) v oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu. Vzhledem k tomu, že všechny podporované zařízení aktuálně podporuje všechny možnosti RMS, nezapomeňte také zkontrolovat, zda [Možnosti zařízení klienta](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) tabulky ve stejné téma.

Azure RMS může podporovat všechny typy souborů. Pro text, obrázek, aplikace Microsoft Office (Word, Excel, PowerPoint) soubory, soubory .pdf a některé typy souborů jiných aplikací poskytuje Azure RMS nativní ochrany, která zahrnuje šifrování a prosazování práv (oprávnění). Pro všechny ostatní aplikace a typy souborů poskytuje Obecná ochrana souboru zapouzdření a ověřování k ověření, pokud je uživatel autorizovaný k otevření souboru.

Seznam přípon souborů, které jsou nativně podporovaný službou Azure RMS, naleznete [podporované typy souborů a přípony názvů souborů](http://technet.microsoft.com/library/dn339003.aspx) oddílu [Příručka správce aplikace pro sdílení obsahu Rights Management](http://technet.microsoft.com/library/dn339003.aspx). Neuvedené přípony názvů souborů jsou podporovány pomocí aplikace, která automaticky použije Obecná ochrana pro tyto soubory pro sdílení obsahu RMS.

## Pokud bude podporovat migrace ze služby AD RMS?
Zpočátku nebyl Azure RMS podporuje migraci z místního nasazení služby Rights Management, jako je například služba AD RMS. Ale je nyní podporován.

Další informace naleznete v tématu [Migrace ze služby AD RMS na Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

## Jsme Opravdu chcete použít BYOK službou Azure RMS, ale se naučili, že to není kompatibilní se systémem Exchange Online – co je vaše Rady?
Nenechte toto aktuální omezení zpoždění nasazení Azure RMS. Pokud máte Exchange Online a chcete použít převést vlastní klíč (BYOK), doporučujeme nasadit službu Azure RMS ve výchozím režimu správy klíčů nyní, kde společnost Microsoft generuje a spravuje váš klíč. Tímto způsobem získáte všechny výhody chrání důležité soubory a e-mailů nyní, s možností přejít BYOK později (například když Exchange Online podporu BYOK).

Pokud zásady vaší společnosti vyžadují, abyste pomocí modulu hardwarového zabezpečení (hardwarového zabezpečení), a to by jinak blokovat nasazení Azure RMS, Další možností je však nasazení Azure RMS s BYOK nyní, s omezenou funkčností RMS pro server Exchange. Další informace naleznete v tématu [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) v oddílu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tématu.

## Funkce hledám asi není, pracovat se službou SharePoint chráněných knihoven – podpora pro moje funkce plánované?
V současné době RMS chráněné dokumenty podporuje služby SharePoint pomocí IRM chráněná knihovny, které nepodporují vlastní šablony, pro sledování dokumentů a některé další možnosti.  Další informace, rozbalte   [SharePoint Online a Onedrivem pro společnost: Konfigurace IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) v oddílu [Jak aplikace podporují Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md) tématu.

Pokud vás zajímají specifické možnosti, která ještě není podporována, je nutné sledovat na oznámení [blog týmu služby RMS](http://blogs.technet.com/b/rms/).

## Jak lze nakonfigurovat jednu jednotku pro firmy ve službě SharePoint Online tak, aby uživatelé mohou bezpečně sdílet své soubory s uživatelů uvnitř i vně společnosti?
Ve výchozím nastavení jako správce služeb Office 365, nekonfigurujete uživatelé provádět.

Stejně jako správce webu služby SharePoint povolí a nakonfiguruje IRM knihovny služby SharePoint, kterou vlastní, Onedrivu pro firmy je určena uživatelům povolit a konfigurovat IRM pro své vlastní Onedrivu pro firmy knihovny.  Však pomocí prostředí PowerShell, můžete to provést u nich. Pokyny, rozbalte [SharePoint Online a Onedrivem pro společnost: Konfigurace IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline)  kapitoly [Konfigurace aplikací pro Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) článku.

## Máte k dispozici žádné tipy nebo tipy pro úspěšné nasazení služby RMS?
Po nasazení velkého počtu dohled nad a naslouchá na našich zákazníků, partnery, konzultanti a pracovníky technické podpory – jedním z největších tipů, které nám můžete předat na z zaznamenat: **Návrhu a nasazení zásad jednoduchá práva**.

Protože Azure RMS podporuje sdílení bezpečně s kýmkoli, můžete si může dovolit být náročných s svůj dosah ochrany informací. Ale uvážlivě s vašimi zásadami práva. Pro mnoho organizací největší dopad na chod firmy pochází z zabránit úniku dat při použití výchozí šablony zásad práv, která omezuje přístup lidem ve vaší organizaci. Samozřejmě, můžete získat podrobnější než, pokud je potřeba – zabránit neoprávněným osobám v tisk, úpravy atd. Ale ponechat podrobnější omezení jako výjimka pro dokumenty, které skutečně potřebujete vysoké úrovně zabezpečení a neimplementují tyto přísnější zásady na jeden den, ale plán pro více několika fází rozdělený postup.

## Jaké funkce lze nebo nelze použít s jinou odběry Azure RMS?
Pro placené předplatné, které podporují Azure RMS (Office 365, Azure RMS Premium a sada Enterprise Mobility) jsou určité rozdíly v RMS funkce, které jsou podporovány. Seznam naleznete v tématu [Rights Management Services (RMS)-porovnání nabídek](http://technet.microsoft.com/dn858608).

Bezplatné předplatné, který podporuje Azure RMS (RMS pro jednotlivce) podporuje náročné obsah, který je chráněný službou Azure RMS. Další informace naleznete v tématu [RMS pro jednotlivce i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Kde lze získat technické informace o bezplatné předplatné Azure RMS (RMS pro jednotlivce) – například jak skutečně funguje, jak řídit účty a které domény nelze použít?
Zjistíte odpovědi na tyto otázky v [RMS pro jednotlivce i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md) tématu.

## Jak jsme získat přístup k souborům, které byly chráněny zaměstnanci, který nyní opustil organizaci?
Použijte funkci superuživatele Azure RMS, který umožní oprávněným uživatelům mít úplná vlastnická práva na všechny licence udělená pomocí klienta služby RMS vaší organizace. Tato funkce stejný index ověřených služby umožňuje a kontrola souborů, podle potřeby.

Další informace naleznete v tématu [Konfigurace tito uživatelé pro Azure Rights Management a zjišťování služeb nebo obnovení dat](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

## Rights Management může zabránit zachycení obrazovky?
Správa přístupových práv blokovat zachycení obrazovky od většiny nástrojů zachycení běžně používané obrazovky, které může pomoci, aby se zabránilo náhodnému nebo z nedbalosti zveřejnění důvěrné nebo citlivé informace. Existují však mnoha způsoby, že uživatel může sdílet data, která se zobrazí na obrazovce, a zabírá snímek obrazovky pouze jednu metodu. Uživatel s úmyslem sdílení zobrazené informace můžete například pořídit snímek pomocí svůj telefon fotoaparátu, znovu zadávat data nebo jednoduše ústně předávají někomu.

Tyto příklady ukazují, jak je technologie samostatně nemůže vždy uživatelům zabránit sdílení dat, která by neměly. Zatímco Rights Management může pomoci k ochraně důležitých dat s použitím autorizace a zásad použití, je třeba použít toto řešení správy práv enterprise s jinými ovládacími prvky. Například implementaci fyzické zabezpečení, pečlivě obrazovky a sledování uživatelů, kteří mají oprávnění přístupu k datům vaší organizace a investovat do vzdělávání uživatelů uživatelům pochopit, jaká data by se neměly sdílet.

## Kde lze najít informace o podpoře pro Azure RMS – například právní, dodržování předpisů a SLA?
Azure RMS podporuje další služby a také závisí na jiné služby. Pokud hledáte informace týkající se na službu Azure RMS, ale nikoli o tom, jak pomocí služby Azure RMS, zkontrolujte následující prostředky:

**Právní a ochrana osobních údajů:**

-   Pro informace o smlouvě Microsoft Azure: [Smlouva Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Informace o ochraně osobních údajů pro Microsoft Azure: [Prohlášení o ochraně osobních údajů Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

**Zabezpečení, dodržování předpisů a auditování:**

Naleznete v části [Zabezpečení, dodržování předpisů a právních požadavků](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMScompliance) v oddílu [Co je Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tématu. Navíc platí:

-   Pro externí certifikace pro Azure RMS: [Centrum zabezpečení pro Microsoft Azure](http://azure.microsoft.com/support/trust-center/)

-   FIPS 140 informace: [FIPS 140 ověření](https://technet.microsoft.com/library/security/cc750357.aspx)

**Smlouvy o úrovni služeb:**

-   Smlouvy o úrovni služeb pro Azure RMS pomocí vybranou zemi: [Smlouvy o úrovni služeb](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

-   Smlouvy o úrovni služeb pro Azure Active Directory: [Smlouvy o úrovni služeb](http://azure.microsoft.com/support/legal/sla/)

**Dokumentace:**

-   Azure Active Directory dokumentace lokality: [Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Knihovna Azure Active Directory: [Azure Active Directory](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Office 365 knihovna: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## Co mohu udělat, pokud zde není můj dotaz?
Použijte odkazy a prostředky, které jsou uvedeny v [Informace a podpora nástroje Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

Kromě toho jsou navrženy pro koncové uživatele nejčastější dotazy:

-   [Nejčastější dotazy týkající se aplikace pro systém Windows pro sdílení obsahu Rights Management](https://technet.microsoft.com/dn467883)

-   [Nejčastější dotazy týkající se pro platformy Mac a mobilní aplikace pro sdílení obsahu Rights Management](https://technet.microsoft.com/dn451248)

-   [Nejčastější dotazy týkající se sledování dokumentů](http://go.microsoft.com/fwlink/?LinkId=523977)

Tato stránka nejčastější dotazy týkající se bude aktualizován pravidelně, nové doplňky v uvedena v měsíční oznámení aktualizace dokumentace [týmu Microsoft Rights Management (RMS)](http://blogs.technet.com/b/rms/) blogu.

> [!TIP]
> Můžete použít [dokumenty značka](http://blogs.technet.com/b/rms/archive/tags/docs/) na blogu, k více snadno najít Tato dokumentace oznámení.

## Viz také
[Začínáme s Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

