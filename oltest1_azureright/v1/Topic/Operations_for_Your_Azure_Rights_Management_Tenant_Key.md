---
description: na
keywords: na
title: Operations for Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
---
# Operace pro kl&#237;č klienta Azure Rights Management
V závislosti na klienta klíče topologii (spravované společnosti Microsoft nebo spravované zákazníka) mají různé úrovně řízení a odpovědnost za váš klíč klienta Microsoft Azure Rights Management (Azure RMS) poté, co je implementována.

Při správě vlastní klíč klienta, je to často označována jako přenést vlastní klíč (BYOK). Další informace o tento scénář a můžete si vybrat mezi klíče topologie dvou klienta naleznete v tématu [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

V následující tabulce jsou uvedeny operací, které je možné provést, v závislosti na topologii, který jste zvolili pro klíč klienta Azure RMS.

|Operace životního cyklu|Spravované společnosti Microsoft (výchozí)|Spravované zákazníků (BYOK)|
|---------------------------|----------------------------------------------|-------------------------------|
|Odvolání váš klíč klienta|Žádné (automaticky)|Žádné (automaticky)|
|Znovu klíč váš klíč klienta|Ano|Ano|
|Zálohování a obnovení klíče vašeho klienta|Ne|Ano|
|Exportovat své klíč klienta|Ano|Ne|
|Odpovědět na porušení|Ano|Ano|
Poté, co jste určili topologie, které je implementována, použijte jednu z následujících částí Další informace o těchto operací pro klíč klienta Azure RMS.

## <a name="BKMK_MSManagedOperations"></a>Spravované společnosti Microsoft: Operace klíče životního cyklu klienta
Pokud společnost Microsoft spravuje váš klíč klienta pro Azure Rights Management (výchozí), použijte v následujících částech Další informace o životního cyklu operace, které jsou relevantní pro tento topologie:

-   [Odvolání váš klíč klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRevoke)

-   [Znovu klíč váš klíč klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)

-   [Zálohování a obnovení klíče vašeho klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBackup)

-   [Exportovat své klíč klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSExport)

-   [Odpovědět na porušení](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBreach)

### <a name="BKMK_MSRevoke"></a>Odvolání váš klíč klienta
Při odhlásíte odběr Azure RMS, Azure RMS zastaví pomocí vašeho klienta klíče a od vás není vyžadována žádná akce.

### <a name="BKMK_MSRekey"></a>Znovu klíč váš klíč klienta
Opětovného zadávání je také označován jako postupných váš klíč. Není znovu klíč váš klíč klienta Pokud to není ve skutečnosti nezbytné. Starší klienty, například systému Office 2010, nebyly určeny ke zpracování řádném klíče změny. V tomto případě je nutné zrušit stav služby RMS na počítačích pomocí zásad skupiny nebo ekvivalentní mechanismus. Jsou však některé legitimní události, které může požadovat, abyste si znovu klíč váš klíč klienta. Příklad:

-   Má vaše společnost rozděleny do dvou nebo více společností. Při přepracování vašeho klienta klíče nové společnosti nebude mít přístup k nový obsah, který publikovat vaše zaměstnance. Původní obsah přístupem případě, že mají kopii starý klíč klienta.

-   Budete mít dojem, že byl prozrazeny hlavní kopii klíče klienta (kopie vašeho k dispozici).

Váš klíč klienta lze znovu klíč voláním služby podpory zákazníků společnosti Microsoft (CSS) a kontroly správce klienta.

Při přepracování vašeho klienta klíče nový obsah je chráněn pomocí nový klíč klienta. K tomu dojde do několika fází rozdělený způsobem, takže časovém intervalu, bude pokračovat v některé nový obsah být chráněny pomocí starý klíč klienta. Chráněný obsah dříve chráněn na váš klíč klienta. Pro podporu tohoto scénáře, Azure RMS zachová původní klíč klienta tak, aby ji může vydávat licence pro původní obsah.

### <a name="BKMK_MSBackup"></a>Zálohování a obnovení klíče vašeho klienta
Společnost Microsoft není zodpovědná za zálohování váš klíč klienta a nevyžaduje se žádný zásah od vás.

### <a name="BKMK_MSExport"></a>Exportovat své klíč klienta
Konfigurace služby RMS Azure a klíč klienta můžete exportovat postupujte podle pokynů v těchto tří kroků:

##### Krok 1: Zahájení exportu

-   Chcete-li to provést, kontaktujte služby podpory společnosti Microsoft zákazníkům (CSS). Musí být, že jste přihlášeni jako správce vašeho klienta Azure RMS.

##### Krok 2: Počkejte, ověření

-   Společnost Microsoft ověří, zda je legitimní vašeho požadavku k uvolnění váš klíč klienta služby RMS. To může trvat až 3 týdny.

##### Krok 3: Zobrazí pokyny klíče z šablony stylů CSS

-   Služby podpory zákazníků společnosti Microsoft (CSS) vám odešle konfigurace služby RMS Azure a klíč klienta jako šifrovaná v heslem chráněný soubor, který má příponu názvu souboru .tpd. Chcete-li to provést, šablon stylů CSS nejprve vám odešle (jako osoba, která iniciované exportu) nástroj e-mailem. Je nutné spustit nástroj z příkazového řádku takto:

    ```
    AadrmTpd.exe -createkey
    ```
    Tato akce generuje dvojici klíč RSA a uloží veřejné a soukromé poloviny jako soubory v aktuální složce. Příklad: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** a **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Odpovědět na e-mailu z šablony stylů CSS, připojení k souboru, který má název, který začíná **PublicKey**. Šablony stylů CSS v dalším obdržíte důvěryhodné domény publikování souboru jako soubor .xml, který je šifrován klíč RSA. Zkopírujte tento soubor do stejné složky, protože jste spustili nástroj AadrmTpd původně a spusťte nástroj znovu, pomocí souboru, který začíná **PrivateKey** a soubor ze šablon stylů CSS. Příklad:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    Výstup tohoto příkazu by měl být dva soubory: Jeden obsahuje heslo ve formátu prostého textu pro důvěryhodné domény publikování chráněná heslem a druhá je chráněn heslem důvěryhodné domény publikování samotného. Pro účely křížových odkazů, jak by měl mít stejný identifikátor GUID jako veřejné a soukromé klíče soubory z když jste spustili příkaz - createkey AadrmTpd.exe:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Zálohovat tyto soubory a ukládat je bezpečně, aby bylo zajištěno, že můžete pokračovat v dešifrovat obsah, který je chráněn s Tento klíč klienta. Kromě toho při migraci na službu AD RMS, můžete importovat tento soubor důvěryhodné domény publikování (soubor, který začíná **ExportedTDP**) k serveru služby AD RMS.

##### Krok 4: Probíhající: Chránit váš klíč klienta

-   Poté, co se zobrazí váš klíč klienta, zachovat ji dobře chráněné, protože někdo získá přístup k němu, jejich dešifrování všechny dokumenty, které jsou chráněny pomocí tohoto klíče.

    Je-li důvod pro export váš klíč klienta vzhledem k tomu, že již nechcete používat Azure RMS jako s osvědčenými postupy, nyní deaktivujte vašeho klienta služby RMS. Není zpoždění tím poté, co obdržíte váš klíč klienta vzhledem k tomu, že toto opatření, které vám pomohou minimalizovat důsledky, pokud klíč klienta pracuje s někdo, kdo nesmí obsahovat. Pokyny naleznete v tématu [Vyřazování z provozu a deaktivace Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

### <a name="BKMK_MSBreach"></a>Odpovědět na porušení
Žádné systému zabezpečení, bez ohledu na to, jak silné je dokončena bez porušení procesu odpovědi. Váš klíč klienta může být ohrožena nebo odcizení. I v případě, že je dobře chráněn dobře, může v aktuální generaci hardwarového zabezpečení technologie nebo aktuální délky klíčů a algoritmy nalézt slabá místa.

Společnost Microsoft má vyhrazený týmu k reakci na zabezpečení incidenty ve svých produktů a služeb. Jakmile je důvěryhodných sestavy incidentu, má být prověřen z oboru, hlavní příčinu a skutečnosti snižující závažnost rizika mezi tohoto týmu. Ovlivní-li tento incident majetku, pak Microsoft vás upozorní, správce klienta Azure RMS e-mailem s použitím na adresu, kterou jste zadali, když jste odběru.

Pokud máte porušení, doporučené akce, která vám nebo společnost Microsoft může trvat závisí na rozsahu porušení; Společnost Microsoft bude fungovat se můžete pomocí tohoto procesu. Následující tabulce jsou uvedeny některé typické situace a pravděpodobně odpověď, přestože přesná odpověď bude záviset na veškeré informace, které je odhalila během řízení.

|Popis incidentu|Pravděpodobně odpovědi|
|-------------------|--------------------------|
|Váš klíč klienta byly prozrazeny.|Znovu klíč váš klíč klienta. Podívejte se na téma [Znovu klíč váš klíč klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey) v tomto tématu.|
|Neoprávněný jednotlivce nebo malwaru máte práva k používání váš klíč klienta, ale klíč samotný není nevrací.|Opětovného zadávání váš klíč klienta nepomůže zde a vyžaduje analýzu hlavní příčinu. Byla-li chybu procesu nebo softwaru zodpovědná za neoprávněným jednotlivce, chcete-li získat přístup, že tato situace musí být převeden.|
|Staňte se rovněž proveditelné chybu zjištěných v algoritmus RSA nebo délka klíče nebo útoky hrubou silou.|Společnost Microsoft musí aktualizovat Azure RMS pro podporu nových algoritmů a delší délky klíčů, které jsou pružné a dát pokyn, všem zákazníkům, aby obnovit jejich klíče klienta.|

## <a name="BKMK_BYOKManagedOperations"></a>Spravované zákazníka: Operace klíče životního cyklu klienta
Pokud spravovat váš klíč klienta pro Azure Rights Management (přenést vlastní klíč nebo BYOK, scénář), pomocí následujících částí Další informace o životního cyklu operace, které jsou relevantní pro tento topologie:

-   [Odvolání váš klíč klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRevoke)

-   [Znovu klíč váš klíč klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)

-   [Zálohování a obnovení klíče vašeho klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBackup)

-   [Exportovat své klíč klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKExport)

-   [Odpovědět na porušení](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBreach)

### <a name="BKMK_BYOKRevoke"></a>Odvolání váš klíč klienta
Při odhlásíte odběr Azure RMS, Azure RMS zastaví pomocí vašeho klienta klíče a od vás není vyžadována žádná akce.

### <a name="BKMK_BYOKRekey"></a>Znovu klíč váš klíč klienta
Opětovného zadávání je také označován jako postupných váš klíč. Není znovu klíč váš klíč klienta Pokud to není ve skutečnosti nezbytné. Starší klienty, například systému Office 2010, nebyly určeny ke zpracování řádném klíče změny. V tomto případě je nutné zrušit stav služby RMS na počítačích pomocí zásad skupiny nebo ekvivalentní mechanismus. Jsou však některé legitimní události, které může požadovat, abyste si znovu klíč váš klíč klienta. Příklad:

-   Má vaše společnost rozděleny do dvou nebo více společností. Při přepracování vašeho klienta klíče nové společnosti nebude mít přístup k nový obsah, který publikovat vaše zaměstnance. Původní obsah přístupem případě, že mají kopii starý klíč klienta.

-   Budete mít dojem, že byl prozrazeny hlavní kopii klíče klienta (kopie vašeho k dispozici).

Při přepracování vašeho klienta klíče nový obsah je chráněn pomocí nový klíč klienta. K tomu dojde do několika fází rozdělený způsobem, takže časovém intervalu, bude pokračovat v některé nový obsah být chráněny pomocí starý klíč klienta. Chráněný obsah dříve chráněn na váš klíč klienta. Pro podporu tohoto scénáře, Azure RMS zachová původní klíč klienta tak, aby ji může vydávat licence pro původní obsah.

K přepracování vašeho klienta klíče, generování a vytvořte nový klíč prostřednictvím Internetu nebo osobně, a to pomocí postupů v [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) oddílu z [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tématu.

### <a name="BKMK_BYOKBackup"></a>Zálohování a obnovení klíče vašeho klienta
Jste zodpovědní za zálohování váš klíč klienta. Pokud váš klíč klienta je generován v hardwarového zabezpečení společnosti Thales, zálohovat klíč, stačí zálohujte Tokenizovaná klíč souboru, souboru světě a správce karet.

Pokud přenesených váš klíč pomocí následujících postupů v [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) oddílu z [Plánování a implementaci váš Azure Rights Management klienta klíč](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tématu, Azure RMS uchová souboru Tokenizovaná klíč k ochraně proti selhání všech uzlů Azure RMS. Však nebere v úvahu to být úplné zálohování. Můžete například budete-li potřebovat kopii váš klíč k použití mimo hardwarového zabezpečení společnosti Thales ve formátu prostého textu, Azure RMS nebude možné načíst pro vás, protože nemá neobnovitelná kopie.

### <a name="BKMK_BYOKExport"></a>Exportovat své klíč klienta
Pokud používáte BYOK, z Azure RMS nelze exportovat klíč klienta. Kopie v Azure RMS je neobnovitelná. Pokud chcete odstranit tento klíč, takže lze nadále používat, kontaktujte služby podpory společnosti Microsoft zákazníkům (CSS).

### <a name="BKMK_BYOKBreach"></a>Odpovědět na porušení
Žádné systému zabezpečení, bez ohledu na to, jak silné je dokončena bez porušení procesu odpovědi. Váš klíč klienta může být ohrožena nebo odcizení. I v případě, že je dobře chráněn dobře, může v aktuální generaci hardwarového zabezpečení technologie nebo aktuální délky klíčů a algoritmy nalézt slabá místa.

Společnost Microsoft má vyhrazený týmu k reakci na zabezpečení incidenty ve svých produktů a služeb. Jakmile je důvěryhodných sestavy incidentu, má být prověřen z oboru, hlavní příčinu a skutečnosti snižující závažnost rizika mezi tohoto týmu. Ovlivní-li tento incident majetku, pak Microsoft vás upozorní, správce klienta Azure RMS e-mailem s použitím na adresu, kterou jste zadali, když jste odběru.

Pokud máte porušení, doporučené akce, která vám nebo společnost Microsoft může trvat závisí na rozsahu porušení; Společnost Microsoft bude fungovat se můžete pomocí tohoto procesu. Následující tabulce jsou uvedeny některé typické situace a pravděpodobně odpověď, přestože přesná odpověď bude záviset na veškeré informace, které je odhalila během řízení.

|Popis incidentu|Pravděpodobně odpovědi|
|-------------------|--------------------------|
|Váš klíč klienta byly prozrazeny.|Znovu klíč váš klíč klienta. Podívejte se na téma [Znovu klíč váš klíč klienta](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey) v tomto tématu.|
|Neoprávněný jednotlivce nebo malwaru máte práva k používání váš klíč klienta, ale klíč samotný není nevrací.|Opětovného zadávání váš klíč klienta nepomůže zde a vyžaduje analýzu hlavní příčinu. Byla-li chybu procesu nebo softwaru zodpovědná za neoprávněným jednotlivce, chcete-li získat přístup, že tato situace musí být převeden.|
|Chyba zjištěných v technologii aktuální generování hardwarového zabezpečení.|Společnost Microsoft musí aktualizovat moduly hardwarového zabezpečení. Pokud existuje důvod se domnívat, že chybu vystaveny klíče, bude společnost Microsoft pokyn všem zákazníkům, aby obnovit jejich klíče klienta.|
|Staňte se rovněž proveditelné chybu zjištěných v algoritmus RSA nebo délka klíče nebo útoky hrubou silou.|Společnost Microsoft musí aktualizovat Azure RMS pro podporu nových algoritmů a delší délky klíčů, které jsou pružné a dát pokyn, všem zákazníkům, aby obnovit jejich klíče klienta.|

## Viz také
[Použití služby Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

