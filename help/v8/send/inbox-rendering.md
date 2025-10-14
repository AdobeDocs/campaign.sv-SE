---
product: campaign
title: Inkorgsåtergivning i Campaign
description: Lär dig hur du hämtar e-poståtergivningar och gör dem tillgängliga i en dedikerad rapport
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
version: Campaign v8, Campaign Classic v7
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: 96f1518f252be7ffa27ba8157b8a090bf4d4510d
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 8%

---

# Inkorgsåtergivning{#inbox-rendering}

## Om inkorgsåtergivning {#about-inbox-rendering}

Innan du klickar på knappen **Skicka** måste du se till att ditt meddelande visas för mottagarna på ett optimalt sätt på en mängd olika webbklienter, e-postmeddelanden och enheter.

Adobe Campaign utnyttjar den webbaserade e-posttestningslösningen [Litmus](https://litmus.com/email-testing){target="_blank"} för att hämta återgivningarna och göra dem tillgängliga i en dedikerad rapport. På så sätt kan du förhandsgranska det skickade meddelandet i olika sammanhang som det kan tas emot i och kontrollera kompatibiliteten i de flesta datorer och program.

>[!CAUTION]
>Inkorgsåtergivning är inte kompatibelt med [återkommande leveranser](../../automation/workflow/recurring-delivery.md).

Litmus är en funktionell e-postvalidering och förhandsgranskning av program. Med den kan e-postskapare förhandsgranska sitt meddelandeinnehåll i över 70 e-postrenderare, till exempel Gmail-inkorgen eller Apple Mail-klienten.

De mobil-, meddelande- och webbpostklienter som är tillgängliga för **Inkorgsåtergivning** i Adobe Campaign finns listade på [Litmus-webbplatsen](https://litmus.com/email-testing){target="_blank"} (klicka på **Visa alla e-postklienter**).

>[!NOTE]
>
>Återgivning av inkorgen behövs inte för att testa personalisering i leveranser. Personalization kan kontrolleras med Adobe Campaign-verktyg som **[!UICONTROL Preview]** och [korrektur](preview-and-proof.md#send-proofs).

## Om Litmus-tokens {#about-litmus-tokens}

Eftersom Litmus är en tredjepartstjänst fungerar den på en kreditmodell per användning. Varje gång en användare anropar Litmus-funktionen dras krediten av.

I Adobe Campaign motsvarar krediten antalet tillgängliga återgivningar (kallas tokens).

>[!NOTE]
>
>Antalet tillgängliga Litmus-tokens beror på vilken Campaign-licens du har köpt. Kontrollera licensavtalet.

Varje gång du använder funktionen **[!UICONTROL Inbox rendering]** i en leverans minskar varje återgivning dina tillgängliga token med ett.

>[!IMPORTANT]
>
>Tokens-konto för varje enskild återgivning och inte för hela inkorgsåtergivningsrapporten, vilket innebär att:
>
>* Varje gång rapporten för inkorgsåtergivning skapas dras en token per meddelandeklient av: en token för Outlook 2000-återgivning, en för Outlook 2010-återgivning, en för Apple Mail 9-återgivning och så vidare.
>* Om du genererar återgivningen av Inkorgen igen för samma leverans minskas antalet tillgängliga tokens igen med antalet genererade återgivningar.
>

Antalet återstående tillgängliga token visas i [Återgivningsrapporten för inkorgen](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

Återgivningsfunktionen i Inkorgen används vanligtvis för att testa HTML-ramverket i ett nyligen utformat e-postmeddelande. Varje återgivning kräver ungefär 70 token (beroende på hur många miljöer som testas i allmänhet). I vissa fall kan du dock behöva flera rapporter om inkorgsåtergivning för att kunna testa leveransen. Det kan därför ta fler tokens att slutföra flera kontroller.

## Få åtkomst till rapporten för inkorgsåtergivning {#accessing-the-inbox-rendering-report}

När du har skapat e-postleveransen och definierat innehållet samt målpopulationen följer du stegen nedan.

Mer information om hur du skapar, utformar och anger mål för en leverans finns på [sidan](defining-the-email-content.md).


1. Klicka på knappen **[!UICONTROL Inbox rendering]** överst i leveransfältet.

1. Välj **[!UICONTROL Analyze]** för att starta hämtningsprocessen.

   ![](assets/s_tn_inbox_rendering_button.png)

   Ett bevis skickas. Miniatyrbilderna för återgivning finns tillgängliga i det korrekturet några minuter efter att du skickat e-postmeddelandena. Mer information om hur du skickar korrektur finns i [det här avsnittet](preview-and-proof.md#send-proofs).

1. När du har skickat korrekturet visas det i leveranslistan. Dubbelklicka på den.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Gå till fliken **Inkorgsåtergivning** för korrekturet.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Återgivningsrapporten för inkorgen visas.

## Återgivningsrapport för inkorgen {#inbox-rendering-report}

I den här rapporten visas inkorgsåtergivningarna så som de visas för mottagaren. Återgivningarna kan variera beroende på hur mottagaren öppnar e-postleveransen: i en webbläsare, på en mobilenhet eller via ett e-postprogram.

I det övre avsnittet visas hur många meddelanden som tagits emot, oönskade meddelanden (skräppost), inte tagits emot eller väntar på att tas emot via en grafisk färgkodad representation.

![](assets/s_tn_inbox_rendering_summary.png){width="40%" align="left"}

Håll pekaren över diagrammet om du vill visa information om varje färg. Klicka på ett objekt i listan om du vill dölja eller visa motsvarande kategori i diagrammet.

Rapportens innehåll är uppdelat i tre delar: **[!UICONTROL Mobile]**, **[!UICONTROL Desktop]** och **[!UICONTROL Webmails]**. Bläddra nedåt i rapporten för att visa alla återgivningar grupperade i dessa tre kategorier.

![](assets/s_tn_inbox_rendering_report.png)

Klicka på motsvarande kort om du vill ha information om respektive rapport. Återgivningen visas för den valda mottagningsmetoden.

![](assets/s_tn_inbox_rendering_example.png)
