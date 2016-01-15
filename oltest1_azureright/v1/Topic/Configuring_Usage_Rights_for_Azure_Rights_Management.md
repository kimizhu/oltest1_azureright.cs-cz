---
description: na
keywords: na
title: Configuring Usage Rights for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
---
# Konfigurace už&#237;vac&#237; pr&#225;va pro Azure Rights Management
Když použijete šablonu nastavit ochranu na soubory nebo e-mailů pomocí Azure Rights Management (Azure RMS), musíte nakonfigurovat užívací práva sami. Kromě toho když konfigurujete vlastní šablony pro Azure RMS, vyberte užívací práva, bude poté automaticky použita, pokud je šablona vybrána uživatelé, správci, nebo nakonfigurované služby. Například na portálu Azure můžete vybrat role, které konfigurovat logické seskupení práva k používání, nebo můžete nakonfigurovat individuální práva.

Pomocí tohoto tématu vám pomohou nakonfigurovat využití práva, která chcete použít pro aplikaci, kterou používáte a pochopit, jak tato práva jsou interpretovány aplikacemi.

## Užívací práva a popisy
Následující tabulka uvádí a popisuje užívací práva, které podporuje Rights Management a jak jsou používány a interpretovány. V této tabulce **běžný název** je obvykle, jak můžete vidět využití vpravo zobrazí nebo odkazováno jako na více popisný verzi hodnota jednoho slova, která se používá v kódu ( **kódování v zásadě** hodnotu).**Konstanta rozhraní API nebo hodnotu** je název sady SDK pro volání rozhraní MSIPC API, používají při zápisu aplikace podporující RMS, která zkontroluje využití vpravo nebo přidá využití právo na zásadu.

|Běžný název|Kódování v zásad|Popis|Implementace v Office vlastní práva|Název portálu Azure|Název v šablonách služby AD RMS|Konstanta rozhraní API nebo hodnota|Další informace|
|---------------|--------------------|---------|---------------------------------------|-----------------------|-----------------------------------|---------------------------------------|-------------------|
|Úpravy obsahu, úpravy|DOCEDIT|Umožňuje uživateli upravit, uspořádání, formátu nebo filtrovat obsah uvnitř aplikace. Tato možnost neuděluje právo uložit upravené kopie.|Jako součást **změnu** a **Úplné řízení** možnosti.|**Úpravy obsahu**|**Upravit**|Není k dispozici|V aplikacích Office toto právo také umožňuje uživateli k uložení dokumentu.|
|Uložit|UPRAVIT|Umožňuje uživateli uložení dokumentu z jeho aktuálního umístění.|Jako součást **změnu** a **Úplné řízení** možnosti.|**Uložte soubor**|**Uložit**|IPC_GENERIC_WRITEL "UPRAVIT"|V aplikacích Office toto právo také umožňuje uživateli upravit dokument.|
|Komentář|KOMENTÁŘ|Umožňuje přidat poznámky nebo komentáře k obsahu.|Není implementováno|Není implementováno|Není implementováno|IPC_GENERIC_COMMENTL "KOMENTÁŘ"|Toto právo je k dispozici v sadě SDK, je k dispozici jako zásady ad hoc v modulu ochranu RMS pro prostředí Windows PowerShell a nebyla implementována v některých aplikacích dodavatele softwaru. Však není široce používány a není aktuálně podporován aplikace Office.|
|Uložit jako, Export|EXPORT|Umožňuje uložit obsah na jiný název souboru (Uložit jako). V závislosti na aplikaci může být soubor uložen bez ochrany.|Jako součást **změnu** a **Úplné řízení** možnosti.|**Export obsahu (Uložit jako)**|**Exportovat (Uložit jako)**|IPC_GENERIC_EXPORTL "EXPORT"|Toto právo také umožňuje uživateli provádět další možnosti exportu v aplikacích, jako je například **Odeslat do aplikace OneNote**.|
|Vpřed|VPŘED|Umožňuje možnost předávat e-mailovou zprávu a přidejte příjemce **k** a **kopie** řádky.|Odepřen při použití **Nepředávat** standardní zásady.|**Vpřed**|**Vpřed**|IPC_EMAIL_FORWARDL "VPŘED"|Neumožňuje předávání udělení oprávnění jiným uživatelům jako součást akce předávání dál.|
|Úplné řízení|VLASTNÍK|Uděluje všechna práva k dokumentu a lze provádět všechny akce k dispozici.|Jako **Úplné řízení** možnost vlastní.|**Úplné řízení**|**Úplné řízení**|IPC_GENERIC_ALLL "VLASTNÍK"|Zahrnuje možnost odebrat ochranu.|
|Tisk|TISK|Povolí možnosti pro tisk obsahu.|Jako **Tisk obsahu** možnost v vlastní oprávnění. Není individuální nastavení.|**Tisk**|**Tisk**|IPC_GENERIC_PRINTL "TISK|Žádné další informace|
|Odpověď|ODPOVĚĎ|Umožňuje možnost odpověď v e-mailového klienta, aniž by se změny v **k** nebo **kopie** řádky.|Není k dispozici|**Odpověď**|**Odpověď**|IPC_EMAIL_REPLY|Žádné další informace|
|Odpovědět všem|REPLYALL|Umožňuje **Odpovědět všem** možnost v e-mailového klienta, ale neumožňuje uživateli přidat příjemcům **k** nebo **kopie** řádky.|Není k dispozici|**Odpovědět všem**|**Odpovědět všem**|IPC_EMAIL_REPLYALLL "REPLYALL"|Žádné další informace|
|Zobrazení otevřít, číst|ZOBRAZENÍ|Umožňuje uživateli otevřít dokument a zobrazit obsah.|Jako **Číst** vlastní zásady **zobrazení** možnost.|**Zobrazení obsahu**|**Zobrazení**|IPC_GENERIC_READL "ZOBRAZENÍ"|Žádné další informace|
|Kopírování|EXTRAKCE|Povolí možnosti kopírování dat z dokumentu do stejného nebo jiného dokumentu.|Jako **umožňuje uživatelům přístup pro čtení kopírovat obsah** možnost vlastní zásadu.|**Kopírování a extrahování obsahu**|**Extrakce**|IPC_GENERIC_EXTRACTL "VÝPIS"|V některých aplikacích umožňuje také celý dokument uložit nechráněným způsobem.|
|Zobrazit práva|VIEWRIGHTSDATA|Umožňuje uživatelům zobrazit zásady, které jsou použity v dokumentu.|Není implementováno|**Zobrazit přiřazené práva**|**Zobrazit práva**|IPC_READ_RIGHTSL "VIEWRIGHTSDATA"|Ignorovány některých aplikací.|
|Změna oprávnění|EDITRIGHTSDATA|Umožňuje uživateli změnit zásady, které jsou použity v dokumentu. Zahrnuje, včetně odebrání ochrany.|Není implementováno|**Změna oprávnění**|**Upravit práva**|IPC_WRITE_RIGHTSL "EDITRIGHTSDATA"|Žádné další informace|
|Povolit makra|OBJMODEL|Umožňuje možnost spustit makra nebo provádět jiné programové nebo vzdálený přístup k obsahu v dokumentu.|Jako **Povolit programový přístup** možnost vlastní zásadu. Není individuální nastavení.|**Povolit makra**|**Povolit makra**|Není k dispozici|Žádné další informace|

## Práva součástí úrovní oprávnění
Některé aplikace seskupit užívací práva do úrovní oprávnění, aby bylo snazší vyberte užívací práva, které jsou obvykle používány společně. Tyto úrovně permisisons pomoci abstraktní úroveň složitosti od uživatelů, takže se můžete vybrat možnosti, které jsou založené na rolích.  Například **kontrolora** a **spoluautor**. I když tyto možnosti často zobrazit souhrn práv uživatele, se nemusí zahrnovat každých vpravo, která je uvedena v předchozí tabulce.

Následující tabulku použijte k seznam tyto úrovně oprávnění a práva, které obsahují úplný seznam.

|Úroveň oprávnění|Aplikace|Práva (běžný název)|
|--------------------|------------|-----------------------|
|Prohlížeč|Portál Azure<br /><br />Aplikace pro systém Windows pro sdílení obsahu Rights Management|Zobrazení otevřít, číst<br /><br />Odpověď<br /><br />Odpovědět všem|
|Kontrolora|Portál Azure<br /><br />Aplikace pro systém Windows pro sdílení obsahu Rights Management|Zobrazení otevřít, číst<br /><br />Uložit<br /><br />Úpravy obsahu, úpravy<br /><br />Reply<sup>*</sup><br /><br />Odpovědět všem<sup>*</sup><br /><br />Předat dál<sup>*</sup>|
|Spoluautor|Portál Azure<br /><br />Aplikace pro systém Windows pro sdílení obsahu Rights Management|Zobrazení otevřít, číst<br /><br />Uložit<br /><br />Úpravy obsahu, úpravy<br /><br />Kopírování<br /><br />Zobrazit práva<br /><br />Změna oprávnění<br /><br />Povolit makra<br /><br />Uložit jako, Export<br /><br />Tisk<br /><br />Reply<sup>*</sup><br /><br />Odpovědět všem<sup>*</sup><br /><br />Předat dál<sup>*</sup>|
|Spoluvlastník|Portál Azure<br /><br />Aplikace pro systém Windows pro sdílení obsahu Rights Management|Zobrazení otevřít, číst<br /><br />Uložit<br /><br />Úpravy obsahu, úpravy<br /><br />Kopírování<br /><br />Zobrazit práva<br /><br />Změna oprávnění<br /><br />Povolit makra<br /><br />Uložit jako, Export<br /><br />Tisk<br /><br />Reply<sup>*</sup><br /><br />Odpovědět všem<sup>*</sup><br /><br />Předat dál<sup>*</sup><br /><br />Úplné řízení|
<sup>*</sup> Není k dispozici pro aplikace pro systém Windows pro sdílení obsahu Rights Management

## Práva, které jsou součástí výchozí šablony
Práva, které jsou součástí výchozí šablony jsou následující:

|Zobrazovaný název|Práva (běžný název)|
|---------------------|-----------------------|
|&lt; název organizace &gt; - pouze důvěrné zobrazení|Zobrazení otevřít, číst|
|&lt; název organizace &gt; - důvěrné|Zobrazení otevřít, číst<br /><br />Uložit<br /><br />Úpravy obsahu, úpravy<br /><br />Zobrazit práva<br /><br />Povolit makra<br /><br />Vpřed<br /><br />Odpověď<br /><br />Odpovědět všem|

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

