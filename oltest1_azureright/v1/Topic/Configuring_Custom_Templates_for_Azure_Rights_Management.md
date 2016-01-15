---
description: na
keywords: na
title: Configuring Custom Templates for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
---
# Konfigurace vlastn&#237;ch šablon pro Azure Rights Management
Po aktivaci Azure Rights Management (Azure RMS), uživatelé mohou automaticky použít dvě výchozí šablony, které usnadňují jejich k uplatnění zásad pro citlivé soubory, které omezují přístup oprávněným uživatelům ve vaší organizaci. Tyto dvě šablony mají následující zásady omezení práva:

-   Zobrazení jen pro čtení pro chráněný obsah

    -   Zobrazovaný název: **&lt; název organizace &gt; - pouze důvěrné zobrazení**

    -   Konkrétní oprávnění: Zobrazení obsahu

-   Číst nebo upravovat oprávnění pro chráněný obsah

    -   Zobrazovaný název: **&lt; název organizace &gt; - důvěrné**

    -   Specifická oprávnění: Zobrazit obsah, soubor uložit, upravit obsah, zobrazit přiřazené práva, povolit makra, vpřed, odpověď, odpovědět všem

Kromě toho [aplikace sdílení RMS](http://technet.microsoft.com/library/dn339006.aspx) umožňuje uživatelům definovat svá vlastní sadu oprávnění. A klient aplikace Outlook a Outlook Web Access, mohou uživatelé vybrat **Nepředávat** možnost pro e-mailové zprávy.

Pro mnoho organizací může být výchozí šablony dostatečná. Ale pokud chcete vytvořit vlastní práva šablony zásad, můžete tak učinit. Důvody pro vytvoření vlastní šablony zahrnují následující:

-   Chcete šablonu, kterou chcete udělit práva na určitou podmnožinu uživatelům v organizaci, nikoli všichni uživatelé.

-   Chcete pouze podmnožinu uživatelé byli schopni zobrazit a vybrat šablonu (založená na odděleních šablona) z aplikací, nikoli všichni uživatelé v organizaci viz a můžete vybrat šablonu.

-   Chcete definovat vlastní vpravo pro šablonu, například zobrazení a úpravy, ale není kopírování a tisk.

-   Chcete-li nakonfigurovat další možnosti v šabloně, které zahrnují datum vypršení platnosti a zda je obsah přístupný bez připojení k Internetu.

Uživatelé nebudou moci vybrat vlastní šablonu, která obsahuje nastavení, například ty musí nejprve vytvořit vlastní šablonu, nakonfigurujte ji a potom ho publikovat.

Použijte následující části vám pomohou nakonfigurovat a používat vlastní šablony:

-   [Jak vytvořit, konfigurovat a publikovat vlastní šablonu](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToConfigureCustomTemplates)

-   [Postup kopírování šablony](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates)

-   [Postup odebrání šablony (archiv)](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToArchiveTemplates)

-   [Aktualizace šablony pro uživatele](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates)

-   [Odkaz na prostředí Windows PowerShell](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_PowerShellTemplates)

## <a name="BKMK_HowToConfigureCustomTemplates"></a>Jak vytvořit, konfigurovat a publikovat vlastní šablonu
Vytvářet a spravovat vlastní šablony v portálu správy Azure. Můžete to provést přímo z portálu pro správu Azure, nebo můžete přihlásit k Centru správy Office 365 a zvolit **Rozšířené funkce** Rights Management, který pak vás přesměruje na portálu pro správu Azure.

Pomocí následujících postupů vytvářet, konfigurovat a publikovat vlastní šablony Rights Management.

#### Chcete-li vytvořit vlastní šablonu

1.  V závislosti na tom, zda přihlášení k Centru správy Office 365 nebo portálu Azure proveďte jednu z následujících akcí:

    -   Z [centra pro správu služeb Office 365](https://portal.office.com/):

        1.  V levém podokně klikněte na tlačítko **Nastavení služby**.

        2.  Z **Nastavení služby** klikněte na tlačítko **služby rights management**.

        3.  V **chránit vaše informace** klepněte na **Spravovat**.

        4.  V **služby rights management** klepněte na **Rozšířené funkce**.

            > [!NOTE]
            > Pokud jste neaktivovali Rights Management, nejprve klikněte na **Aktivovat** a potvrzení této akce. Další informace naleznete v tématu [Aktivace Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).
            > 
            > Pokud jste ještě klikli **Pokročilé funkce** před, po Rights Management je aktivována, postupujte na obrazovce pokyny pro získání bezplatné předplatné Azure, který je požadovaný pro přístup k portálu Azure.

            Klepnutím na **Rozšířené funkce** načte portálu Azure, kde můžete spravovat **RIGHTS MANAGEMENT** pro Azure Active Directory vaší organizace.

    -   Z [portálu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  V levém podokně klikněte na tlačítko **služby ACTIVE DIRECTORY**.

        2.  Z **služby active directory** klikněte na tlačítko **RIGHTS MANAGEMENT**.

        3.  Vyberte adresář pro správu pro Rights Management.

        4.  Pokud jste ještě neaktivovali Rights Management, klikněte na tlačítko **Aktivovat** a potvrzení této akce.

            > [!NOTE]
            > Další informace naleznete v tématu [Aktivace Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

2.  Vytvořte novou šablonu:

    -   Na portálu Azure z **Začínáme s Rights Management** rychle začít stránku, klikněte na tlačítko **vytvořit nové šablony zásad práv**.

        Pokud se nezobrazí okamžitě tuto stránku po provedení kroků pro Office 365, použijte navigační pokynů výše, pro portál Azure.

3.  Na **Přidat nové šablony zásad práv** vyberte jazyk, ve kterém bude zadejte název šablony a popis, který se zobrazí uživatelům (můžete přidat další jazyky později). Poté zadejte jedinečný název a popis a klikněte na tlačítko dokončení.

Z **Začínáme s Rights Management** rychle úvodní stránka, klepněte na tlačítko **správu vašich šablon zásad práv**. Zobrazí se nově vytvořená šablona přidán do seznamu šablon se stavem **archivované**. V této fázi je šablona vytvořen, ale není nakonfigurována a není viditelné pro uživatele.

#### Ke konfiguraci a publikovat vlastní šablonu

1.  Vyberte šablonu nově vytvořený z **šablony** stránku v portálu správy Azure.

2.  Z **byla přidána do šablony** rychle začít stránku, klikněte na tlačítko **začít** z kroku 1, **nakonfigurovat oprávnění pro uživatele a skupiny,** klikněte na tlačítko **Začít nyní** nebo **Přidat**, a pak vyberte uživatele a skupiny, kteří budou mít práva k používání obsah, který je chráněn novou šablonu.

    > [!NOTE]
    > Uživatele nebo skupiny, které jste vybrali, musí mít e-mailovou adresu. V provozním prostředí téměř vždy to bude v případě, ale v jednoduché testovacím prostředí, může být nutné přidat e-mailové adresy na uživatelské účty nebo skupiny.

    Jako nejlepší postup použijte skupinám než uživatelům, které zjednodušuje správu šablon. Pokud máte služby Active Directory místně a synchronizují do Azure AD, můžete poštovní skupiny, které jsou skupiny zabezpečení nebo distribuční skupiny. Nicméně pokud chcete udělit práva pro všechny uživatele v organizaci, je efektivnější zkopírovat jeden výchozí šablony, spíše než určit více skupin. Další informace naleznete v tématu [Postup kopírování šablony](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates) v tomto tématu.

    > [!TIP]
    > Později můžete přidat uživatele z mimo vaši organizaci do šablony pomocí [modul Windows PowerShell pro Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx) a pomocí jedné z následujících metod:
    > 
    > -   **Exportu, úpravy a importu aktualizované šablony**:  Toto je nejjednodušší způsob přidání externích uživatelů do stávající šablony, která obsahuje jiné skupiny. Použití [Export AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) rutiny exportovat šablonu, kterou chcete. Soubor CSV, který lze upravovat přidat externí e-mailové adresy tito uživatelé a jejich práva na stávajících skupin a oprávnění. Potom pomocí [Import AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) rutiny Import této změny zpět do Azure RMS.
    > -   **Použití definice objektu práva aktualizace šablony**:    Zadejte externí e-mailové adresy a jejich práva v objektu definice práv, který pak použijete k aktualizaci šablony. Zadejte definici objektu práva pomocí [Nový AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) rutiny vytvořit proměnnou a poté poskytnout tuto proměnnou na parametr - RightsDefinition s [Set AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) rutiny Úprava stávající šablony. Nicméně pokud přidáváte tito uživatelé do stávající šablony, bude také potřebujete definovat práva definice objektů pro existující skupiny v šablonách a nikoli pouze nové, externí uživatelé.

3.  Klepněte na tlačítko Další a pak přiřadit jeden z uvedených práva k vybrané uživatele a skupiny.

    Další informace o jednotlivých vpravo (a pro vlastní práva), použijte zobrazené popis. Další podrobné informace jsou také k dispozici v [Konfigurace užívací práva pro Azure Rights Management](../Topic/Configuring_Usage_Rights_for_Azure_Rights_Management.md). Aplikace, které podporují RMS však může lišit, jak implementují tato práva. V dokumentaci k jejich a provést vlastní testování s aplikacemi, které uživatelé použít ke kontrole chování před nasazením šablony pro uživatele. Chcete-li tuto šablonu viditelné pouze správce pro tento testování, proveďte tuto šablonu založená na odděleních šablony (krok 6).

4.  Pokud jste vybrali **Vlastní**, klepněte na tlačítko Další a poté vyberte těchto vlastní oprávnění.

    I když můžete použít libovolnou kombinaci jednotlivých práv k dispozici v některých aplikacích, může některá práva jsou závislé na jiné individuální práva. Je to tento případ, jsou pro vás automaticky vybrána závislá práva.

    > [!TIP]
    > Zvažte přidání **Kopírovat a extrahování obsahu** doprava a to udělit vybrané skupině administrators nebo pracovníci v jiných rolí, které mají odpovědnosti pro informace o obnovení. Udělení toto právo umožňuje jejich odebrání ochrany v případě potřeby ze souborů a e-mailů, které budou chráněny pomocí této šablony. Tato schopnost odebrání ochrany na úrovni šablona poskytuje jemněji odstupňovanou kontrolu než používá funkci superuživatele.

5.  Klikněte na tlačítko dokončení.

6.  Pokud chcete, aby šablony, která má být viditelná pouze podmnožinu uživatelé vidí seznam šablon v aplikacích: Klikněte na tlačítko **oboru** to nakonfigurovat jako šablonu založená na odděleních, a klikněte na **Začít nyní**. V opačném případě přejděte ke kroku 9.

    Další informace o založená na odděleních šablony: Ve výchozím nastavení všechny uživatele v adresáři Azure najdete v části publikované šablony a mohou si vybrat, je z aplikací, když chtějí ochranu obsahu. Pokud chcete konkrétním uživatelům pouze některé z publikovaných šablony, musíte určit rozsah šablony pro tyto uživatele. Pak pouze tito uživatelé budou moci vybrat tyto šablony. Ostatním uživatelům, kteří nezadáte neuvidí šablony a proto nelze je vybrat. Tento postup můžete provést výběr správnou šablonu snazší pro uživatele, zejména v případě, že vytvoříte šablony, které jsou určeny k použít pro konkrétní skupiny nebo oddělení. Potom se uživatelům zobrazí pouze šablony, které jsou určeny pro ně.

    Jste například vytvořili šablonu pro oddělení lidských zdrojů, které platí pro členy finančním oddělení oprávnění jen pro čtení. Tak, aby pouze členové oddělení lidských zdrojů, můžete tuto šablonu použít při používání aplikace pro sdílení obsahu Rights Management, oboru šablony do skupiny povoleno e-mailu s názvem lidských zdrojů. Pouze členové této skupiny viz a můžete pak, použijte tuto šablonu.

7.  Na **šablony viditelnost** vyberte uživatele a skupiny, kteří budou moci zobrazit a vyberte šablonu z aplikace podporující RMS. Jako dříve, jako nejlepší postup použití skupin spíše než uživatele nebo skupiny nebo uživatele, které jste vybrali musí mít e-mailovou adresu.

8.  Klepněte na tlačítko Další a rozhodněte se, zda je nutné nakonfigurovat kompatibilitu aplikace založená na odděleních šablony. Je-li provést, klikněte na tlačítko **Kompatibilita aplikací**, zaškrtněte políčko a klikněte na tlačítko **Dokončeno**.

    Proč možná budete muset nakonfigurovat kompatibilita aplikací? Ne všechny aplikace může podporovat založená na odděleních šablony. Provedete to tak, aplikace musí nejprve provést ověření pomocí služby RMS před stažením šablony. Pokud proces ověřování nedojde, bude ve výchozím nastavení, budou staženy žádná z oddělení šablon. Toto chování můžete přepsat zadáním, že by měla stáhnout založená na odděleních šablony, konfigurace pro kompatibilitu aplikací a výběrem **Zobrazit tuto šablonu pro všechny uživatele, když aplikace nepodporují identita uživatele** zaškrtávací políčko.

    Například pokud nenakonfigurujete kompatibilita aplikací založená na odděleních šablony v našem příkladu lidské zdroje, pouze v oddělení lidských zdrojů uvidí založená na odděleních šablony používají aplikace sdílení RMS, ale žádní uživatelé vidět založená na odděleních šablonu při používání aplikace Outlook Web Access (OWA) ze serveru Exchange Server 2013 vzhledem k tomu, že aplikace OWA serveru Exchange a Exchange ActiveSync aktuálně nepodporují založená na odděleních šablony. Je-li toto výchozí chování můžete přepsat nakonfigurováním kompatibilitu aplikací, pouze v oddělení lidských zdrojů uvidí založená na odděleních šablony používají aplikaci sdílení RMS, ale všichni uživatelé vidět založená na odděleních šablonu při používání aplikace Outlook Web Access (OWA). Pokud uživatelé používají aplikaci OWA nebo Exchange ActiveSync ze služby Exchange Online, všichni uživatelé uvidí založená na odděleních šablony nebo žádní uživatelé uvidí oddělení šablony, na základě stavu šablony (archivace nebo publikovaných) v systému Exchange Online.

    > [!NOTE]
    > Pokud máte aplikace, které zatím nepodporují nativně založená na odděleních šablony, můžete použít [vlastní skript stažení šablony RMS](http://go.microsoft.com/fwlink/?LinkId=524506) nebo jiné nástroje pro nasazení tyto šablony k místní složce klienta služby RMS. Potom tyto aplikace správně zobrazí založená na odděleních šablony pro uživatele a skupiny, které jste vybrali pro obor šablony:
    > 
    > -   Pro systém Office 2010 složky klienta je **%localappdata%\Microsoft\DRM\Templates**.
    > -   Z klientského počítače, který byl stažen všechny šablony můžete zkopírujte a vložte soubory šablon do jiných počítačů.
    > 
    > Office 2016 nativně podporuje založená na odděleních šablony, a proto Office 2013 s nejnovější aktualizací sady Office ([KB 3054853](https://support.microsoft.com/kb/3054853)).

9. Klikněte na tlačítko **KONFIGUROVAT** a přidejte další jazyky, které uživatelé používat společně s název a popis této šablony v daném jazyce. Pokud máte více jazyků uživatelů, je třeba přidat jednotlivé jazyky, které používají a zadejte název a popis v daném jazyce. Uživatelům se potom zobrazí název a popis šablony ve stejném jazyce jako jejich klientský operační systém, který zajistí, že vědí zásada použitá k dokumentu nebo e-mailové zprávy. Pokud je nalezena shoda s jejich klientský operační systém, název a popis, který se uživatelům zobrazí přejde do jazyka a popis, který jste definovali při prvním vytvoření šablony.

    Zkontrolujte, zda chcete provést jakékoli změny následující nastavení:

    |Nastavení|Další informace|
    |-------------|-------------------|
    |**vypršení platnosti obsahu**|Definujete datum nebo počet dní pro tuto šablonu neměli otevírat soubory, které jsou chráněny pomocí šablony. Můžete určit datum nebo zadejte počet dnů od doby, použitý ochranu na soubor.<br /><br />Když zadáte datum, je účinné půlnoci v aktuální časové pásmo.|
    |**přístup v režimu offline**|Toto nastavení použijte k vyrovnávání nějaké požadavky na zabezpečení, budete mít proti požadavek, který uživatelé musí být schopen otevřít chráněné soubory při nemají připojení k Internetu.<br /><br />Pokud určíte, že obsah není k dispozici bez připojení k Internetu, nebo tento obsah je k dispozici pouze pro zadaný počet dnů, kdy je dosaženo této prahové hodnoty, uživatelé musí být znovu ověřený a je protokolováno jejich přístup. Pokud k tomu dojde, pokud nejsou jejich přihlašovací údaje uložené v mezipaměti, uživatelé vyzváni k přihlášení, než mohou otevřít soubor.<br /><br />Kromě toho opětovné ověření je opět hodnotit zásady a členství ve skupině uživatelů. To znamená, že uživatelé různý přístup výsledky pro stejný soubor pokud existují změny ve členství zásad nebo skupiny z při posledního použití souboru.|

10. Pokud jste si jisti, že je šablona správně konfigurována pro uživatele, klikněte na tlačítko **Publikovat** zviditelnit šablony pro uživatele a potom klikněte na tlačítko **Uložit**.

11. Klepněte na tlačítko Zpět se vraťte do portálu pro správu **šablony** stránku, kde šablony má nyní aktualizovaný stav **Publikováno**.

Žádné změny do šablony, vyberte ji a pak znovu použijte kroky rychlý start. Nebo vyberte některou z následujících možností:

-   Chcete-li přidat další uživatelé a skupiny a definovat oprávnění pro uživatele a skupiny: Klikněte na tlačítko **práva**, klikněte na tlačítko **Přidat**.

-   Odebrání uživatele nebo skupiny, které jste dříve vybrali: Klikněte na tlačítko **práva**, vyberte uživatele nebo skupinu ze seznamu a poté klikněte na tlačítko **Odstranit**.

-   Chcete-li změnit, které uživatelé mohou vidět šablony výběr z aplikace: Klikněte na tlačítko **oboru**, klikněte na tlačítko **Přidat** nebo **Odstranit**, nebo **Kompatibilita aplikací**.

-   Chcete-li šablonu již nebudou viditelné pro všechny uživatele: Klikněte na tlačítko **KONFIGUROVAT**, klikněte na tlačítko **ARCHIVU**, a potom klikněte na tlačítko **Uložit**.

-   Chcete-li provést další změny konfigurace: Klikněte na tlačítko **KONFIGUROVAT**, proveďte požadované změny a potom klikněte na tlačítko **Uložit**.

> [!WARNING]
> Pokud provedete změny do šablony, který byl dříve uložen, klienti neuvidí tyto změny do šablony, dokud šablony jsou aktualizovány na svých počítačích. Další informace naleznete v tématu [Aktualizace šablony pro uživatele](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates) v tomto tématu.

## <a name="BKMK_HowToCopyTemplates"></a>Postup kopírování šablony
Pokud chcete vytvořit novou šablonu, kterou má velmi podobné nastavení pro existující šablonu, vyberte na původní šablony **šablony** klikněte na tlačítko **kopie**, zadejte jedinečný název a provést změny, které potřebujete.

> [!IMPORTANT]
> Při kopírování šablony, **Publikováno** nebo **archivované** stav je také zkopírován. Tak, že při kopírování publikované šablony, jeho okamžité stav bude publikována, pokud jej nezměníte.

Můžete zkopírovat vlastní šablony a výchozích šablonách. Jako nejlepší postup zkopírujte jeden výchozí šablony namísto vytvoření nové vlastní šablony, pokud chcete šablonu, kterou chcete udělit práva pro všechny uživatele ve vaší organizaci. Tato metoda znamená, že nemáte vytvořte nebo vyberte více skupin můžete určit všechny uživatele. V tomto scénáři je však nutné zadat nový název a popis pro kopírované šablonu pro další jazyky.

## <a name="BKMK_HowToArchiveTemplates"></a>Postup odebrání šablony (archiv)
Výchozí šablony nelze odstranit, ale mohou být archivovány tak, aby je uživatelé neuvidí.

Podobně, pokud jste publikovali vlastní šablony a již nechcete, aby uživatelé mohli zobrazit, můžete upravit šablonu a zvolte **ARCHIVU** a **Uložit** z **KONFIGUROVAT** stránky. Nebo můžete vybrat z **šablony** stránku a vyberte **ARCHIVU**.

Protože nelze upravit výchozí šablony pro archivaci těchto šablon, je nutné použít **ARCHIVU** možnost z **šablony** stránky. Nelze archivovat aplikace Outlook **Nepředávat** možnost.

#### Chcete-li odebrat výchozí šablony

-   Z **šablony** vyberte výchozí šablonu a klikněte na tlačítko **ARCHIVU**.

Stav se změní z **Publikováno** k **archivované**. Pokud změníte své rozhodnutí, vyberte šablonu a klikněte na tlačítko **Publikovat**.

## <a name="BKMK_RefreshingTemplates"></a>Aktualizace šablony pro uživatele
Pokud používáte službu Azure RMS, šablony jsou automaticky staženy do klientských počítačů, tak, aby uživatelé mohou vybrat z jejich aplikací. Však může být zapotřebí provést další kroky, pokud provedete změny šablony:

|Aplikace nebo služby|Jak jsou aktualizovány šablony po provedení změn|
|------------------------|----------------------------------------------------|
|Exchange Online|Ruční konfigurace požadované aktualizace šablony.<br /><br />Kroky konfigurace, rozbalte položku v následující části [Exchange Online pouze: Postup konfigurace serveru Exchange, chcete-li stáhnout změnit vlastní šablony](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_ExchangeOnlineTemplatesUpdate).|
|Office 365|Automaticky aktualizovat – žádné další kroky.|
|Office 2016 a Office 2013<br /><br />Aplikace sdílení RMS pro Windows|Automaticky aktualizovat – podle plánu:<br /><br />-   Pro tyto novější verze Office: Výchozí interval aktualizace je každých 7 dní.<br />-   Pro aplikace pro Windows Sdílení RMS: Počínaje verzí 1.0.1784.0, je výchozí interval aktualizace je každý 1 den. Předchozí verze mají výchozí interval každých 7 dní aktualizace.<br /><br />Chcete-li vynutit aktualizaci dříve než tento plán, rozbalte v následující části [Office 2016, Office 2013 a aplikace sdílení RMS pro Windows: Jak můžete vynutit aktualizaci změněné vlastní šablony](#BKMK_Office2013ForceUpdate).|
|Office 2010|Aktualizovat při přihlášení uživatelů.<br /><br />Můžete vynutit aktualizaci, požádejte nebo přinutit uživatele se odhlásit a znovu přihlaste. Nebo, naleznete v následující části [Pouze v systému Office 2010: Jak můžete vynutit aktualizaci změněné vlastní šablony](#BKMK_Office2010ForceUpdate).|
Pro mobilní zařízení, které používají aplikace sdílení RMS, šablony jsou automaticky staženy (a aktualizovat v případě potřeby) bez další nezbytné konfigurace.

### <a name="BKMK_ExchangeOnlineTemplatesUpdate"></a>Exchange Online pouze: Postup konfigurace serveru Exchange, chcete-li stáhnout změnit vlastní šablony
Pokud jste již nakonfigurovali Správa informačních práv (IRM) pro Exchange Online, nebudou pro uživatele stáhnout vlastní šablony, dokud provést následující změny pomocí prostředí Windows PowerShell v systému Exchange Online.

> [!NOTE]
> Další informace o tom, jak pomocí prostředí Windows PowerShell v systému Exchange Online v tématu [pomocí prostředí PowerShell s Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Tento postup je nutné provést při každé změně šablony.

##### Chcete-li aktualizovat šablony pro Exchange Online

1.  Použití příkazu Windows PowerShell v systému Exchange Online, připojte ke službě:

    1.  Zadejte Office 365 uživatelské jméno a heslo:

        ```
        $Cred = Get-Credential
        ```

    2.  Připojte ke službě Exchange Online spuštěním následujících příkazů:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Použití [Import RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) rutiny znovu importujte vaší důvěryhodné domény publikování (důvěryhodné domény publikování) ze služby Azure RMS:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Například, pokud je název vaší důvěryhodné domény publikování **RMS Online - 1** (typický název pro mnoho organizací), zadejte: **Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > Chcete-li ověřit název vaší důvěryhodné domény publikování, můžete použít [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) rutiny.

3.  Chcete-li potvrdit, že šablony úspěšně importovali, počkejte několik minut a poté spusťte [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) rutiny a nastavte typ pro všechny. Příklad:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > Je vhodné ponechat kopii výstupu, takže můžete snadno zkopírovat názvy šablon nebo identifikátory GUID Pokud později archivace šablony.

4.  Pro každou importovanou šablonu, kterou chcete být k dispozici v aplikaci Outlook Web App, je nutné použít [Set RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) rutiny a nastavte typ distribuované:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Protože aplikace Outlook Web Access ukládá do mezipaměti uživatelského rozhraní pro 24 hodin, nemusí se uživatelům zobrazí nové šablony pro až denně.

Kromě toho, pokud archivace šablony (vlastní nebo výchozí) a používání systému Exchange Online s Office 365, budou uživatelé nadále najdete archivované šablony, pokud používají Outlook Web App nebo mobilní zařízení, která používají protokol Exchange ActiveSync.

Tak, aby uživatelé již nebudou tyto šablony zobrazíte připojit ke službě pomocí prostředí Windows PowerShell v systému Exchange Online a pak použít [Set RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) rutiny spuštěním následujícího příkazu:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

### <a name="BKMK_Office2013ForceUpdate"></a>Office 2016, Office 2013 a aplikace sdílení RMS pro Windows: Jak můžete vynutit aktualizaci změněné vlastní šablony
Automatické plán můžete úpravou registru v počítačích se systémem Office 2016, Office 2013 nebo sdílení Rights Management (RMS) aplikace pro Windows změnit tak, aby změněné šablony jsou aktualizovány na počítačích častěji, než jejich výchozí hodnotu. Můžete také vynutit okamžitou aktualizaci odstranění existujících dat v hodnotě registru.

> [!WARNING]
> Nesprávné použití Editoru registru může způsobit vážné problémy, které mohou vyžadovat přeinstalaci operačního systému. Společnost Microsoft nemůže zaručit, že budete schopni vyřešit problémy vzniklé z nesprávného použití Editoru registru. Pomocí Editoru registru na vlastní nebezpečí.

##### Chcete-li změnit automatické plán

1.  Pomocí Editoru registru, vytvoření a nastavení jedné z následujících hodnot registru:

    -   Chcete-li nastavit četnost aktualizace ve dnech (minimálně 1 den):  Vytvořte novou hodnotu registru s názvem **TemplateUpdateFrequency** a definovat celočíselnou hodnotu pro data, která určuje četnost, se ve dnech, chcete-li stáhnout všechny změny do stažené šablony. Vyhledejte cestu registru pro vytvoření této nové hodnoty registru pomocí následující tabulky.

        |Cesta v registru|Typ|Hodnota|
        |--------------------|-------|-----------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequency|

    -   Chcete-li nastavit četnost aktualizace v sekundách (nejméně 1 sekundu):  Vytvořte novou hodnotu registru s názvem **TemplateUpdateFrequencyInSeconds** a definovat celočíselnou hodnotu pro data, která určuje interval v sekundách stáhnout všechny změny do stažené šablony. Vyhledejte cestu registru pro vytvoření této nové hodnoty registru pomocí následující tabulky.

        |Cesta v registru|Typ|Hodnota|
        |--------------------|-------|-----------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequencyInSeconds|

    Ujistěte se, vytvořit a nastavit jednu z těchto hodnot registru, ne obojí. Pokud jsou přítomny, oba **TemplateUpdateFrequency** je ignorován.

2.  Pokud chcete vynutit okamžitou aktualizaci šablon, přejděte pomocí následujícího postupu. V opačném restartujte aplikace Office a instance v Průzkumníku souborů.

##### Chcete-li vynutit okamžitou aktualizaci

1.  Pomocí Editoru registru, odstranit data **LastUpdatedTime** hodnotu. Například může zobrazit data **2015-04-20T15:52**; odstranit 2015-04-20T15:52, aby mohli zobrazit žádná data. Následující tabulku použijte k vyhledejte cestu registru Chcete-li odstranit tento údaj hodnoty registru.

    |Cesta v registru|Typ|Hodnota|
    |--------------------|-------|-----------|
    |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; MicrosoftRMS_FQDN &gt; \Template|REG_SZ|LastUpdatedTime|
    > [!TIP]
    > V cestě registru *&lt; MicrosoftRMS_FQDN &gt;* odkazuje na službě Microsoft RMS plně kvalifikovaný název domény. Pokud chcete ověřit tuto hodnotu:
    > 
    > 1.  Spuštění [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) rutiny pro Azure RMS. Pokud jste ještě nenainstalovali modul prostředí Windows PowerShell pro službu Azure RMS, naleznete v části [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 2.  Z výstupu, určete **LicensingIntranetDistributionPointUrl** hodnotu.
    > 
    >     Příklad: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Od hodnoty, odeberte **https://** a **/_wmcs/licensing** z tohoto řetězce. Zbývající hodnota je plně kvalifikovaný název domény služby Microsoft RMS. V našem příkladu službu Microsoft RMS plně kvalifikovaný název domény by byl následující hodnotu:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Odstraňte následující složku a všechny soubory, které obsahuje: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Restartujte aplikace Office a instance v Průzkumníku souborů.

### <a name="BKMK_Office2010ForceUpdate"></a>Pouze v systému Office 2010: Jak můžete vynutit aktualizaci změněné vlastní šablony
Úpravou registru v počítačích se systémem Office 2010 můžete nastavit hodnotu, aby změněné šablony jsou aktualizována v počítačích bez čekání na uživatele se odhlásit a znovu zapnout. Můžete také vynutit okamžitou aktualizaci odstranění existujících dat v hodnotě registru.

> [!WARNING]
> Nesprávné použití Editoru registru může způsobit vážné problémy, které mohou vyžadovat přeinstalaci operačního systému. Společnost Microsoft nemůže zaručit, že budete schopni vyřešit problémy vzniklé z nesprávného použití Editoru registru. Pomocí Editoru registru na vlastní nebezpečí.

##### Chcete-li změnit četnost aktualizace

1.  Pomocí Editoru registru, vytvořte novou hodnotu registru s názvem **UpdateFrequency** a definovat celočíselnou hodnotu pro data, která určuje četnost, se ve dnech, chcete-li stáhnout všechny změny do stažené šablony. Vyhledejte cestu registru pro vytvoření této nové hodnoty registru pomocí následující tabulky.

    |Cesta v registru|Typ|Hodnota|
    |--------------------|-------|-----------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_DWORD|UpdateFrequency|

2.  Pokud chcete vynutit okamžitou aktualizaci šablon, přejděte pomocí následujícího postupu. V opačném restartujte nyní aplikací sady Office.

##### Chcete-li vynutit okamžitou aktualizaci

1.  Pomocí Editoru registru, odstranit data **LastUpdatedTime** hodnotu. Například může zobrazit data **2015-04-20T15:52**; odstranit 2015-04-20T15:52, aby mohli zobrazit žádná data. Následující tabulku použijte k vyhledejte cestu registru Chcete-li odstranit tento údaj hodnoty registru.

    |Cesta v registru|Typ|Hodnota|
    |--------------------|-------|-----------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_SZ|lastUpdatedTime|

2.  Odstraňte následující složku a všechny soubory, které obsahuje: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Restartování aplikací sady Office.

## <a name="BKMK_PowerShellTemplates"></a>Odkaz na prostředí Windows PowerShell
Vše, co můžete provést v portálu správy Azure vytvářet a spravovat šablony můžete provést z příkazového řádku pomocí prostředí Windows PowerShell. Kromě toho můžete exportovat a importovat šablony, takže můžete kopírovat šablony mezi klienty nebo provést hromadné úpravy komplexní vlastnosti v šablonách, jako je například vícejazyčné názvy a popisy.

Můžete také použít exportu a importu zálohovat a obnovit vlastní šablony, jako nejlepší postup, pravidelně zálohovat vlastní šablony, takže pokud provedete změny, která nebyla určena, můžete snadno vrátit k předchozí verzi.

> [!IMPORTANT]
> Pomocí prostředí Windows PowerShell vytvořit a spravovat šablony zásad práv Azure RMS, pokud nemáte alespoň verze 2.0.0.0 [modul Windows PowerShell pro službu Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Pokud jste již dříve nainstalovali tento modul prostředí Windows PowerShell, spusťte následující příkaz v okně prostředí PowerShell zkontrolujte číslo verze: `(Get-Module aadrm -ListAvailable).Version`

Instalační pokyny naleznete v tématu [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Rutiny, které podporují vytváření a Správa šablon:

-   [Přidat AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Export AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Import AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [Nové AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Odebrat AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Sada AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)

## Další kroky
Po nakonfigurování vlastní šablony pro Azure Rights Management pomocí [Plán nasazení Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) Zkontrolovat, zda jsou ostatní kroky konfigurace, které chcete provést předtím, než můžete přejít na [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] uživatelům a správcům. Pokud neexistují žádné další kroky konfigurace, které je třeba provést, naleznete v části [Použití služby Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) provozní pokyny pro podporu úspěšné nasazení pro vaši organizaci.

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

