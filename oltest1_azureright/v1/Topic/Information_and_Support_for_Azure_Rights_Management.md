---
description: na
keywords: na
title: Information and Support for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7cc73d92-27d6-49ff-a8ab-2fae73519b4b
---
# Informace a podpora n&#225;stroje Azure Rights Management
Použít následující prostředky pro další informace o aplikaci Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

|Chcete-li to provést...|.. postupujte takto:|
|---------------------------|------------------------|
|… Přečtěte si nejaktuálnější [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] → dokumentaci produktu|Použijte dokumentaci v knihovně TechNet  [Azure Rights Management](../Topic/Azure_Rights_Management.md)|
|… názor na dokumentaci nebo položit otázku o → dokumentace|E-mailu [askipteam](mailto:%20askipteam@microsoft.com?subject=Documentation%20feedback)|
|… přijímat tweety o Rights Management a oznámení o aktualizacích dokumentace z → skupiny produktů|Postupujte podle Plastina daň, která pomáhá vést týmů ve společnosti Microsoft Rights Management. Podívejte se na téma [daň Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy)|
|… Získejte zkušební verzi aplikace [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] →|[Zaregistrujte se zdarma 30denní zkušební verze](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)|
V následujících částech Další informace o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]:

-   [Hledání v knihovně dokumentace](../Topic/Information_and_Support_for_Azure_Rights_Management.md#BKMK_SearchTips)

-   [Dokumentace ke stažení](../Topic/Information_and_Support_for_Azure_Rights_Management.md#BKMK_Download)

-   [Blog skupiny pro produkt Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md#BKMK_ProductGroupBlog)

-   [Možnosti podpory a materiály z komunity](../Topic/Information_and_Support_for_Azure_Rights_Management.md#BKMK_SupportOptions)

## <a name="BKMK_SearchTips"></a>Hledání v knihovně dokumentace
[Pomocí tohoto dotazu cílené vyhledání](http://www.bing.com/search?q=%28"Rights%20Management"%29%20site:technet.microsoft.com/library%20meta:search.MSCategory%28jj619159%29) lze vyhledat dokumentaci v knihovně TechNet, který je zaměřená na [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] pouze.

Výsledky hledání pro tento dotaz nezahrnují výsledky o službě Active Directory Rights Management Services (AD RMS) nebo Windows Rights Management nebo materiály z komunity. Můžete zúžit výsledky hledání dále nahradí řetězec "Rights Management," v adrese URL s hledanému řetězci.

### Příklad vyhledávání
[Pomocí tohoto dotazu vyhledávání](http://www.bing.com/search?q=%28"Rights%20Management"%29%20site:technet.microsoft.com/library%20meta:search.MSCategory%28jj619159%29) a poté si můžete upravit hledání pomocí následující příklady.

-   Jeden hledaný řetězec: Chcete-li hledat témata, které obsahují hledaný řetězec **konektor služby RMS**, nahradit **“Rights Management”** s **“RMS connector”**:

    ```
    ("RMS connector") site:technet.microsoft.com/library meta:search.MSCategory(jj619159)
    ```

-   Kombinování vyhledávací řetězce: Chcete-li hledat témata, které obsahují vyhledávací řetězce **Exchange** a **SharePoint**, použít **AND** operátor:

    ```
    ("Exchange") AND ("SharePoint") site:technet.microsoft.com/library meta:search.MSCategory(jj619159)
    ```

-   Alternativní vyhledávací řetězce: Chcete-li hledat témata, které obsahují hledaný řetězec **Exchange** nebo **SharePoint**, použít **OR** operátor:

    ```
    ("Exchange" OR "SharePoint") site:technet.microsoft.com/library meta:search.MSCategory(jj619159)
    ```

-   Vylučte vyhledávací řetězce: Chcete-li hledat témata, které obsahují hledaný řetězec **Exchange** a vyloučení témata o **SharePoint**, použít **NOT** operátor:

    ```
    ("Exchange)" NOT ("SharePoint") site:technet.microsoft.com/library meta:search.MSCategory(jj619159)
    ```

### Tipy pro vyhledávání
Aby vám pomohl najít informace, které je nutné použijte následující tipy pro vyhledávání:

-   Při hledání pro oficiální dokumentaci, použijte hledané výrazy, které odpovídají těch, které se zobrazí v uživatelském rozhraní (UI) a dokumentace TechNet, nikoli neoficiální termíny nebo zkratky, které mohou se zobrazit v obsahu vytvořeného komunitou. Můžete například hledat "Azure Rights Management" a "AADRMS" nebo jiné neoficiální zkratky pro tuto službu cloudu. Ačkoli může často poslechněte si a podívejte se na téma "RMS", úplný název je služba Rights Management, vyzkoušejte proto hledání "rights management" a RMS v případě, že hledáte oficiální dokumentaci. Můžete použít [Terminologie Azure Rights Management](../Topic/Terminology_for_Azure_Rights_Management.md) k identifikaci oficiální podmínky, které jsou specifické pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

-   Při vyhledávání stránky na webu TechNet (stiskněte klávesy Ctrl + F a zadejte hledané výrazy v **Najít** pole), text, který je v částech sbaleného vyloučit výsledky. K vyhledání textu v částech sbalené, rozbalte v částech před Hledat stránky. Chcete-li to provést, klepněte **Rozbalit vše** tlačítko v horní části stránky, nebo poklepejte na libovolné sbaleného části. Pokud jsou všechny oddíly rozbaleny, vyhledávání stránky prohledá všechny oddíly na této stránce.

-   Kdykoli je to možné, použijte dokumentaci online, nikoli stažené knihovna TechNet. Online v knihovně TechNet obsahuje nejnovější informace a informace, které chcete vyhledat nemusí být v stažené dokumentaci nebo může být oprav nebo Další informace naleznete online.

-   Pokud zjistíte, je jednodušší a rychlejší vyhledávání dokumentace, když je uložena místně, můžete vybrat více témat na webu TechNet a uložit místně. Další informace naleznete v části Další.

## <a name="BKMK_Download"></a>Dokumentace ke stažení
Můžete stáhnout stránek na webu TechNet a uložit místně – například je uložit do souboru PDF ke čtení na přenosné počítače, tablety nebo telefon, pokud nemáte připojení k Internetu. Můžete také anotaci sami a vytisknout informace. Při použití této metody můžete efektivně vytvořit vlastní dokumenty white paper nebo dokumentace k projektům podle seskupování témata, která je nutné pro konkrétní nastavit úlohy, případně scénáři začátku do konce.

Tuto metodu lze použít pro všechny knihovny dokumentace na webu TechNet, nikoli pouze [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

#### Chcete-li stáhnout dokumenty na webu TechNet:

1.  Přihlaste se k webu TechNet.

2.  Horní části stránky, který chcete uložit místně, klikněte na tlačítko **Exportovat** (vedle **Tisk**).

    Zobrazí se **Export více sad stránek** hlavičky, která umožňuje přidávat a odebírat stránky, které chcete uložit.

3.  Klikněte na tlačítko **Spravovat stránky** exportovat je.

Další informace získáte kliknutím na tlačítko **pomoci** do hlavičky.

> [!NOTE]
> Informace na webu TechNet jsou pravidelně aktualizovány, proto použít online verzi vždy, když je možné zajistit, abyste měli nejnovější informace.
> 
> Měsíční hlášení dokumentaci můžete používat na [Blog týmu Microsoft Rights Management (RMS) a dokumentace značkou](http://blogs.technet.com/b/rms/archive/tags/docs/) ke kontrole zda témata, které jste dříve stáhli pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] jsou nyní upravit, a jaké změny byly provedeny.

## <a name="BKMK_ProductGroupBlog"></a>Blog skupiny pro produkt Rights Management
Skupina produktů Rights Management používá [Blog týmu Microsoft Rights Management (RMS)](http://blogs.technet.com/b/rms/) k poskytování technických informací a dalších novinek o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], služby AD RMS a související technologie. Tyto příspěvky blogu doplňují informace o dokumentaci a podpory produktu.

> [!TIP]
> Pokud při vývoji aplikací pro Azure RMS nebo služby AD RMS, bude také pravděpodobně zájem [Active Directory Rights Management Services (AD RMS) Developer rohu blogu](http://blogs.msdn.com/b/rms/).

## <a name="BKMK_SupportOptions"></a>Možnosti podpory a materiály z komunity
Následující odkazy poskytují informace o podpoře a Poradce při potížích s možností a materiály z komunity:

-   [Nástroj RMS Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=46437)

-   [Yammer: Microsoft Rights Management (RMS)](http://www.yammer.com/AskIPTeam)

-   [Fóra: Aplikace Microsoft RMS (cloudu)](https://social.technet.microsoft.com/Forums/en-US/home?forum=rmscloud)

-   [Fóra: RMS pro uživatele (aplikace)](https://social.technet.microsoft.com/Forums/en-US/home?forum=rmsapps)

-   [Společnost Microsoft Nápověda a odborná pomoc](http://go.microsoft.com/fwlink/?LinkId=243064)

Kromě toho naleznete [Microsoft Rights Management services portál](http://www.microsoft.com/rms) najít další doprovodné materiály pro [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

## Viz také
[Začínáme s Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

