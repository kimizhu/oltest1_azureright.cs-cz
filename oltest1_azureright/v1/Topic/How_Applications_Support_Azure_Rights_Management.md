---
description: na
keywords: na
title: How Applications Support Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
---
# Jak aplikace podporuj&#237; Azure Rights Management
Pomocí následujících informací, který vám pomůže pochopit, jak vašich aplikací s koncovým uživatelem (například Office aplikací, Word, Excel, PowerPoint a aplikace Outlook) a služeb (například Exchange a služby SharePoint) můžete v aplikaci [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] k ochraně dat vaší organizace:

-   [Aplikace pro systém Windows a mobilní platformy pro sdílení obsahu RMS](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharingAppIntro)

-   [Aplikace systému Office: Word, Excel, PowerPoint, Outlook](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_OfficeAppsIntro)

    -   [Exchange Online a Exchange Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_ExchangeIntro)

    -   [SharePoint Online a SharePoint Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharePointIntro)

-   [Souborové servery, které se systémem Windows Server a používat soubor klasifikace infrastruktury (FCI)](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_FCIIntro)

-   [Jiné aplikace, které podporují rozhraní API služby RMS](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_APIAppsIntro)

> [!NOTE]
> Chcete-li ověřit aplikace a verze, [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] podporuje (Azure RMS) naleznete v tématu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

V některých případech je ochrana údajů automaticky použity, podle zásady, které je nakonfigurovat. Toto je například v případě knihovny služby SharePoint, klasifikovaný soubory a pravidla výměny přenosu. V ostatních případech uživatelé musí použít ochrana údajů sama sebe ze svých aplikací tak, že vyberete šablonu nebo výběrem konkrétních možností. Například to je případ, kdy uživatelé sdílet soubor e-mailem nebo chránit souboru na místě omezení přístupu nebo využití vybraným uživatelům nebo uživatelům mimo organizaci.

Šablony vám usnadní pro uživatele (a správcům, kteří nakonfigurovat zásady) chcete použít správnou úroveň ochrany a omezit tak přístup uživatelům ve vaší organizaci. I když [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] pochází s dvěma výchozích šablon, bude pravděpodobně chcete vytvořit vlastní šablony ke snížení v době, kdy budou muset provést vlastní nastavení. Další informace naleznete v tématu [Konfigurace vlastních šablon pro Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

Pro případy, kdy uživatelé musí použít informace o ochraně sami, ujistěte se, jak poskytnout s pokyny a pokyny a je-li to provést. Pokynů, které by měl být specifické pro aplikace a verze, které používají a jak používají a pokyny pro kdy a jak použít informace ochrana by měla být vhodné pro vaši společnost. Další informace naleznete v tématu [Pomáhá uživatelům k ochraně souborů pomocí Azure Rights Management](../Topic/Helping_Users_to_Protect_Files_by_Using_Azure_Rights_Management.md).

Informace o tom, jak konfigurovat tyto aplikace pro službu RMS Azure naleznete v tématu [Konfigurace aplikací pro Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

> [!TIP]
> Příklady a snímky obrazovky aplikací pomocí Azure RMS naleznete v tématu [Azure RMS v akci: Co správci a uživatelé v tématu](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) oddíl z [Co je Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tématu.

## <a name="BKMK_SharingAppIntro"></a>Aplikace pro systém Windows a mobilní platformy pro sdílení obsahu RMS
Aplikace sdílení RMS je zdarma ke stažení aplikace, která je vyžadována pro podporu systému Office 2010, ale také vhodné pro počítače se systémem Windows, Mac počítačů a mobilních zařízení. Jedna z jeho výhod je, že jej lze použít obecný ochrany pro aplikace a soubory, které nepodporují nativně [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], což znamená, že všechny soubory může být chráněn. Další informace o různých úrovní, naleznete v části [úroveň ochrany – nativní a obecný](http://technet.microsoft.com/library/dn339003.aspx) oddíl z [Rights Management sdílení aplikace Správce průvodce](http://technet.microsoft.com/library/dn339003.aspx).

Když uživatelé chránit jejich soubory s použitím RMS sdílení aplikací, mohou také sledování dokumentů, které jsou chráněny a v případě potřeby odvolat přístup k nim. Je to s využitím [Sledování webu dokumentů](http://go.microsoft.com/fwlink/?LinkId=529562).

Pro počítače se systémem Windows unobtrusively aplikace pro sdílení obsahu RMS integrována se službou a zvyšuje aplikací, které již uživatelé:

-   Doplněk Office pro Word, Excel, PowerPoint a aplikace Outlook je nainstalován. To poskytuje uživatelům **sdílet chráněné** tlačítko na pásu karet, který vyvolá dialogové snadným ovládáním nastavení, které jsou nejčastěji používají k ochraně souborů, chcete-li být odeslány e-mailem. Klepnutím na toto tlačítko také poskytuje rychlý způsob, jak získat přístup k dokumentu sledování webu.

-   Nový klikněte pravým tlačítkem na možnost pro soubor Explorer. To poskytuje uživatelům **chránit místně** možnost, která se vyvolá dialogové snadným ovládáním nastavení, které jsou nejčastěji používaný k ochraně soubory uložené na disku.

-   Prohlížeč k otevření souborů, které bylo chráněno [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Tento prohlížeč je automaticky volána, když neexistuje žádná jiná aplikace nainstalována, může otevřít chráněný soubor.

-   Konfigurace back-end pro systém Office 2010, který umožňuje aplikaci Word, Excel, PowerPoint a aplikace Outlook z této sady bezproblémovou práci s [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Ačkoli může být aplikace pro systém Windows pro sdílení obsahu RMS stažen a nainstalován do jednoho počítače s použitím [stránky Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970), ale také podporuje nasazení v podnikovém prostředí pro tichou instalaci a vlastní konfigurace. Další informace naleznete na následujících odkazech:

-   [Průvodce Rights Management sdílení aplikace Správce](http://technet.microsoft.com/library/dn339003.aspx)

-   [Průvodce Rights Management sdílení aplikace uživatele](http://technet.microsoft.com/library/dn339006.aspx)

Aplikace pro mobilní zařízení pro sdílení obsahu RMS podporuje nejčastěji používané mobilní zařízení, například iPad a zařízení iPhone, Android, Windows Phone a Windows pr. Uživatelé mohou stahovat této aplikace z obchodu relevantní a existuje propojení z [Microsoft Rights Management stránky](http://go.microsoft.com/fwlink/?LinkId=303970).

## <a name="BKMK_OfficeAppsIntro"></a>Aplikace systému Office: Word, Excel, PowerPoint, Outlook
Tyto aplikace nativní podporu Rights Management s použitím Správa práv k informacím (IRM) a umožnit uživatelům použijí ochranu uložený dokument nebo e-mailovou zprávu k odeslání. Uživatelé mohou použít šablony nebo zvolte možnost velmi vlastního nastavení pro omezení přístupu, práva a používání. Můžete například uživatelé soubor můžete nakonfigurovat tak, aby jej mohou přistupovat pouze uživatelé ve vaší organizaci nebo ovládací prvek zda souboru lze upravit, nebo omezit na jen pro čtení nebo zabránit vytištěny. Pro soubory citlivé na čas lze nakonfigurovat čas vypršení platnosti (přímo uživateli nebo použitím šablony) pro Pokud soubor již nebude zpřístupněn. Pro aplikaci Outlook, uživatelé mohou také **dál** možnost vám mohou pomoci zabránit úniku data.

### <a name="BKMK_ExchangeIntro"></a>Exchange Online a Exchange Server
Při použití systému Exchange Online nebo serveru Exchange Server, můžete použít informace rights management (IRM) integrace, který obsahuje další informace o řešení ochrany:

-   **Exchange ActiveSync IRM** aby mohli chránit a využívat mobilní zařízení chráněné e-mailové zprávy.

-   Podpora služby RMS **aplikace Outlook Web**, podobně implementována tak, aby klient aplikace Outlook, tak, aby uživatelé lze chránit e-mailové zprávy, šablony nebo zadáním jednotlivé možnosti a uživatelé mohou číst a používat chráněné e-mailové zprávy, které jsou odeslány na ně.

-   **Pravidla ochrany** pro klienty Outlook, aby správce konfiguruje automaticky aplikujete RMS šablony e-mailové zprávy pro zadaný příjemce. Například když interní e-maily jsou odeslány do oddělení právní, jejich lze je číst pouze členy právní oddělení a nemůže být předán. Uživatelé vidí ochrany před odesláním použité e-mailové zprávě a ve výchozím nastavení, že jej odebrat Pokud se rozhodnete, že není nutné. E-mailů jsou šifrovány před odesláním. Další informace naleznete v tématu [pravidla pro ochranu aplikace Outlook](http://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) a [Vytvoření pravidla pro ochranu aplikace Outlook](http://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) v knihovně Exchange.

-   **Přenosu pravidla** může správce konfigurovat, mají být automaticky použity RMS šablony e-mailové zprávy na základě vlastnosti, například odesílatele, příjemce, předmět zprávy a obsahu. Tyto jsou v principu podobná pravidla ochrany, ale není uživatelům odebrat ochranu, lze použít k aplikaci Outlook Web Access a e-mailech odesílají mobilní zařízení a nelze zašifrovat e-mailové zprávy před odesláním z klienta. Další informace naleznete v tématu [vytvořit pravidlo přenosu ochrany](http://technet.microsoft.com/library/dd302432.aspx) v knihovně Exchange.

-   **Zásady prevence (DLP) ztrátě dat** obsahují sady podmínky pro filtrování e-mailové zprávy a provést akce, které vám mohou pomoci zabránit ztrátě dat pro obsah důvěrné nebo malá a velká písmena (například osobní údaje nebo informace o platební kartě). Zásady tipy lze použít, když je zjištěno citlivá data výstrah uživatelům, kteří potřebují může použít informace ochrany, na základě informací v e-mailové zprávě. Další informace naleznete v tématu [Zabránění ztrátě dat](http://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) v knihovně Exchange.

-   **Šifrování zpráv office 365** používá přenosu pravidla pro odeslání šifrované e-mailů osobám mimo vaši společnost a e-mailu je pro čtení, v prohlížeči s rozhraním podobný webovou aplikaci Outlook. Můžete přizpůsobit zřeknutí se text a text záhlaví šifrované e-mailů vaší společnosti a to i přidat logo společnosti. Další informace naleznete v tématu [šifrování zpráv Office 365](http://office.microsoft.com/o365-message-encryption-FX104179182.aspx) z webu Office.

Pokud používáte Exchange Server, můžete použít funkce ochrany informace s [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] nasazením služby RMS konektor, který funguje jako přenosový mezi na místní servery a cloudové služby RMS. Další informace naleznete v tématu [Nasazení konektoru Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_SharePointIntro"></a>SharePoint Online a SharePoint Server
Při použití služby SharePoint Online nebo serveru SharePoint Server, můžete informace o integraci práva IRM (Správa), který umožňuje správcům chránit seznamy nebo knihovny tak, že pokud se uživatel kontroly out dokumentu, soubor je chráněn tak, aby pouze autorizovaní uživatelé mohou zobrazit a používat soubor podle zásady ochrany informací, které zadáte. Soubor může být například jen pro čtení, zakázání kopírování textu, nelze uložit místní kopii a zabránit tisku souboru.

Pro seznamy a knihovny ochrana údajů platí vždy správce, nikdy koncovému uživateli. A je použit na úrovni seznamu nebo knihovny pro všechny dokumenty v tomto kontejneru, a nikoli na jednotlivé soubory.  Pokud používáte služby SharePoint Online, uživatelé také mohou zvolit IRM s jejich Onedrivem pro obchodní knihovnu.

Služba IRM musí být nejprve povolena pro službu SharePoint. Poté zadejte informace o Rights Management pro knihovnu. Zadejte informace o Rights Management pro jejich Onedrivem pro knihovnu obchodní také v případě služby SharePoint Online a Onedrivem pro společnost. Server SharePoint nepoužívá šablony zásad práv, i když jsou nastavení konfigurace služby SharePoint, které můžete vybrat a které nejpřesněji odpovídají nastavení, které můžete určit v šablonách.

Pokud používáte SharePoint Server, můžete použít funkce ochrany informace s [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] nasazením služby RMS konektor, který funguje jako přenosový mezi na místní servery a cloudové služby RMS. Další informace naleznete v tématu [Nasazení konektoru Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!NOTE]
> V současné době má některá omezení, pokud použijete IRM se službou SharePoint:
> 
> -   Nelze použít výchozí nebo vlastní šablony, které můžete spravovat na portálu Azure.
> -   Soubory, které mají. Přípona názvu souboru PPDF pro chráněné soubory PDF nejsou podporovány. Soubory, které mají. Příponu názvu souboru PDF a že bylo nativně chráněno RMS jsou podporovány, pokud použijete čtení souborů PDF, který nativně podporuje RMS.
> -   Vzhledem k tomu, že Office na mobilních zařízeních dosud nepodporuje RMS, tato zařízení musí používat prohlížeč, chcete-li zobrazit soubory, které je chráněno s RMS a soubory jsou jen pro čtení.

Azure RMS použije omezení použití a šifrování dat pro dokumenty při jejich stažení z webu služby SharePoint a nikoli při prvním dokumentu vytvořen ve službě SharePoint nebo odeslat do knihovny. Informace o tom, jak jsou chráněny dokumenty, stažení, naleznete v části [šifrování dat v Onedrivem pro podnikové a služby SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) z dokumentace rozhraní služby SharePoint.

Další informace o použití Azure RMS pomocí služby SharePoint naleznete v následujících příspěvek z blogu Office: [Co je nového v Správa informačních práv v SharePoint a služby SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="BKMK_FCIIntro"></a>Souborové servery, které se systémem Windows Server a používat soubor klasifikace infrastruktury (FCI)
Při konfiguraci systému Windows Server používat infrastrukturu klasifikace souboru, můžete tuto funkci správce prostředků souborového serveru scan lokálních souborů a zjišťuje, zda neobsahují citlivá data. Pro soubory, které splňují tato kritéria jsou označeny klasifikace vlastnosti, které definuje správce. Infrastruktura klasifikace souboru poté můžete začít automatické akce podle klasifikace. Jednu z následujících akcí zahrnout použitím ochrana informací pomocí [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] a nasazení konektoru Rights Management (také označované jako konektor služby RMS). Soubory sady Office jsou pak automaticky chráněné službou Azure RMS.

Pokud chcete chránit všechny typy souborů, by není použijete konektoru služby RMS, ale místo toho spustit skript prostředí Windows PowerShell pomocí rutin z [Nástroj pro ochranu RMS](https://www.microsoft.com/en-us/download/details.aspx?id=47256).

Klasifikace zásady jsou plně konfigurovatelná a velmi dobře rozšiřitelná, takže můžete zabránit potenciální únik data z neověřených a autorizované uživatele. I může pomoci snížit riziko úniku dat správci sítě vzhledem k tomu, že je možné nakonfigurovat zásady, které nevyžadují těmto správcům chcete-li mít přístup k souborům.

Pokyny k nasazení a konfigurace služby RMS připojovací souborů sady Office naleznete v tématu [Nasazení konektoru Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

Chcete-li použít skript prostředí Windows PowerShell pro všechny typy souborů, naleznete v tématu [Ochrana RMS pomocí systému Windows Server soubor klasifikace infrastruktury &#40;FCI&#41;](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

## <a name="BKMK_APIAppsIntro"></a>Jiné aplikace, které podporují rozhraní API služby RMS
Pomocí sady SDK služby RMS vaší interní vývojáři může zapisovat-podnikových aplikací tak, aby podporovaly [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Jak je ochrana údajů integrována s těmito aplikacemi závisí na tom, jak jsou zapsány. Můžete například integrace může být automaticky použita s minimální uživatelskou interakcí požadované nebo více přizpůsobené prostředí, mohou uživatelé vyzváni ke konfiguraci nastavení, které mají být použity informace o ochraně souborů. Další informace o sadě SDK naleznete [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

Podobně mnoho dodavatelé softwaru poskytovat aplikacím a informace o řešení ochrany, také označován jako enterprise rights management (ERM) produkty. Oblíbené příklad je čtení souborů PDF, který podporuje [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] pro konkrétní platformy. Můžete použít v tabulce v [Možnosti zařízení klienta](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) část [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu, které chcete určit aplikace podporující RMS (RMS enlightened aplikace) a potom pomocí vyhledávání na webu zakoupit nebo stáhnout aplikaci.

> [!TIP]
> Pro nově vydané aplikace, zkontrolujte kanálů RMS komunity, uvedené v [Informace a podpora nástroje Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Viz také
[Začínáme s Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

