---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# Aktivace Azure Rights Management
Pokud je aktivováno [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), může vaše organizace začít chránit důležitá data pomocí aplikace a služby, které podporují toto řešení ochrany informací. Správci mohou také sledovat a spravovat chráněné soubory a e-mailů, které vaše organizace vlastní. Je nutné povolit [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] předtím, než můžete začít používat funkce informace práva IRM (Správa) v rámci sady Office, SharePoint a serveru Exchange a chránit libovolného citlivá nebo důvěrná souboru.

Pokud chcete získat další informace o Azure Rights Management před aktivací služby – například jaké obchodních problémů ji byl odstraněn, některé typické použití případy a jak funguje – naleznete v části [Co je Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

> [!IMPORTANT]
> Před aktivací [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], ujistěte se, že má vaše organizace plán služby, která zahrnuje [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] služby. V opačném případě nebude možné aktivovat Azure RMS.
> 
> Další informace naleznete v tématu [Cloud odběry, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) v oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu.

Po aktivaci Azure RMS, všichni uživatelé ve vaší organizaci můžete použít ochrana informací ke svým souborům a všichni uživatelé mohli otevřít (spotřebovávat) soubory chráněné službou Azure RMS. Nicméně pokud dáváte přednost, můžete omezit ochrana informací, který můžete použít s využitím registrace ovládacích prvků dvoufázové nasazení. Další informace naleznete v tématu [Registrace ovládacích prvků pro dvoufázové nasazení konfigurace](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) v tomto tématu.

## Aktivaci služby Rights Management
Použijte jednu z následujících postupů k aktivaci [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

> [!TIP]
> Můžete také použít rutiny prostředí Windows PowerShell, [Povolit službou Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx), chcete-li aktivovat [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Chcete-li aktivovat službu Rights Management z centra pro správu služeb Office 365

1.  Poté, co jste se přihlásili pro Office 365 plán, který obsahuje Rights Management [přihlásit k odběru Office 365 pomocí pracovní nebo školní účet](https://portal.office.com/) který je správcem nasazení služeb Office 365.

2.  Pokud nejsou Centru správy Office 365 automaticky zobrazeny, vyberte ikonu Spouštěč aplikace v levém horním a zvolte **Admin**.**Admin** dlaždice se zobrazí pouze pro správce služeb Office 365.

    > [!TIP]
    > Nápovědu admin center najdete v tématu [centra pro správu Office 365 - správce nápovědy](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  V levém podokně rozbalte položku **Nastavení služby**.

4.  Klikněte na tlačítko **Rights Management**.

    > [!NOTE]
    > Pokud tuto možnost nevidíte, může být vzhledem k tomu, že služba plán nebo produktu verze nepodporuje Rights Management, nebo ještě nebyla upgradována na podporu Rights Management.
    > 
    > Pomocí informací v [Cloud odběry, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) v oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu potvrďte podpory. Pokud je podporována verze aktualizace service plán nebo produktu, ale nevidíte možnost Rights Management, může být vzhledem k tomu, že služba ještě není upgradována. Nápovědu k tomuto problému, odeslat e-mailovou zprávu na [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).

5.  Na **RIGHTS MANAGEMENT** klikněte na tlačítko **Spravovat**.

6.  Na **služby rights management** klikněte na tlačítko **Aktivovat**.

7.  Po zobrazení výzvy **Chcete aktivovat službu Rights Management?**, klikněte na tlačítko **Aktivovat**.

Nyní byste měli vidět **Rights management je aktivována** a deaktivovat.

#### Chcete-li aktivovat službu Rights Management z portálu Azure klasické

1.  Poté, co jste se přihlásili k účtu Azure [přihlásit na portál Azure klasické](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  V levém podokně klikněte na tlačítko **služby ACTIVE DIRECTORY**.

3.  Z **služby active directory** klikněte na tlačítko **RIGHTS MANAGEMENT**.

4.  Vyberte adresář pro správu pro [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], klikněte na tlačítko **Aktivovat**, a pak akci potvrďte.

    > [!NOTE]
    > Pokud se zobrazí chyba aktivace, může to být způsobeno verze aktualizace plánu nebo produktu service nemůže podporovat [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].
    > 
    > Pomocí informací v [Cloud odběry, které podporují službu Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) v oddílu [Požadavky pro Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tématu potvrďte podpora služby RMS. Nápovědu k tomuto problému, odeslat e-mailovou zprávu na [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

**Stav správy práv** by nyní měl zobrazovat **Active** a **Aktivovat** je nahrazena možnost **DEAKTIVUJTE**.

### Hodnoty stavu Rights Management a popisy klasické portálu Azure
Kromě **Active** stav, který označuje, že je povolena služba Rights Management a připravené k použití, může také dojít **neaktivní**, **není k dispozici**, nebo **Neautorizováno**.

|Hodnota stavu|Popis|
|-----------------|---------|
|**Aktivní**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] je povolen a připravena k použití.|
|**Neaktivní**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] je zakázáno a musí být aktivováno, než vaše organizace může chránit soubory.|
|**Není k dispozici**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] Služba není spuštěna. Opakujte akci později.|
|**Neoprávněný přístup**|Nemáte oprávnění k zobrazení stavu [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] služby. Například je váš účet uzamčen nebo nejste globální správce pro vybraného klienta.|

## <a name="BKMK_OnboardingControls"></a>Registrace ovládacích prvků pro dvoufázové nasazení konfigurace
Pokud nechcete, aby všichni uživatelé byli schopni okamžitě chránit soubory pomocí Azure RMS, můžete nastavit uživatelské ovládací prvky registrace pomocí [Set AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) příkaz prostředí Windows PowerShell. Tento příkaz lze spustit před nebo po aktivaci Azure RMS.

> [!IMPORTANT]
> Tento příkaz lze použít, pokud nemáte alespoň verze **2.1.0.0** z [modul prostředí Windows PowerShell Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Chcete-li zkontrolovat, verze, kterou jste nainstalovali, spusťte: **(Get-Module aadrm –ListAvailable).Version**

Například pokud budete moci chránit obsah pro účely testování původně chcete pouze správci ve skupině "IT oddělení" (který má ID objektu fbb99ded-32a0-45f1-b038-38b519009503), použijte následující příkaz:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Všimněte si, že pro tuto možnost konfigurace, je nutné zadat skupinu; Nelze zadat jednotlivých uživatelů.

Nebo pokud chcete zajistit, že pouze uživatelé, kteří jsou správně licenci k používání Azure RMS můžete chránit obsah:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Použijete-li tyto ovládací prvky registrace, všichni uživatelé v organizaci může spotřebovat vždy chráněný obsah, který je chráněn podsadu uživatelů, ale nebudou moci použít informace ochrany sami z klientské aplikace. Například neuvidí v jejich klienti Office výchozí šablony, které jsou publikovány automaticky, když je aktivován Azure RMS, nebo vlastní šablony, které můžete konfigurovat.  Serverové aplikace, například server Exchange, můžete implementovat vlastní za uživatelské ovládací prvky pro integraci služby RMS k dosažení stejného výsledku.

## Další kroky
Teď, když jste aktivovali [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] pro vaši organizaci používat [Plán nasazení Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) Zkontrolovat, zda jsou ostatní kroky konfigurace, které mohou vyžadovat před můžete přejít na [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] uživatelům a správcům. Například můžete chtít použít [vlastní šablony](http://technet.microsoft.com/library/dn642472.aspx) usnadnit uživatelům platí ochrana informací soubory, připojit místní servery používat [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] nainstalováním [RMS konektor](http://technet.microsoft.com/library/dn375964.aspx), a nasadit [aplikace pro sdílení obsahu Rights Management](http://technet.microsoft.com/library/jj585031.aspx) který podporuje chrání všechny typy souborů na všech zařízeních. Služby Office, jako například Exchange Online a SharePoint Online vyžadovat další konfiguraci před použitím jejich funkce Správa informačních práv (IRM). Nicméně pokud neexistují žádné další konfigurační kroky, budete muset, naleznete v části [Použití služby Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) provozní pokyny pro podporu úspěšné nasazení pro vaši organizaci.

Informace o možnosti vašich aplikací pro práci s [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], naleznete v části [Jak aplikace podporují Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

## Viz také
[Konfigurace Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

