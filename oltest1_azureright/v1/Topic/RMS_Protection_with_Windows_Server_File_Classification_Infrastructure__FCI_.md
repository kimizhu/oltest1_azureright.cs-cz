---
description: na
keywords: na
title: RMS Protection with Windows Server File Classification Infrastructure (FCI)
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
---
# Ochrana RMS pomoc&#237; syst&#233;mu Windows Server soubor klasifikace infrastruktury (FCI)
Pomocí tohoto článku pokyny a skript použití klienta Rights Management (RMS) s nástrojem pro ochranu RMS ke konfiguraci Správce prostředků souborového serveru a soubor klasifikace infrastruktury (FCI).

Toto řešení umožňuje automaticky chránit všechny soubory ve složce na soubor serveru se systémem Windows Server, nebo automaticky chránit soubory, které splňují určitá kritéria. Můžete například soubory, které mají nebyl klasifikován jako obsahující důvěrné nebo citlivé informace. Toto řešení používá [Azure Rights Management](../Topic/Azure_Rights_Management.md) (Azure RMS) k ochraně souborů, takže musí mít tato technologie nasazen ve vaší organizaci.

> [!NOTE]
> I když obsahuje Azure RMS [konektor](https://technet.microsoft.com/library/dn375964.aspx) soubor podporuje infrastrukturu klasifikace, že řešení podporuje pouze nativní ochrana – například soubory sady Office.
> 
> Chcete-li podporují všechny typy souborů s infrastrukturou klasifikace souboru, je nutné použít prostředí Windows PowerShell **RMS ochrany** modulu, jak je uvedeno v tomto článku. Rutiny RMS ochrany, jako je aplikace pro sdílení obsahu RMS podporu obecný ochrany, jakož i nativní ochrany, což znamená, že všechny soubory může být chráněn. Další informace o těchto různých úrovní, naleznete v části [Úroveň ochrany – nativní a obecný](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) v oddílu [Průvodce Rights Management sdílení aplikace Správce](../Topic/Rights_Management_sharing_application_administrator_guide.md).

Postupujte podle pokynů jsou pro systém Windows Server 2012 R2 nebo Windows Server 2012. Pokud spustíte ostatní podporované verze systému Windows, můžete přizpůsobit některé z kroků pro rozdíly mezi verze operačního systému a popsaných v tomto článku.

## Předpoklady pro ochranu Azure RMS pomocí systému Windows Server FCI
Předpoklady pro následujících pokynů:

-   Na každém serveru souboru, kde bude spuštěna správce prostředků souborového s infrastruktury klasifikace souboru:

    -   Správce prostředků souborového serveru jste nainstalovali jako jedna ze služeb role pro roli Souborové služby.

    -   Určili jste do místní složky obsahující soubory k ochraně s Rights Management. Můžete například C:\FileShare.

    -   Byl nainstalován nástroj pro ochranu RMS, včetně předpoklady pro nástroj (například klienta služby RMS) a pro Azure RMS (například hlavní účet služby). Další informace naleznete v tématu [RMS ochrany rutiny](https://msdn.microsoft.com/library/azure/mt433195.aspx).

    -   Pokud chcete změnit výchozí úroveň ochrany RMS (nativní nebo obecný) pro konkrétní přípony názvů, jak je popsáno v jste upravili registru [soubor rozhraní API konfigurace](https://msdn.microsoft.com/library/dn197834%28v=vs.85%29.aspx) stránky.

    -   Máte připojení k Internetu, s nastavením nakonfigurovaný počítač v případě potřeby pro proxy server. Příklad: `netsh winhttp import proxy source=ie`

-   Jste nakonfigurovali další požadavky pro vaše nasazení Azure Rights Management, jak je popsáno v [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx). Konkrétně máte následující hodnoty pro připojení k Azure RMS pomocí hlavní název služby:

    -   BposTenantId

    -   AppPrincipalId

    -   Symetrický klíč

-   Vaše místní služby Active Directory uživatelských účtů mají synchronizovat se službou Azure Active Directory nebo Office 365, včetně jejich e-mailovou adresu. Toto je nezbytné pro všechny uživatele, které může být nutné získat přístup k souborům poté, co jsou chráněny FCI a Azure RMS. Pokud provedete tento krok (například v testovacím prostředí), mohou být blokovány uživatelům v přístupu k tyto soubory. Pokud potřebujete další informace o konfiguraci tohoto účtu, naleznete v části [Příprava na Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

-   Jste určili Rights Management šablonu, kterou chcete použít, který bude chránit soubory. Ujistěte se, že znáte ID pro tuto šablonu s použitím [Get-RMSTemplate](https://msdn.microsoft.com/library/azure/mt433197.aspx) rutiny.

## Pokyny ke konfiguraci FCI správce prostředků souborového serveru pro ochranu Azure RMS
Postupujte podle následujících pokynů automaticky chránit všechny soubory ve složce, s použitím skript prostředí Windows PowerShell jako vlastní úkol. Proveďte tyto postupy v tomto pořadí:

1.  Uložit skript prostředí Windows PowerShell

2.  Vytvoření vlastnosti klasifikace pro RMS (Rights Management)

3.  Vytvoření pravidla klasifikace (třídění pro službu RMS)

4.  Nastavení plánu klasifikace

5.  Vytvoření úlohy správy pro vlastní soubor (chránit soubory s RMS)

6.  Vyzkoušejte konfiguraci ručně spuštěním pravidlo a úloh

Na konci tyto pokyny všechny soubory ve vybrané složce budou klasifikován s vlastní vlastností služby RMS a tyto soubory bude potom chráněna Rights Management. Pro složitější nastavení, které chrání selektivní některé soubory a jiné ne můžete pak vytvořit nebo jinou klasifikaci vlastnosti a pravidla, pomocí úlohy správy souborů, které chrání pouze tyto soubory.

#### Uložit skript prostředí Windows PowerShell

1.  Rozbalit [Skript prostředí PowerShell systému Windows pro ochranu Azure RMS pomocí FCI správce prostředků souborového serveru](#BKMK_RMSProtection_Script) oddílu v tomto článku a zkopírovat jeho obsah. Umožňuje vložit obsah skript a zadejte název souboru **RMS-Protect-FCI.ps1** ve vašem počítači.

2.  Zkontrolujte skript a provést následující změny:

    -   Hledat následující libovolný řetězec, který jej nahradit vlastní AppPrincipalId, který můžete použít s [sady RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) rutiny pro připojení k Azure RMS:

        ```
        <enter your AppPrincipalId here>
        ```
        Můžete například skript může vypadat například takto:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)] [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Hledat následující libovolný řetězec, který jej nahradit vlastní symetrický klíč, který můžete použít s [sady RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) rutiny pro připojení k Azure RMS:

        ```
        <enter your key here>
        ```
        Můžete například skript může vypadat například takto:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Hledat následující libovolný řetězec, který jej nahradit vlastní BposTenantId (ID klienta), který můžete použít s [sady RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) rutiny pro připojení k Azure RMS:

        ```
        <enter your BposTenantId here>
        ```
        Můžete například skript může vypadat například takto:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

    -   Pokud váš server se systémem Windows Server 2012, bude pravděpodobně nutné ručně načíst modul RMSProtection na začátku skriptu. Přidejte následující příkaz (nebo ekvivalentní složky "Program Files" je na jednotce než C::

        ```
        Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"
        ```

3.  Přihlaste se skript. Pokud není uživatel skriptu (bezpečnější), je nutné nakonfigurovat prostředí Windows PowerShell na serverech, které jej spustit. Můžete například spustit relaci prostředí Windows PowerShell s **Spustit jako správce** a zadejte: **Set-ExecutionPolicy Unrestricted**. Tato konfigurace však umožní všechny nepodepsané skripty spustit (méně bezpečné).

    Další informace o podepisování skriptů prostředí Windows PowerShell, naleznete v části [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) v knihovně dokumentace nástroje prostředí PowerShell.

4.  Uložte soubor místně na každém serveru soubor, který bude spuštěn správce prostředků souborového s infrastrukturou klasifikace souboru. Můžete například uložit soubor do **C:\RMS-Protection**. Tento soubor Zabezpečte pomocí oprávnění systému souborů NTFS tak, aby neoprávněným uživatelům nelze jej upravovat.

Nyní jste připraveni začít konfigurace správce prostředků souborového serveru.

#### Vytvoření vlastnosti klasifikace pro RMS (Rights Management)

-   V správce prostředků souborového serveru, správu klasifikace, vytvořte novou místní vlastnost:

    -   **Name**: Typ **RMS**

    -   **Popis**:   Typ **Rights Management protection**

    -   **Typ vlastnosti**: Vyberte **Ano**

    -   **Value**: Vyberte **Ano**

Společnost Microsoft nyní můžete vytvořit pravidlo klasifikace, které používá tuto vlastnost.

#### Vytvoření pravidla klasifikace (třídění pro službu RMS)

-   Vytvořte nové pravidlo klasifikace:

    -   Na **Obecné** kartu:

        -   **Name**: Typ **Classify for RMS**

        -   **Povoleno**: Zachovat výchozí, což je, že toto políčko zaškrtnuto.

        -   **Popis**: Typ **Classify all files in the &lt;folder name&gt; folder for Rights Management**.

            Nahradit *&lt; název složky &gt;* s zvolený název složky. Můžete například **klasifikaci všechny soubory ve složce C:\FileShare pro službu Rights Management**

        -   **Scope**: Přidáte vybrané složky. Můžete například **C:\FileShare**.

            Nevybírejte zaškrtávacích políček.

    -   Na **klasifikace** kartu:

    -   **Metoda vyhodnocení**: Vyberte **třídění složek**

    -   **Vlastnost** název: Vyberte **RMS**

    -   Vlastnost **hodnotu**: Vyberte **Ano**

Přestože je klasifikační pravidla pro probíhající operace spustit ručně, bude toto pravidlo spouštět podle plánu tak, aby nové soubory budou klasifikován s vlastností služby RMS.

#### Nastavení plánu klasifikace

-   Na **automatická klasifikace** kartu:

    -   **Povolit pevný plán**: Zaškrtnutím tohoto políčka.

    -   Nastavení plánu pro všechna pravidla klasifikace ke spuštění, což zahrnuje naší nové pravidlo ke klasifikaci soubory s vlastností RMS.

    -   **Povolit průběžné klasifikaci pro nové soubory**: Zaškrtněte toto políčko, tak, že bude třeba zařadit nové soubory.

    -   Volitelné: Proveďte požadované změny, které potřebujete, jako je například konfigurace možnosti pro sestavy a oznámení.

Nyní jste dokončili konfiguraci klasifikace, budete připraveni ke konfiguraci úlohy správy, který má být použita pro soubory ochranu RMS.

#### Vytvoření úlohy správy pro vlastní soubor (chránit soubory s RMS)

-   V **úlohy správy souborů**, vytvoření nové úlohy správy souborů:

    -   Na **Obecné** kartu:

        -   **Název úlohy**: Typ **Protect files with RMS**

        -   Zachovat **Povolit** zaškrtávací políčko zaškrtnuto.

        -   **Popis**: Typ **Protect files in &lt;folder name&gt; with Rights Management and a template by using a Windows PowerShell script.**

            Nahradit *&lt; název složky &gt;* s zvolený název složky. Můžete například **Ochrana souborů ve C:\FileShare s Rights Management a šablonu pomocí skript prostředí Windows PowerShell**

        -   **Scope**: Vyberte do vybrané složky. Můžete například **C:\FileShare**.

            Nevybírejte zaškrtávacích políček.

    -   Na **Akce** kartu:

        -   **Type**: Vyberte **Vlastní**

        -   **Spustitelný soubor**: Zadejte následující:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Pokud systém Windows není na disku C:, upravit tuto cestu nebo přejděte k tomuto souboru.

        -   **Argument**: Zadejte následující, poskytnutím vlastní hodnoty pro &lt; cesta &gt; a &lt; ID šablony &gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Například pokud jste zkopírovali skriptu do C:\RMS-Protection a ID šablony, můžete zjistit z předpoklady je e6ee2481-26b9-45e5-b34a-f744eacd53b0, zadejte následující:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            V tomto příkazu **[cesta zdrojového souboru]** a **[zdrojový soubor vlastník e-mailu]** jsou oba konkrétní FCI proměnné, zadejte je proto, stejně jako se zobrazují v příkazu výše uvedené. První z nich je používán FCI automaticky určit identifikovaný soubor ve složce a druhá pro FCI se automaticky načíst e-mailová adresa pojmenované vlastníka identifikovaný soubor. Tento příkaz se opakuje u každého souboru ve složce, která je v našem případě každého souboru ve složce C:\FileShare, která má navíc RMS jako vlastnost klasifikace souboru.

            > [!NOTE]
            > **-OwnerMail [Source File Owner Email]** Parametr a hodnotu zajišťuje, že je původní vlastník souboru po je chráněn udělena Rights Management vlastníka souboru. To zajistí, že původní vlastník souboru mít všechna práva Rights Management na své vlastní soubory. Pokud soubory jsou vytvořeny pomocí uživatele domény, e-mailová adresa automaticky načíst ze služby Active Directory pomocí název uživatelského účtu ve vlastnosti vlastníka v souboru. Chcete-li to provést, souborového serveru musí být ve stejné doméně nebo důvěryhodné domény jako uživatel.
            > 
            > Pokud je to možné, přiřadíte původní vlastníci chráněné dokumenty, chcete-li zajistit, aby tito uživatelé i nadále mají plnou kontrolu nad soubory, které jsou vytvořeny. Nicméně pokud použijete proměnnou [zdrojový soubor vlastník e-mailu] jak je uvedeno výše a soubor nemá uživatel domény, který je definován jako vlastník (například místní účet byl použit k vytvoření souboru, takže vlastníka zobrazí systém), skript se nezdaří.
            > 
            > Pro soubory, které nemají žádný uživatel domény jako vlastník můžete zkopírovat a uložit tyto soubory sami jako uživatel domény, tak, aby stát vlastníkem pouze tyto soubory. Nebo pokud máte oprávnění, můžete ručně změnit vlastníka.  Případně můžete také můžete zadat konkrétní e-mailová adresa (například vlastní nebo adresa skupiny pro oddělení IT) místo proměnné [zdrojový soubor vlastník e-mailu], což znamená, že všechny soubory můžete chránit pomocí tohoto skriptu bude použít této e-mailovou adresu definovat nového vlastníka.

    -   **Spustit příkaz jako**: Vyberte **místního systému**

    -   Na **stavu** kartu:

        -   **Vlastnost**: Vyberte **RMS**

        -   **Operátor**: Vyberte **stejné**

        -   **Value**: Vyberte **Ano**

    -   Na **plán** kartu:

        -   **Run at**: Nakonfigurujte upřednostňované plánu.

            Poskytnout dostatek času na dokončení skriptu. Přestože je toto řešení chrání všechny soubory ve složce, bude skript spuštěn jednou pro každý soubor pokaždé, když. Ačkoli to trvá déle, než chrání všechny soubory v době, která podporuje nástroj RMS ochrany, je tento soubor po souboru konfigurace pro FCI výkonnější. Můžete například chráněné soubory mohou mít různé vlastníci (zachovat původní vlastník) když použijete proměnnou [zdrojový soubor vlastník e-mailu] a tato akce souboru soubor-li provést později změnit konfiguraci selektivní chránit soubory a nikoli všechny soubory ve složce.

        -   **Spouštět nepřetržitě na nové soubory**: Zaškrtnutím tohoto políčka.

#### Vyzkoušejte konfiguraci ručně spuštěním pravidlo a úloh

1.  Spuštění pravidla klasifikace:

    1.  Klikněte na tlačítko **pravidla klasifikace** &gt; **nyní spustit klasifikace se všechna pravidla**

    2.  Klikněte na tlačítko **Počkejte klasifikace k dokončení**, a potom klikněte na tlačítko **OK**.

2.  Počkejte **systémem klasifikace** dialogové okno zavřete a prohlédněte si výsledky v sestavě automaticky zobrazen. By se mělo objevit **1** pro **Vlastnosti** pole a počet souborů ve složce. Potvrďte použití Průzkumníku souboru a kontrolou vlastnosti souborů ve složce zvolený. Na **klasifikace** kartu, by se mělo objevit **RMS** jako název vlastnosti a **Ano** pro jeho **hodnotu**.

3.  Spusťte úlohu správy souborů:

    1.  Klikněte na tlačítko **úlohy správy souborů** &gt; **chránit soubory s RMS** &gt; **Spustit soubor Správa úloh nyní**

    2.  Klikněte na tlačítko **Počkejte na dokončení úlohy**, a potom klikněte na tlačítko **OK**.

4.  Počkejte **spuštěna úloha správy souborů** dialogové okno zavřete a prohlédněte si výsledky v sestavě automaticky zobrazen. Počet souborů, které jsou ve vybrané složce aplikace by se mělo objevit **soubory** pole. Potvrďte, že jsou soubory ve složce zvolený nyní chráněné službou RMS. Například pokud je zvolený složka C:\FileShare, v relaci prostředí Windows PowerShell zadejte následující příkaz a ověřte, zda žádné soubory mají stav **UnProtected**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Některé tipy:
    > 
    > -   Pokud vidíte **0** v sestavě, namísto počet souborů ve složce, to znamená, že skript nebyla spuštěna. Nejprve zkontrolujte samotného skriptu načtením v ISE v prostředí Windows PowerShell můžete ověřit obsah skriptu a pokuste se zjistit, zda jsou zobrazeny všechny chyby. Zadaný bez argumentů skript se pokusí připojit a ověřit nejen v Azure RMS.
    > 
    >     -   Pokud skript hlásí, že se nelze připojit k Azure RMS, zkontrolujte hodnoty, které zobrazuje pro hlavní účet služby, který jste zadali ve skriptu.  Další informace o tom, jak vytvořit tento hlavní účet služby, naleznete v tématu druhý požadovanou součást v [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)
    >     -   Pokud skript hlásí, že se nemohl připojit k Azure RMS a svou Azure oblast je mimo Severní Amerika, zkontrolujte, zda jste upravili registru správně pro tuto konfiguraci. Vhodný pro tento test je na serveru spustit přímo z prostředí Windows PowerShell Get-RMSTemplate. Další informace o úpravy registru, naleznete v části třetí požadovanou součást v [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx).
    > -   Pokud se skript sám o sobě běží ve Windows PowerShell ISE bez chyb, pokuste se spustit takto z relace prostředí PowerShell zadání názvu souboru k ochraně a bez parametru - OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File <full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Pokud bude skript spuštěn úspěšně v této relaci prostředí Windows PowerShell, zkontrolujte položky pro **Executive** a **Argument** v akci úloh správy souboru.  Pokud jste určili **- OwnerEmail [zdrojový soubor vlastník e-mailu]**, zkuste odebrat tento parametr.
    > 
    >         Je-li úloha správy souborů funguje úspěšně bez  **- OwnerEmail [zdrojový soubor vlastník e-mailu]**, zkontrolujte, zda nechráněné soubory jako uživatele domény, který je uveden jako vlastník souboru místo **systému**.  Chcete-li to provést, použijte **zabezpečení** kartu pro vlastnosti souboru a potom klikněte na tlačítko **Upřesnit**.**Vlastníka** hodnota je zobrazena bezprostředně po soubor **název**. Ověřte rovněž, zda je server souboru ve stejné doméně nebo důvěryhodné domény k vyhledání e-mailová adresa uživatele ze služby Active Directory Domain Services.
    > -   Pokud vidíte správný počet souborů v sestavě, ale nejsou chráněny soubory, zkuste ochranu soubory ručně pomocí [chránit RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx) rutiny, chcete-li zjistit, zda jsou zobrazeny všechny chyby.

Pokud ověříte, že tyto úlohy úspěšně spuštěna, můžete zavřít správce prostředků souborového. Nové soubory budou automaticky chráněna, a všechny soubory chráněné znovu, při spuštění plány. Znovu ochranu souborů zajišťuje, aby všechny změny do šablony jsou použity soubory.

### <a name="BKMK_RMSProtection_Script"></a>Skript prostředí PowerShell systému Windows pro ochranu Azure RMS pomocí FCI správce prostředků souborového serveru
Tento oddíl obsahuje ukázkový skript zkopírovat a upravit, jak je popsáno v předchozím oddílu.

*&#42;&#42;Zřeknutí se&#42;&#42;: Tento ukázkový skript není podporován v rámci jakékoli program standardní odborná pomoc společnosti Microsoft nebo služby. Tento ukázkový skript jsou poskytovány tak, jak je bez záruky jakéhokoli druhu.*

```
<# .SYNOPSIS Helper script to protect all file types with Azure RMS and FCI. .DESCRIPTION Protect files with Azure RMS and Windows Server FCI, using an RMS template ID. #> param( [Parameter(Mandatory = $false)] [ValidateScript({ If($_ -eq "") {$true} else { if (Test-Path -Path $_ -PathType Leaf) {$true} else {throw "Can't find file specified"} } })] [string]$File, [Parameter(Mandatory = $false)] [string]$TemplateID, [Parameter(Mandatory = $false)] [string]$OwnerMail, [Parameter(Mandatory = $false)] [string]$AppPrincipalId = "<enter your AppPrincipalId here>", [Parameter(Mandatory = $false)] [string]$SymmetricKey = "<enter your key here>", [Parameter(Mandatory = $false)] [string]$BposTenantId = "<enter your BposTenantId here>" ) # script information [String] $Script:Version = 'version 1.0' [String] $Script:Name = "RMS-Protect-FCI.ps1" #global working variables [switch] $Script:isScriptProcess = $False # Controls the script process. If false, the script gracefully stops running. #**Functions (general helper)*************************************** function Get-ScriptName(){ return $MyInvocation.ScriptName.Substring($MyInvocation.ScriptName.LastIndexOf('\') + 1, $MyInvocation.ScriptName.LastIndexOf('.') - $MyInvocation.ScriptName.LastIndexOf('\') - 1) } #**Functions (script specific)************************************** function Check-Module{ param ([String]$Module = $(Throw "Module name not specified")) [bool]$isResult = $False #try to load the module if (get-module -list -name $Module) { import-module $Module if (get-module -name $Module ) { $isResult = $True } else { $isResult = $False } } else { $isResult = $False } return $isResult } function Protect-File ($ffile, $ftemplateId, $fownermail) { [bool] $returnValue = $false try { If ($OwnerMail -eq $null -or $OwnerMail -eq "") { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId") } else { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId -OwnerEmail $fownermail $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId, set Owner: $fownermail") } } catch { Write-Host ( "ERROR" + "During protection of file: $ffile with Template: $ftemplateId") } return $returnValue } function Set-RMSConnection ($fappId, $fkey, $fbposId) { [bool] $returnValue = $false try { Set-RMSServerAuthentication -AppPrincipalId $fappId -Key $fkey -BposTenantId $fbposId Write-Host ("Information: " + "Connected to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") $returnValue = $true } catch { Write-Host ("ERROR" + "During connection to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") } return $returnValue } #**Main Script (Script)********************************************* Write-Host ("-== " + $Script:Name + " " + $Version + " ==-") $Script:isScriptProcess = $True # Validate Azure RMS connection by checking the module and then connection if ($Script:isScriptProcess) { if (Check-Module -Module RMSProtection){ $Script:isScriptProcess = $True } else { Write-Host ("The RMSProtection module is not loaded") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } if ($Script:isScriptProcess) { #Write-Host ("Try to connect to Azure RMS with AppId: $AppPrincipalId and BPOSID: $BposTenantId" ) if (Set-RMSConnection $AppPrincipalId $SymmetricKey $BposTenantId) { Write-Host ("Connected to Azure RMS") } else { Write-Host ("Couldn't connect to Azure RMS") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } #  Start working loop if ($Script:isScriptProcess) { if ( !(($File -eq $null) -or ($File -eq "")) ) { if (!(Protect-File -ffile $File -ftemplateId $TemplateID -fownermail $OwnerMail)) { $Script:isScriptProcess = $False } } } # Closing if (!$Script:isScriptProcess) { Write-Host "ERROR occurred during script process" -foregroundcolor "red" -backgroundcolor "black"} write-host ("-== " + $Script:Name + " " + $Version + "  ==-") if (!$Script:isScriptProcess) { exit(-1) } else {exit(0)}
```

## Úprava pokyny k ochraně selektivní souborů
Pokud máte předchozích pokynech práci, je pak velmi snadno upravit pro složitější konfigurace. Můžete například chránit soubory pomocí skriptu na stejné, ale pouze pro soubory, které obsahují identifikovatelných osobních údajů a případně vyberte šablonu, která má více omezující práva.

Chcete-li to provést, použijte jednu z vlastnosti integrované klasifikace (například **určitelné osobní údaje**), nebo vytvořte vlastní novou vlastnost. Vytvořte nové pravidlo, které používá tuto vlastnost. Například můžete vybrat možnost **obsahu třídění**, zvolte **určitelné osobní údaje** vlastnost s hodnotou **vysoké**, a nakonfigurujte vzor řetězec nebo výraz, který identifikuje soubor, který má být nakonfigurován pro tuto vlastnost (například řetězec "**datum narození**").

Nyní je třeba provést pouhé vytvořit nové úlohy správy souborů, který používá stejné skriptu ale možná s jinou šablonu a konfiguraci podmínky pro vlastnost klasifikace, který jste právě nakonfigurovali. Například namísto podmínku, že jsme nakonfigurována dříve (**RMS** vlastnost, **stejné**, **Ano**), vyberte možnost **určitelné osobní údaje** vlastnost s **operátor** nastavena na hodnotu **stejné** a **hodnotu** z **vysoké**.

