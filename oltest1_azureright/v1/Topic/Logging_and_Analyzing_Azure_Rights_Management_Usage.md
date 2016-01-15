---
description: na
keywords: na
title: Logging and Analyzing Azure Rights Management Usage
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# Protokolov&#225;n&#237; a anal&#253;za využit&#237; Azure Rights Management
Použijte informace v tomto tématu vám pomohou pochopit, jak můžete použít využití protokolování s Azure Rights Management (Azure RMS). Služba Azure Rights Management můžete přihlásit každý požadavek je pro vaši organizaci, které zahrnují požadavky od uživatelů, Rights Management správci ve vaší organizaci provedené akce a akce prováděné operátory společnosti Microsoft pro podporu nasazení Azure Rights Management.

Poté můžete provádět tyto protokoly Azure Rights Management pro podporu obchodní scénářů:

-   Při analýze pro obchodní statistiky.

    Azure Rights Management zapisuje do účtu úložiště Azure, které poskytujete protokoly ve formátu rozšířené protokolu W3C. Tyto protokoly mohou pak směrovat do úložiště zvoleného (například databáze, systém (OLAP) online analytical processing nebo mapy snížit system) a analyzovat informace o vytváření sestav. Jako příklad může identifikovat, kdo přistupuje k vaší RMS chráněná data. Můžete určit, co jsou přístup lidé RMS chráněná data a z jaké zařízení a odkud. Můžete zjistit, zda mohou uživatelé úspěšně číst chráněný obsah. Můžete také určit, které osoby přečetli důležitý dokument, který byl chráněn.

-   Monitorování urážlivý příspěvek.

    Azure Rights Management protokolování informací je k dispozici v téměř v reálném čase, takže mohou průběžně sledovat vaše společnost použití Rights Management. 99,9 % protokoly jsou k dispozici v rámci 15 minut akce inicioval RMS.

    Například můžete být upozorněni, pokud je náhlé zvýšení osob čtení dat chráněného službou RMS mimo standardní pracovní dobu, po které může znamenat, že uživatel se zlými úmysly je shromažďování informací o prodávat konkurencí. Nebo pokud jednomu uživateli zjevně přistupuje data ze dvou různých IP adres v rámci krátkého formátu času, které by mohly být známkou účet uživatele došlo k ohrožení zabezpečení.

-   Provedení forenzní analýzy.

    Pokud máte nevracení informace, budete pravděpodobně požádáni, kdo nedávno použitých konkrétní dokumenty a jaké informace podezření osoba přístup nedávno. Tyto typ otázky můžete odpovědět, pokud používáte Azure Rights Management a protokolování, protože obsah chráněný uživateli, kteří používají musí vždy získat licenci Rights Management otevřete dokumenty a obrázky, které jsou chráněné službou Azure Rights Management, i když jsou tyto soubory přesunout e-mailem nebo zkopírován do jednotky USB nebo jiná zařízení úložiště. To znamená, že můžete používat protokoly Azure Rights Management jako konečné zdroje informací pro forenzní analýzy při ochraně dat pomocí Azure Rights Management.

> [!NOTE]
> Pokud vás zajímá pouze v protokolování úlohy správy pro Azure Rights Management a proveďte není chcete sledovat, jak uživatelé používají Rights Management, můžete použít [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) rutiny prostředí Windows PowerShell pro Azure Rights Management.
> 
> Můžete také na portálu Azure pro sestavy využití vysoké úrovně, které zahrnují **RMS využití**, **Nejaktivnější uživatelé RMS**, **využití zařízení RMS**, a **RMS povoleno použití aplikací**. Tyto sestavy z portálu Azure, klikněte na tlačítko **služby Active Directory**, vyberte a otevřete adresář a potom klikněte na tlačítko **sestavy**,

Další informace o protokolování využití Azure Rights Management pomocí následujících částí.

-   [Jak povolit protokolování využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_EnableRMSLogging)

-   [Přístup a použití protokolů využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)

-   [Jak spravovat úložiště protokolu Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_ManageStorage)

-   [Jak mohou delegovat přístup do protokolů využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)

-   [Jak interpretovat protokolů využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)

-   [Odkaz na prostředí Windows PowerShell](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_PowerShell)

## <a name="BKMK_EnableRMSLogging"></a>Jak povolit protokolování využití Azure Rights Management
Protokolování využití Azure Rights Management je volitelné, takže pokud chcete používat, musí provést určité kroky. Použijete-li protokolování využití Azure Rights Management, nedošlo ke změně v principu Rights Management a samotný proces protokolování je zdarma. Nicméně je nutné zadat účet úložiště Azure protokolů a vám bude účtována pro toto úložiště.

Než začnete, ujistěte se, že jsou splněny následující podmínky pro použití protokolování využití Azure Rights Management:

|Požadavek|Další informace|
|-------------|-------------------|
|Předplatné spravované IT, které zahrnuje Azure Rights Management|Musí mít předplatné Microsoft Azure Rights Management, které spravuje vaše organizace. Organizace, které používají služby RMS pro jednotlivce nelze použít protokolování využití Azure Rights Management.<br /><br />Pokud má vaše organizace uživatelé, kteří používají RMS pro jednotlivce, protokolování využití Azure Rights Management poskytuje velmi závažný důvod obchodní k převést RMS pro jednotlivce předplatné Microsoft Azure Rights Management.<br /><br />Další informace o odběry, které zahrnují Azure RMS najdete v části [Cloud odběry, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) v oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu.<br /><br />Další informace o RMS pro jednotlivce naleznete v tématu [RMS pro jednotlivce i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|Předplatné Azure.|Musí mít předplatné Azure a dostatečné úložiště v Azure pro protokolů Azure Rights Management.|
|Prostředí Windows PowerShell pro Azure Rights Management|Pokud jste tak již neučinili, stáhněte a nainstalujte modul Windows PowerShell pro Azure Rights Management. Ke konfiguraci a správě protokolů využití Azure Rights Management budou používat rutiny prostředí Windows PowerShell.<br /><br />Další informace naleznete v tématu [Instalace prostředí Windows PowerShell pro službu Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).|
Pomocí následujícího postupu povolíte protokolování využití Azure Rights Management, který obsahuje kroky k vytvoření účtu úložiště Azure a pak nakonfigurujte Azure pro Rights Management protokolů pomocí tohoto účtu úložiště.

> [!NOTE]
> Tento postup předpokládá, že máte účet Azure. Protokolování využití Azure Rights Management podporuje samostatné účty, ale jako nejlepší postup použít pracovní nebo školní účty. Kromě toho doporučujeme vytvořit účet úložiště vyhrazené pro protokolů Rights Management. Přístupové klávesy úložiště musí sdílet s Azure Rights Management a potenciálně s jinými uživateli, pokud budou používat také soubory protokolů.
> 
> Další informace o Azure úložiště naleznete v tématu [Azure dokumentace pro úložiště](http://azure.microsoft.com/documentation/services/storage/).

#### Postup vytvoření účtu úložiště a povolit protokolování využití Azure Rights Management

1.  Přihlaste se k [portálu Azure](https://manage.windowsazure.com/).

2.  Vyberte **úložiště**.

    > [!TIP]
    > Pokud se tato možnost nezobrazí, zkontrolujte, zda je předplatné Azure kromě předplatné pro Rights Management.

3.  Klikněte na tlačítko **vytvořit účet úložiště A** a pro **Adresa URL**, zadejte jedinečný název pro účet úložiště a v případě potřeby změňte **umístění nebo SPŘAŽENÍ skupiny** tak, aby odpovídalo vaší oblasti.

4.  Klikněte na tlačítko **OK**, a počkejte, dokud se nezobrazí název vašeho úložiště zobrazit stav **Online**.

5.  Klikněte na tlačítko **Spravovat přístupové klávesy**.

6.  Z **Spravovat přístupové klávesy** dialogové okno zobrazující váš primární a sekundární přístupové klávesy primární přístupový klíč zkopírovat do schránky a pak zavřete dialogové okno.

7.  Spusťte prostředí Windows PowerShell se **Spustit jako správce** možnost. Spuštění [Připojit AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) příkaz k připojení ke službě Azure Rights Management:

    ```
    Connect-AadrmService
    ```

8.  Použití [Set AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) příkaz k určení, kde chcete zachovat protokolů využití Azure Rights Management, nahrazení *&lt; Access_Key &gt;* s primární přístupový klíč, který jste zkopírovali v kroku 6 a *&lt; StorageAccount &gt;* s názvem účtu úložiště, které jste vytvořili v kroku 3:

    ```
    $accesskey = convertto-securestring -asplaintext -force –string <Access_Key> Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <StorageAccount>
    ```

9. Použití [Povolení AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx) příkaz povolte protokolování využití Azure Rights Management:

    ```
    Enable-AadrmUsageLogFeature
    ```
    Zobrazí se zpráva: **Funkce protokolu využití je povolena pro službu Rights management.**

Teď, když je povoleno protokolování využití, Azure Rights Management začne protokolovat všechny akce pro vaši organizaci a uloží tyto informace do účtu úložiště. Protokolování informací není k dispozici před tento bod.

## <a name="BKMK_AccesAndUseLogs"></a>Přístup a použití protokolů využití Azure Rights Management
Azure Rights Management zapíše protokoly ke svému účtu úložiště Azure jako řadu objektů BLOB. Každý objekt blob obsahuje jeden nebo více záznamů protokolu ve formátu rozšířené protokolu W3C. Objekt blob názvy jsou čísla v pořadí, ve kterém byly vytvořeny.[Jak interpretovat protokolů využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret) Později v tomto dokumentu obsahuje další informace o obsah protokolu a jejich vytvoření.

Může trvat nějakou dobu protokoly se zobrazí v účtu úložiště po akci Azure Rights Management. Většina protokoly se zobrazí v rámci 15 minut.

Účet úložiště, který jste vytvořili pro použití protokolů Azure Rights Management je jako poštovní schránky a čtení přímo z účtu úložiště podporuje, ale není optimalizována pro použití tímto způsobem. Místo toho pro nejlepší výkon a snížit náklady, doporučujeme stáhnout protokoly do místního úložiště, jako místní složku, databáze nebo mapy snížit úložiště.

Můžete stáhnout protokolů využití dvěma způsoby:

-   Pomocí rutiny prostředí Windows PowerShell [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx).

    Toto je nejjednodušší způsob, jak získat přístup k využití protokolů. Tato rutina stáhne protokoly k počítači, stahování každý objekt blob jako soubor do umístění, které zadáte.

-   Použití [SDK úložiště Azure](http://www.windowsazure.com/en-us/develop/net/) psát vlastní aplikace ke stažení protokoly.

    Vlastní aplikace můžete zadat více flexibility než Rutina Get-AadrmUsageLogs. Můžete například chtít delegovat stažení protokoly někomu nebo proces, který se nesmí používat vaše pověření pro správu Azure Rights Management. Nebo můžete chtít dotazovat protokolů v reálném čase, protože chcete sledovat pro zneužití.

#### Chcete-li stáhnout protokolů využití pomocí prostředí PowerShell

-   Spusťte prostředí Windows PowerShell se **Spustit jako správce** a spusťte **Get-AadrmUsageLog –Path &lt;location&gt;**. Například po vytvoření složky s názvem **logs** na jednotce E:

    -   Chcete-li stáhnout všechny dostupné protokoly do složky E:\logs: `Get-AadrmUsageLog -Path "e:\logs"`

    -   Chcete-li stáhnout na konkrétní rozsah objektů blob: `Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047`

Při spuštění těchto rutin prostředí Windows PowerShell zobrazí název poslední objekt blob, který byl stažen. Tento název můžete přiřadit k proměnné, které vám umožní spustit Get-AadrmUsageLog ve smyčce nebo naplánovat úlohu, stahování pokaždé, když pouze přírůstkové protokolů.

Příklad:

**PS C:\ &gt; $LastBlobName = Get-AadrmUsageLog – cesta "e:\logs"**

**1527**

**PS C:\ &gt; $LastBlobName**

**1527**

> [!TIP]
> Všechny stažené soubory protokolu do formátu CSV lze agregovat pomocí [analyzátoru protokolu společnosti Microsoft](http://www.microsoft.com/download/details.aspx?id=24659), což je nástroj pro převod mezi různé formáty dobře známé protokolu. Můžete také tento nástroj použijte k převedení dat do formátu SYSLOG nebo importovat do databáze. Po instalaci nástroje spustit **LogParser.exe /?** pro nápovědu a informace o použití tohoto nástroje. Například může spustit následující příkaz pro import všech informací do souboru .log ve formátu: **logparser –i:w3c –o:csv “SELECT &#42; INTO AllLogs.csv FROM &#42;.log”**.

Můžete pozastavit a obnovit protokolování využití. Po pozastavení protokolování Azure Rights Management uchovává informace o účtu úložiště, tak, že můžete snadno obnovit protokolování znovu.

#### Pozastavení a obnovení protokolování využití

-   Chcete-li pozastavit protokolování, použijte následující rutinu: [Zakázat AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   Chcete-li obnovit protokolování, použijte následující rutinu: [Povolit AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   Chcete-li zkontrolovat, zda je povoleno protokolování, použijte následující rutinu: [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

    Hodnota **True** znamená, že je povoleno protokolování využití Azure Rights Management a hodnotu **False** znamená, že je zakázáno protokolování využití.

## <a name="BKMK_ManageStorage"></a>Jak spravovat úložiště protokolu Azure Rights Management
Jsou zodpovědné úložného prostoru, který slouží k ukládání protokolů Azure Rights Management.

Azure Rights Management nemá žádné Automatická správa souborů protokolu využití. Pokud žádná akce zůstanou v účtu úložiště. Chcete-li ušetřit místo a snížit náklady na úložiště, můžete však je po stažení je odstranit. Nebo můžete vybrat soubory, které chcete odstranit. S jednou výjimkou Azure Rights Management nepoužívá tyto soubory protokolu, takže neexistují žádná omezení o při jejich odstranění.

Soubor, který nesmí odstranit (nebo upravit) je pojmenován **metadata** v **rms metadata** kontejneru. Azure Rights Management používá ke sledování Číslo poslední objekt blob, která je použita tohoto objektu blob. Pokud tento soubor bude odstraněn, Azure Rights Management začíná objektu blob číslo začínající od 1 nový kontejner protokolů, a všechny budoucí stahované soubory, které použijte rutinu Get-AadrmUsageLog použít tento nový kontejner ke stahování souborů protokolu. V důsledku toho všechny protokoly v původní kontejneru jsou zachovány, ale osamocený. Jediný způsob, jak stáhnout tyto osamocené protokoly je použití úložiště Azure SDK.

> [!TIP]
> Namísto Správa protokolu úložiště Azure Rights Management, můžete delegovat tato funkce řízení na jiné společnosti sdílením vaše úložiště účet název a přístupový klíč. Další informace naleznete v tématu [Jak mohou delegovat přístup do protokolů využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate) později v tomto tématu.

V některých případech můžete chtít znovu generovat přístupové klávesy vašeho úložiště. Příklad:

-   Můžete změnit společnost, která spravuje protokolů využití Azure Rights Management.

-   Máte podezření, že vaše úložiště přístupový klíč dojde k ohrožení.

V takovém případě vám toto je při použití sekundární přístupový klíč (na předpokladu, že jste používali dříve primární přístupový klíč) Chcete-li zajistit kontinuitu služeb. Při obnovení přístupový kód, který nebyl dříve používali poté nakonfigurovat Azure Rights Management pomocí nového klíče. Pomocí následujícího postupu znovu vygenerovat sekundární přístupový klíč a konfigurovat Azure Rights Management používat:

#### Chcete-li znovu vygenerovat sekundární přístupový klíč

1.  Přihlaste se k [portálu Azure](https://manage.windowsazure.com/).

2.  Vyberte **úložiště**.

3.  Klikněte na tlačítko **Spravovat přístupové klávesy**.

4.  V **Spravovat přístupové klávesy** dialogové okno, klikněte na tlačítko **znovu vygenerovat** vedle sekundární přístupový klíč a zkopírujte nový sekundární přístupový klíč do schránky.

5.  Spusťte prostředí Windows PowerShell s **Spustit jako správce** možnost a použít [Set AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) rutiny konfigurace Azure Rights Management používat tento nový klíč přístup k nahrazení *&lt; StorageAccount &gt;* s názvem účtu úložiště a *&lt; Access_Key &gt;* s obnoveného sekundární přístupový klíč, který jste zkopírovali:

    ```
    Set-AadrmUsageLogStorageAccount -StorageAccount <StorageAccount>-AccessKey <Access_Key>
    ```
    > [!WARNING]
    > I když můžete přepnout na jiný účet úložiště při spuštění tohoto příkazu, tato akce osamocení předchozí protokoly a jejich, přestane být přístupný pro rutiny Set-AadrmUsageLogStorageAccount nebo podobné příkazy pro správu a funkce.

6.  Zpět **Spravovat přístupové klávesy** dialogové okno pole, znovu vygenerovat primární přístupový klíč.

## <a name="BKMK_Delegate"></a>Jak mohou delegovat přístup do protokolů využití Azure Rights Management
Můžete delegovat přístup na protokolů RMS pomocí sdílení vašeho úložiště název účtu a přístup klíč. Můžete delegovat přístup k jiným správcem, vývojáři v rámci vlastní organizaci nebo nezávislý dodavatel softwaru (ISV). Vzhledem k tomu, že nebude mít pověření správce služby RMS, nemohou používat rutiny Get-AardrmUsageLog ke stažení protokoly RMS. Místo toho musí použít sady SDK úložiště systému Windows ke stažení protokoly. Případně se můžete vytvářet aplikace pro čtení protokoly přímo z úložiště Azure.

Je bezpečné sdílení vašeho úložiště název účtu a přístup klíč tímto způsobem, pokud účet úložiště je vyhrazen pro váš protokoly RMS. I když mají jiní uživatelé přístupový klíč, to nemohou používat pro přístup k jiný účet úložiště nebo použít váš účet klienta služby RMS.

## <a name="BKMK_Interpret"></a>Jak interpretovat protokolů využití Azure Rights Management
Pomocí následujících informací vám pomůže interpretovat protokoly použití Azure Rights Management.

### Rozložení účet úložiště
Při prvním Azure Rights Management zapíše protokoly ke svému účtu úložiště, vytvoří následující dva kontejnery:

-   **Rms metadata**: Tento kontejner je vyhrazena pro Azure Rights Management. Úpravy nebo odstranění tohoto kontejneru.

-   **Rms - protokoly - &lt; guid &gt;**: Je tento kontejner kde Azure Rights Management vytvoří a uloží protokoly. Můžete bezpečně odstranit všechny soubory v tomto kontejneru, pokud již nechcete protokolování informací, které obsahují.

V průběhu času může vytvořit další Azure Rights Management **Rms - protokoly - &lt; guid &gt;** kontejnery. Například pokud **Rms metadata** kontejneru je poškozena nebo náhodnému odstranění, Azure Rights Management obnoví jeho obsah a vytvoří novou **Rms - protokoly - &lt; guid &gt;** kontejner pro všechny budoucí protokoly. Staré protokoly v kontejneru staré nebudou odstraněny, ale jsou osamocený.

### Pořadí protokolu
Azure Rights Management zapíše protokoly jako řadu objektů BLOB. Každý objekt blob obsahuje jeden nebo více záznamů protokolu v rozšířené formát protokolu W3C.

Název každého objektu blob je číslo. V rámci každého kontejneru protokolu je první objekt blob s názvem 000000001. Každý objekt blob je postupně pojmenované v pořadí, ve kterém byl vytvořen. Každý objekt blob obsahuje jeden nebo více záznamů protokolu. Každý záznam protokolu má časové razítko UTC, která označuje, kdy byl požadavku obsloužených Azure Rights Management.

> [!IMPORTANT]
> V systému Azure Rights Management protokolování je optimalizovaný poskytnout protokoly rychle, spíše než v postupném pořadí strict. Pořadí objektů BLOB, jakož i pořadí záznamů protokolu v rámci objektu blob, může být mimo chronologickém pořadí. Pouze důvod, proč jsou postupně pojmenované blob je vám umožňují efektivně je chcete stáhnout přírůstkově.
> 
> Dva příklady možných výsledků pořadí protokolu:
> 
> -   Záznamy protokolu v objektu blob 000000004 může překrývat časovém pořadí záznamy protokolu v objektu blob 000000003. V extrémních případech všechny záznamy protokolu v objektu blob 000000004 mohl být vygenerován před všechny záznamy protokolu v objektu blob 000000003.
> -   Druhý záznam protokolu v objektu blob může objevovat před první záznam protokolu, ale byla zapsána do úložiště v obráceném pořadí.

Dříve, než analyzujete protokolů využití Azure Rights Management, doporučujeme stáhnout a naimportovat do úložiště, kde můžete seřadit podle jejich časové razítko protokoly protokolu. Další informace o stažení protokoly, naleznete v části [Přístup a použití protokolů využití Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs) v tomto tématu.

Protože protokoly nejsou nutně chronologickém, ale většina z nich jsou zapsány do 15 minut žádost, při identifikaci protokoly, které chcete pomocí jejich časové razítko, přidejte 15 minut na dobu, která vás zajímají. Pak si stáhněte tyto protokoly. Tato strategie by měl zajistí, že téměř všechny protokoly.

Jedna věc zapamatujte si je, že časové razítko na každý záznam protokolu je místního času služby Azure Rights Management, který zpracovat žádost. Protože Azure Rights Management spuštěna na více serverů napříč více datového centra, někdy protokoly může zdát, mimo pořadí, i když jsou seřazeny podle jejich časové razítko. Různých je ale malé a obvykle v rámci minutu. Ve většině případů to není problém, který by se jednat o problém pro analýzu protokolu.

### Formát objektu blob
Každý objekt blob je ve formátu rozšířené protokolu W3C. Začíná následující dva řádky:

**#Software: RMS**

**#Version: 1.1**

První řádek identifikuje, že jsou protokoly Azure Rights Management. Druhý řádek identifikuje, že zbytek objekt blob následuje specifikace verze 1.1. Doporučujeme vám, že všechny aplikace, které analyzovat tyto protokoly před pokračováním se analyzovat zbytek objekt blob ověřte tyto dva řádky.

Třetí řádek uvádí seznam názvů polí, které jsou odděleny tabulátory:

**#Fields: datum, čas id řádku typ požadavku id uživatele výsledek id korelace vlastníka obsahu id-e-mailu vystavitele id šablony název souboru publikovaná data c-informace o c-ip**

Každý z následujících řádků je záznam protokolu. Hodnoty polí jsou ve stejném pořadí jako v předchozím řádku a jsou odděleny tabulátory. Následující tabulku použijte k interpretovat pole.

|Název pole|W3C datový typ|Popis|Příklad hodnoty|
|--------------|------------------|---------|-------------------|
|Datum|Datum|Pokud byl doručen požadavek datum UTC.<br /><br />Zdroj je místní čas na serveru, který obsluhuje požadavek.|2013-06-25|
|čas|Čas|Čas UTC ve 24hodinovém formátu, pokud byl doručen požadavek.<br /><br />Zdroj je místní čas na serveru, který obsluhuje požadavek.|21:59:28|
|id řádku|Text|Jedinečný identifikátor GUID pro tento záznam protokolu.<br /><br />Tato hodnota je užitečné, když agregace protokoly nebo kopírování protokoly do jiného formátu.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|Typ požadavku|Název|Název rozhraní API služby RMS, který byl vyžádán.|AcquireLicense|
|id uživatele|Řetězec|Uživatel, který vytvořil požadavek.<br /><br />Hodnota není uzavřen v jednoduchých uvozovkách. Některé typy požadavků jsou anonymní přístup, v takovém případě je hodnota ".|"joe@contoso.com"|
|výsledek|Řetězec|Úspěch, pokud byl doručen požadavek úspěšné.<br /><br />Typ chyby do jednoduchých uvozovek, je-li požadavek se nezdařil.|'Úspěch'|
|id korelace|Text|Identifikátor GUID, která je společná mezi protokolu klienta služby RMS a server protokolu pro daný požadavek.<br /><br />Tato hodnota může být užitečné při řešení problémů s klientem.|cab52088-8925-4371-be34-4b71a3112356|
|id obsahu|Text|Identifikátor GUID uzavřeny ve složených závorkách, které identifikuje chráněný obsah (například dokument).<br /><br />Toto pole má hodnotu pouze v případě, že typ požadavku je AcquireLicense a je prázdný pro všechny ostatní typy požadavků.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|vlastník e-mailu|Řetězec|E-mailovou adresu vlastníka dokumentu.|Alice@contoso.com|
|vystavitele|Řetězec|E-mailovou adresu, která vystavitele dokumentu.|Alice@contoso.com (nebo) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com "|
|Id šablony|Řetězec|ID šablony použité k ochraně dokumentu.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|Název souboru|Řetězec|Název souboru dokumentu, který byl chráněn.|TopSecretDocument.docx|
|Datum vydání|Datum|Datum, kdy byl chráněn dokumentu.|2015-10-15T21:37:00|
|c-info|Řetězec|Informace o platformě klienta, který posílá požadavek.<br /><br />Konkrétní řetězec se liší v závislosti na aplikaci (například operačního systému nebo v prohlížeči).|"MSIPC; verze = 1.0.623.47; AppName = WINWORD. EXE; AppVersion = 15.0.4753.1000; AppArch = x 86; OSName = Windows; OSVersion = 6.1.7601; OSArch = amd64 "|
|c-ip|Adresa|IP adresa klienta, která vytvořila požadavek.|64.51.202.144|

#### Výjimky pro pole id uživatele
I když pole id uživatele obvykle označuje uživatele, který vytvořil požadavek, existují dvě výjimky kde hodnota nemapuje skutečné uživatele:

-   Hodnota **' microsoftrmsonline @&lt; YourTenantID &gt;. &lt; oblast &gt; rms.. aadrm.com'**.

    To znamená, že služby Office 365, jako je například Exchange Online nebo služby Sharepoint Online posílá požadavek. V řetězci *&lt; YourTenantID &gt;* je identifikátor GUID pro vašeho klienta a *&lt; oblast &gt;* je oblast, kde je váš klient zaregistrovaný. Například **na** představuje Severní Amerika **eu** představuje Evropě, a **ap** představuje Asii.

-   Pokud používáte konektor služby RMS.

    Požadavky z tohoto konektoru jsou protokolovány s hlavní název služby, které automaticky generuje RMS po nainstalování konektoru služby RMS.

#### Typy typických požadavků
Existuje mnoho typů žádosti pro Azure Rights Management, ale v následující tabulce jsou uvedeny některé typy nejvíce obvykle používané požadavků.

|Typ požadavku|Popis|
|-----------------|---------|
|AcquireLicense|z počítače se systémem Windows klient požaduje licenci pro RMS chráněný obsah.|
|AcquirePreLicense|klienta, jménem uživatele, žádá o licenci pro RMS chráněný obsah.|
|AcquireTemplates|bylo provedeno volání získá šablony založené na šabloně ID|
|AcquireTemplateInformation|bylo provedeno volání, chcete-li získat ID šablony ze služby.|
|AddTemplate|je provedeno volání z portálu Azure chcete přidat šablonu.|
|BECreateEndUserLicenseV1|je provedeno volání z mobilního zařízení k vytvoření licence koncového uživatele.|
|BEGetAllTemplatesV1|je provedeno volání z mobilního zařízení (back-end) Chcete-li získat všechny šablony.|
|Certifikovat|klienta je potvrzuje obsah pro ochranu.|
|Dešifrovat|Klient se pokouší k dešifrování obsahu chráněného službou RMS.|
|DeleteTemplateById|je provedeno volání z portálu Azure odstranit šablona šablony ID|
|ExportTemplateById|je provedeno volání z portálu Azure exportovat šablonu na základě šablony ID|
|FECreateEndUserLicenseV1|podobá AcquireLicense požadavek, ale z mobilních zařízení.|
|FECreatePublishingLicenseV1|stejné, jako je certifikovat a GetClientLicensorCert kombinovat od mobilních klientů.|
|FEGetAllTemplates|je provedeno volání, z mobilního zařízení (front-end) Chcete-li získat šablony.|
|GetAllTemplates|je provedeno volání z portálu Azure, chcete-li získat všechny šablony.|
|GetClientLicensorCert|Klient požaduje publikování certifikátu (která se později používá k ochraně obsahu) z počítače se systémem Windows.|
|Getconfiguration –|rutiny prostředí PowerShell Azure je volána k získání konfigurace klienta Azure RMS.|
|GetConnectorAuthorizations|je provedeno volání z konektorů RMS získat jejich konfiguraci z cloudu.|
|GetTenantFunctionalState|portál Azure kontroluje, zda je aktivován Azure RMS.|
|GetTemplateById|z portálu Azure k získání šablony zadáním ID šablony je provedeno volání|
|ExportTemplateById|je je provedeno volání z portálu Azure Export šablony zadáním ID šablony|
|FindServiceLocationsForUser|je provedeno volání se dotázat na adresy URL, který se používá k volání certifikovat nebo AcquireLicense.|
|ImportTemplate|je provedeno volání z portálu Azure Import šablony.|
|ServerCertify|je provedeno volání z klienta služby RMS povolen (například SharePoint) Chcete-li certifikovat serveru.|
|SetUsageLogFeatureState|je provedeno volání, chcete-li povolit protokolování využití.|
|SetUsageLogStorageAccount|je provedeno volání k určení umístění protokoly Azure RMS.|
|SignDigest|je provedeno volání, pokud klíč se používá pro podepsání účely. Jedná se obvykle jednou za AcquireLicence (nebo FECreateEndUserLicenseV1) certifikovat a GetClientLicensorCert (nebo FECreatePublishingLicenseV1).|
|UpdateTemplate|je provedeno volání z portálu Azure aktualizovat existující šablony.|

## <a name="BKMK_PowerShell"></a>Odkaz na prostředí Windows PowerShell
Pomocí následující rutiny prostředí Windows PowerShell můžete konfigurovat a používat protokolování využití Azure Rights Management:

-   [Zakázat AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Povolit AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Sada AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Další informace o použití prostředí Windows PowerShell pro Azure Rights Management naleznete v tématu [Správa Azure Rights Management pomocí prostředí Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Viz také
[Použití služby Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

