---
description: na
keywords: na
title: Helping Users to Protect Files by Using Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
---
# Pom&#225;h&#225; uživatelům k ochraně souborů pomoc&#237; Azure Rights Management
Po nasazení a nakonfigurovat pro vaši organizaci Azure Rights Management (Azure RMS), zadejte nápovědy a pokyny pro uživatele, správci a vaše oddělení technické podpory:

-   **Informace o koncovém uživateli:**

    Upozornit uživatele, kdy a jak k ochraně dokumenty a e-mailů, které obsahují citlivé informace. Pokud je to možné, zadejte tyto informace pro své stávající pracovní toky, aby zahrnují další kroky procesu již dobře známé, nikoli představení zcela nové procesy. Ujistěte se, zda jste oznámit mu výhod (a rizika), které jsou specifické pro vaši společnost a také poskytuje pokyny pro kdy by měla chránit soubory a e-mailů. Pokud jste nakonfigurovali [vlastní šablony](http://technet.microsoft.com/library/dn642472.aspx), poskytuje pokyny, o který z nich zaškrtněte, pokud název a popis šablony není dostatečné, chcete-li zvolit ten správný.

    > [!TIP]
    > Příklad videa pro koncové uživatele:
    > 
    > -   [Azure RMS uživatelské prostředí](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Sledování Azure RMS dokumentů a zrušení](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informace pro správce:**

    Některé aplikace automaticky použít ochrana informací pomocí zásady a nastavení, které správci konfigurovat. Pro tyto aplikace může být zapotřebí který poskytuje pokyny ostatním správcům, kteří spravují těchto aplikací a služeb. Další informace naleznete v tématu [Jak aplikace podporují Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md) a [Konfigurace aplikací pro Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

-   **Nápověda oddělení technické podpory:**

    Jedním z velmi užitečné nástroje pro oddělení technické podpory je [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437).   Nápověda k oddělení technické podpory operátory lze spustit s možností Správce Azure RMS a jejich lze požádejte uživatele, aby jej spustit s možností uživatele Azure RMS. Tento nástroj můžete nejen pomáhá identifikovat problémy, ale také opravit problémy, zjistí, a pokud ještě není odstraněn, protokoly trasování záznamu.

    Pokud je oprávněné požadavky na přístup úplná práva k chráněné dokumenty, například žádosti o právního oddělení nebo správce, poté, co zaměstnanec opustil organizaci, přesvědčte se oddělení technické podpory procesy žádost o to s využitím Azure RMS [funkce superuživatel](https://technet.microsoft.com/en-us/library/mt147272.aspx).

    Kromě toho zde jsou některé z typické problémů, které uživatelé hlásit:

    -   **Přihlaste se nápovědy:**

        Uživatelé může vyzváni k zadání pověření při Azure RMS potřebuje k ověření uživatele a nelze použít pověření uložená v mezipaměti. Bude jím uživatele pracovní nebo školní účtu a hesla, který je přidružen k služeb Office 365 klienta nebo klienta služby Azure Active Directory. Účet Microsoft (dříve Microsoft Live ID) nebo jejich osobní e-mailového účtu, nesmí být vzhledem k tomu, že tyto nejsou aktuálně podporovány službou Azure RMS. Pokyny k účtu, který má být použita při uživatelé vyzváni k zadání pověření při použití těchto aplikací s Azure RMS poskytovat uživatelům i vaše oddělení technické podpory.

    -   **Problémy s chránit nebo spotřebovávat obsah:**

        Ujistěte se, zda mají uživatelé vhodné pokyny pro aplikace, použijte a používáte aplikací a zařízení, které jsou podporovány službou Azure RMS. Další informace o podporovaných aplikací a zařízení, naleznete v tématu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

        Pokud uživatelé vidí chybu při pokusu o ochraně nebo spotřebovávat obsah, požádejte je ke spuštění [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) jako uživatel Azure RMS.

        Pokud uživatelé sestav, můžete otevřít chráněný obsah, ale nemáte oprávnění, která potřebují, požádejte je ke spuštění [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) jako uživatel Azure RMS a stáhněte si a zobrazení šablon. Tímto způsobem potvrdíte, že se úspěšně stáhli šablony a co práv šablony, které poskytují. Tento problém může být, že uživatel není ve skupině správný, který je nakonfigurován pro šablonu, nebo že šablona potřebuje změny konfigurace pro daného uživatele.

Pomocí níže uvedených částech najdete informace o specifických pro aplikaci uživatelům pomáhá chránit citlivé dokumenty a e-mailů.

## Použití ochrany informace k aplikaci sdílení Rights Management
RMS (Rights Management) aplikace pro sdílení je vyžadována pro uživatele k ochraně a spotřebovávat chráněný obsah v případě, že používají systému Office 2010, ale také doporučuje pro všechny počítače a mobilní zařízení, které podporují Azure RMS.

Kromě usnadňují uživatelům chránit důležité dokumenty, aplikace pro sdílení obsahu RMS uživatelům umožňuje sledování dokumentů, které jsou chráněna a v případě potřeby odvolat přístup k nim.

Chcete-li použít tuto aplikaci pro počítače se systémem Windows naleznete v tématu [Rights Management sdílení aplikace uživatelské příručce](http://technet.microsoft.com/library/dn339006.aspx).

Pro mobilní zařízení, naleznete [Nejčastější dotazy týkající se Microsoft Rights Management sdílení aplikace pro mobilní platformy](http://technet.microsoft.com/dn451248).

> [!TIP]
> Scénář vysoké úrovně příklad s snímky obrazovky, naleznete v části [Uživatelé bezpečně sdílet přílohy s mobilní uživatele](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Example_SharingApp) v oddílu [Co je Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tématu.

## Ochrana informací pomocí služeb Office 365, Office 2016 nebo Office 2013
Pokud používáte Azure RMS a nenainstalovali Rights Management, aplikace pro sdílení, nebude zobrazeno **sdílet chráněné** na pásu karet na tlačítko nebo **chránit místně** z Průzkumníka soubor, který usnadňuje jejich k ochraně souborů. Pro tyto uživatele jsou musí postupujte podle pokynů, podobně jako na tyto.

> [!TIP]
> Chcete-li vyhledat konkrétní aplikace nápovědy a pokyny k používání ochrana údajů s těmito aplikacemi, vyhledejte **IRM** a název aplikace a verze.

#### K ochraně dokumentu v aplikaci Word 2013

1.  Aplikace Microsoft Word vytvořte nový dokument.

2.  Z **soubor** nabídky, klikněte na tlačítko **informace o**, klikněte na tlačítko **Zamknout dokument**, klikněte na tlačítko **omezení přístupu**, a poté zvolte šablonu, kterou chcete rychle použít správné použití práva, nebo vyberte **omezení přístupu** a vyberte práva k používání sami.

    > [!NOTE]
    > Pokud je to poprvé, že jste použili Rights Management, obraťte [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] služeb a budete vyzváni k zadání pověření ke konfiguraci klienta IRM sady Office.

3.  Uložte dokument.

Při otvírání dokumentu, je nejprve ověřen. Pokud nejste oprávněni otevřete dokument, dokument nebude možné otevřít. Pokud jsou oprávněni otevřete dokument, otevře se s právy využití s omezeným přístupem, které byly zadány pro daného uživatele. Můžete například využití vpravo od jen pro čtení neumožňuje uživatele, kterého chcete upravit nebo uložit dokument, i v případě, že je nejprve zkopírovat do jiného umístění. Práva k používání jsou zobrazeny v horní části dokumentu pomocí nápis omezení. Hlavičky může zobrazit oprávnění, které jsou použity k dokumentu nebo ho zadat odkaz na jejich zobrazení.

#### K ochraně e-mailovou zprávu pomocí aplikace Outlook 2013 a systému Exchange Online

1.  V rámci aplikace Outlook vytvořte novou zprávu řešit příjemci v rámci vaší organizace.

2.  Z **Možnosti** klikněte na tlačítko **oprávnění**, a potom vyberte možnost. Příklad: **Nešíří**, **&lt; název společnosti - &gt; důvěrné** nebo **&lt; název společnosti - &gt; pouze důvěrné zobrazení**.

3.  Odešle zprávu.

Podobně k prohlížení chráněný dokument, pokud příjemců přijímat e-mailovou zprávu, budou se nejprve ověřeni. Pokud jsou oprávněni najdete v e-mailová zpráva, otevře se s právy využití s omezeným přístupem, které byly zadány pro daného uživatele. Například pokud jste vybrali možnost **dál**, není k dispozici tlačítko Vpřed na pásu karet.

#### K ochraně e-mailovou zprávu pomocí webové aplikace Outlook

1.  V rámci webové aplikace Outlook vytvořte novou zprávu řešit příjemci v rámci vaší organizace.

2.  Klikněte na tlačítko  **...**,  klikněte na tlačítko **nastavit oprávnění**, a potom vyberte možnost. Příklad: **Nešíří**, **neodpovídejte všechny**, **&lt; název společnosti - &gt; důvěrné** nebo **&lt; název společnosti - &gt; pouze důvěrné zobrazení**.

3.  Odešle zprávu.

Podobně k prohlížení chráněný dokument, pokud příjemců přijímat e-mailovou zprávu, budou se nejprve ověřeni. Pokud jsou oprávněni najdete v e-mailová zpráva, otevře se s právy využití s omezeným přístupem, které byly zadány pro daného uživatele. Například pokud jste vybrali možnost **proveďte není Odpovědět všem**,  **Odpovědět všem** možnost v okně zprávy není k dispozici.

## Viz také
[Použití služby Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

