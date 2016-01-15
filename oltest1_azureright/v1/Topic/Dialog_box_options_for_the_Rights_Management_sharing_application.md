---
description: na
keywords: na
title: Dialog box options for the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
---
# Možnosti dialogov&#233;ho okna pro službu Rights Management, aplikace pro sd&#237;len&#237;
Pomocí těchto informací můžete zadat možnosti v aplikaci sdílení RMS **Přidat ochranu** dialogové okno nebo **sdílet chráněné** dialogového okna. Zobrazí se dialogové okno když vám [chránit soubor sdílet](http://technet.microsoft.com/library/dn574735.aspx) nebo [chránit soubor na místě](http://technet.microsoft.com/library/dn574733.aspx) a zvolte vlastní oprávnění.

> [!IMPORTANT]
> Pokud se liší od nastavení zde uvedeny možnosti, které vidíte, pravděpodobně nemáte nejnovější verzi sdílení aplikace nainstalována. Můžete stáhnout nejnovější verzi z [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) stránky.
> 
> Jak víte, pokud máte k dispozici nejnovější verzi? Vyhledat **Microsoft Rights Management aplikace pro sdílení** uvedených v části programy a funkce a zkontrolujte odpovídající číslo verze. Chcete-li zobrazit a pomocí možností v tabulce, verze by měla být nejméně **1.0.1770.0**. Můžete zkontrolovat na stránce stažení nejnovější číslo verze.

Kromě možnosti, které můžete použít vám může také vás zajímá:

-   [Co je .ppdf soubor, který se automaticky vytvoří?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)

-   [Jaký je rozdíl mezi obecný ochrany a integrované ochrany (nativní)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative)

|Možnost|Popis|
|-----------|---------|
|**UŽIVATELÉ**|Pokud jste již nezadali e-mailovou adresu z aplikace Outlook, zadejte e-mailové adresy uživatelů, který chcete otevřít soubor.<br /><br />Pokud vaše organizace používá místní verze Rights Management (AD RMS), jsou e-mailové adresy, které můžete určit omezen na uživatele v rámci vaší organizace. Pokud to se týká, a můžete se pokusit určit externí e-mailové adresy, zobrazí se zpráva, že konfigurace vaší společnosti, které umožňuje sdílení chráněný obsah pouze v rámci společnosti. Nicméně pokud vaše organizace používá Azure RMS, tyto e-mailové adresy může být pro osoby v rámci vaší organizace nebo pro osoby v jiné organizaci.<br /><br />Příklad: janetm@contoso.com; p.Dover@Fabrikam.com|
|**Obecný ochrany**|Pokud je vybrána tato možnost, znamená to, že vybraný soubor nelze chránit nativně. Další informace naleznete v tématu. [Jaký je rozdíl mezi obecný ochrany a integrované ochrany (nativní)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative) v tomto tématu.|
|**Prohlížeč – pouze zobrazení**<br /><br />**Kontrolor – zobrazení a úprava**<br /><br />**Vytváření – zobrazení, úpravy, kopírování a tisk**<br /><br />**Vedlejšího vlastníka – všechna oprávnění** **Note:** Všechny tyto možnosti mají odezvy ikonu před název, které představují celém světě světa. Tato ikona je použít, protože obvykle vyberete jednu z těchto možností při odesílání přílohy někdo v jiné organizaci.|Pokud chcete definovat práva pro chráněný dokument, vyberte jednu z těchto možností. Každá možnost zobrazení popisu.<br /><br />Když vyberete některou z těchto možností, pouze uživatelé určíte v **Uživatelé** nemá oprávnění zadáte k otevření a použití dokumentu. Například pokud předávají na jiný uživatel si dokument nebude otevřen.|
|Zásady šablony, které nakonfiguruje správce.<br /><br />Pokud například název společnosti je Contoso, Ltd: **Contoso, Ltd - pouze důvěrné zobrazení** **Note:** Všechny tyto možnosti mít Čtvereček ikonu před název, který představuje kancelářské budovy. Tato ikona se používá, protože obvykle vyberete jednu z těchto možností při odesílání přílohy někdo ve vaší organizaci.|Při sdílení dokumentu s uživateli, kteří budou pracovat pro vaši organizaci, se zobrazí šablony k dispozici zásady, které nakonfiguruje správce. Vyberte jednu z těchto při dokumentu nesmí být sdílen mimo vaši organizaci.<br /><br />Když vyberete některou z těchto možností, Správce definuje oprávnění pro dokument a ho otevřít.|
|**Tyto dokumenty vyprší**|Vyberte tuto možnost pouze pro náročné na čas soubory, které by neměl být možné otevřít po datu, který zadáte uživatele, které jste vybrali. Stále moci otevřít původní soubor, ale po půlnoc (aktuální časové pásmo), který zadáte, ostatním uživatelům nebude možné k otevření souboru.<br /><br />Tato možnost není k dispozici, pokud vyberete šablonu zásad, který konfiguruje správce.|
|**Zaslat mi e-mail, když někdo pokusí otevřít tyto dokumenty**|**Note:** Tato možnost je aktuálně v náhledu.<br />Vyberte tuto možnost, pokud chcete přijímat oznámení vždy, když někdo pokusí otevřít dokument, který jste ochranu. E-mailové zprávy je uvedeno, který byl proveden pokus o otevření, kdy a zda byly úspěšné.<br /><br />Tato možnost je k dispozici pouze v případě, že vaše organizace používá Azure RMS. Pokud vaše organizace používá místní verze Rights Management (AD RMS), neuvidíte tuto možnost.|
|**Umožnit okamžitě odebrat přístup ke tyto dokumenty**|Tuto možnost zvolte, pokud bude pravděpodobně nutné odebrat přístup ke dokumenty později pomocí dokumentu sledování webu, a je třeba odvolání okamžitě vstoupila v platnost. Však nastavení tato možnost znamená, zatímco dokument nebyl odvolán, uživateli vždy je nutné připojení k Internetu ke čtení dokumentu, pokaždé, když jsou k němu přístup. Mohou existovat některé scénáře uživatelů jejich zařízení nelze připojit k Internetu, kde uživatelé nelze přečíst váš dokument, jako je určen.<br /><br />Pokud se rozhodnete není tato možnost, můžete stále odvolat dokumenty později, s použitím webu sledování dokumentu. Nicméně vzhledem k tomu, že uživatelé vždy nemusí připojení k Internetu ke čtení dokumentu, nebude znají okamžitě že dokument je odvolán a mohou i nadále ji přečíst, dokud nebude dále ověřování s Azure RMS. Ve výchozím nastavení je maximální počet dní, které uživatel si může pokračovat ve čtení chráněný dokument, který jste odvolán 30 dnů, ale správce může změnit tuto hodnotu na méně nebo vyšší než 30 dní.<br /><br />Tato možnost je k dispozici pouze v případě, že vaše organizace používá Azure RMS. Pokud vaše organizace používá místní verze Rights Management (AD RMS), neuvidíte tuto možnost.|

## <a name="BKMK_GenericNative"></a>Jaký je rozdíl mezi obecný ochrany a integrované ochrany (nativní)?

-   Když je **ke generické chybě chránit soubor**, neoprávněným uživatelům nelze otevřít soubor. Však po oprávněným uživatelům otevřít soubor, může pak předá nechráněné ostatním uživatelům nebo ho uložit do umístění, které by mohly přístup ostatním uživatelům. V takovém případě však zobrazí zprávu, že jejich oprávnění, která mají pro soubor, a dotázáni, přijmout tyto, ale tato ochrana nelze vynutit. Kromě toho při uzamčení ke generické chybě souboru, nemohou omezit oprávnění dále než autorizace. Například nemohou omezit obsah na jen pro čtení nebo nejsou vytištěny.:

    > [!NOTE]
    > Obecně chráněný soubor má vždy příponu názvu souboru **.pfile**.

-   Ve srovnání s při použití **integrované (nativní) ochrany** obsahu Rights Management s aplikacemi, které to podporují (například soubory sady Office), ochrana se vztahuje k souboru i v případě, že soubor odeslán do někdo jiný nebo uložené v jiném umístění. A pokud jste ochranu tyto soubory, můžete použít omezující oprávnění jako jen pro čtení, nebo oprávnění k úpravám, ale nelze vytisknout nebo zkopírovat. Například byste mohli vybrat **Viewer – zobrazení pouze**, tak, aby obsahu nelze upravovat, tisku nebo kopírování.

Další technické informace naleznete v tématu [Úroveň ochrany – nativní a obecný](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) v oddílu [Průvodce Rights Management sdílení aplikace Správce](../Topic/Rights_Management_sharing_application_administrator_guide.md).

## <a name="BKMK_PPDF"></a>Co je .ppdf soubor, který se automaticky vytvoří?

-   Při sdílení chráněných souborů e-mailem (sdílet chráněné), vytvoří automaticky aplikace pro sdílení obsahu RMS **.ppdf** verzi souboru pro aplikaci Word, Excel, PowerPoint nebo ve formátu PDF. Toto je jen pro čtení chráněné verze souboru, který lze otevřít pouze autorizované osoby a zajišťuje příjemců může číst vždy přílohu, i když používají mobilního zařízení, které není zaškrtnuta možnost aplikace s nativní podporou Rights Management. Poskytující tyto osoby mít nainstalována aplikace pro sdílení obsahu RMS, bude moci číst přílohu.

    V této situaci, na rozdíl od ke generické chybě chráněný soubor bude vynuceno omezení použití. Příjemce nebude možné uložit tuto verzi souboru a je-li předávají na jiný uživatel si přílohu, zůstávají původní omezení s dokumentu. Pouze uživatelé, které byly povoleny pro chráněný dokument bude možné ho otevřít.

    > [!NOTE]
    > Pokud sdílet chráněné (sdílení e-mailem), ale není vytvořen při ochraně na místě, se automaticky vytvoří soubor .ppdf.

## Příklady a další informace
Příklady pro jak je možné použít Rights Management, sdílení aplikací a návody, naleznete v následujících částech v uživatelské příručce sdílení aplikace Rights Management:

-   [Příklady použití aplikace pro sdílení obsahu RMS](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Co chcete provést?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Viz také
[Průvodce Rights Management sdílení aplikace uživatele](../Topic/Rights_Management_sharing_application_user_guide.md)

