---
title: Spåra personanpassade länkar
description: Lär dig spåra personliga länkar i e-postmeddelanden
feature: Personalization
role: User
level: Beginner
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 6e465ec24f72d0b30c4fc287da5d4c4bcaeda05b
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 1%

---

# Spåra personanpassade länkar {#tracking-personalized-links}

Länkarna i e-postinnehåll som innehåller personalisering måste spåras med specifik syntax.

Med JavaScript i e-postinnehåll (HTML eller Text) kan du generera och skicka dynamiskt innehåll till mottagarna, med två begränsningar:

* Skriptet kan inte komma åt databasen direkt (SQL-funktionen och API-funktionerna är inte tillgängliga),
* Adobe Campaign måste kunna identifiera URL:er så att länkar kan spåras.

## Instruktioner för förbehandling {#pre-processing-instructions}

Du kan lägga till specifika förbearbetningsinstruktioner för att skripta URL:en och spåra den. Dessa instruktioner måste skrivas i JavaScript och börja med `<%@`.

Exempel:

```
<%@ value object="myObject" xpath="@myField" %>
```

Den här instruktionen hämtar värdet för fältet `myField` från objektet `myObject`.

## URL-identifiering {#url-detection}

För spårningsidentifiering bäddar Adobe Campaign in [Tidy](https://www.html-tidy.org/) för att analysera HTML-källan och identifiera mönstret. Här listas alla URL:er för innehållet så att de kan spåras individuellt. Adobe Campaign använder Tidy igen för att ersätta URL:en (`http://myurl.com`) med en URL som pekar på Adobe Campaign omdirigeringsserver.

I det ursprungliga innehållet ersätts till exempel `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` för en viss mottagare med: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Var:

* &quot;h&quot; betyder HTML-innehåll (eller&quot;t&quot; för textinnehåll).
* 617791 är meddelande-ID:t / brustlogg-ID (hexadecimalt).
* 71ffa3 är NmsDelivery-ID (hexadecimalt).
* 71ffa8 är NmsTrackingUrl-ID (hexadecimalt).
* p1, p2 och så vidare, är alla parametrar som ska ersättas i URL:en.

### Exempel på icke-identifiering {#non-detection-example}

`<%= getURL("http://mynewsletter.com") %>` fungerar och skickar det faktiska innehållet på webbsidan via e-post till mottagarna. Men ingen länk spåras. Orsaken till detta är att MTA kör `"<%=getURL(..."` för varje e-postmeddelande innan det skickas. Det kan vara olika för varje mottagare, så Adobe Campaign kan inte känna till URL:erna för att spåra och tilldela dem ett tagg-ID.

När sidan som ska hämtas är densamma för alla mottagare är det bästa sättet att använda:

```
<%@ include url="http://mynewsletter.com" %>
```

I så fall hämtas sidan under analysen, innan spårningsidentifieringen. Det gör att Adobe Campaign kan identifiera länkarna, tilldela ett tagg-ID och spåra dem.

### Rekommenderat mönster {#recommended-pattern}

Efter bearbetning av `<%@`-instruktioner ska URL:en som ska spåras ha följande syntax:

```
<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">
```

>[!IMPORTANT]
>
>Alla andra mönster stöds inte av Adobe och bör undvikas för att förhindra eventuella säkerhetsbrister.

## URL-parametrar {#url-parameters}

För att säkerställa att personaliserade URL-adresser spåras korrekt måste du använda funktionen `escapeUrl()` eller lämplig kodningsmetod för parametrarna i dina URL-adresser.

**Exempel:**

```
<a href="http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>">Click here</a>
```

Detta säkerställer att den personaliserade parametern kodas och spåras korrekt av Adobe Campaign.

## Slinga med `<%@ foreach %>` {#foreach}

Instruktionen `<%@ foreach %>` gör att du kan iterera över arrayer med objekt som lästs in i leveransen för att spåra enskilda länkar som är relaterade till objekten.

### Syntax

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %>
  <!-- Content to repeat -->
<%@ end %>
```

**Parametrar:**

* **`object`**: Namnet på objektet som ska börja från (vanligtvis ett extra skriptobjekt, men kan vara en leverans)
* **`xpath`** (valfritt): XPath för samlingen som ska slingas. Standardvärdet är &quot;.&quot;, vilket innebär att objektet är arrayen som ska slingras på
* **`index`** (valfritt): Om xpath inte är &quot;.&quot; och objektet är en array, objektindex för objekt (börjar vid 0)
* **`item`** (valfritt): Namnet på ett nytt objekt som är tillgängligt med `<%@ value %>` inuti förgreningsslingan. Standard är länknamnet i schemat

### Exempel

Läs in en array med artiklar och en relationstabell mellan mottagare och artiklar i leveransegenskaperna/personaliseringen.

Du kan visa länkar till de här artiklarna med individuell spårning:

```
<%@ foreach object="articleList" item="article" %>
  <a href="http://example.com/article.jsp?id=<%@ value object="article" xpath="@id" %>">
    <%@ value object="article" xpath="@title" %>
  </a>
<%@ end %>
```

På så sätt kan Adobe Campaign spåra vilken specifik artikel varje mottagare klickade på, i stället för att bara spåra en artikellänk som användaren klickat på.

## Bästa praxis {#best-practices}

* Använd alltid funktionen `escapeUrl()` för dynamiska URL-parametrar
* Använd `<%@ foreach %>` när du behöver spåra enskilda objekt i samlingar
* Testa spårningen innan du skickar leveransen för att se till att alla länkar fungerar korrekt
* Kontrollera att personaliserade länkar är korrekt formaterade i leveransinnehållet
* Kontrollera spårningsloggarna för att bekräfta att personaliserade parametrar hämtas korrekt

## Relaterade ämnen {#related-topics}

* [Lär dig konfigurera spårade länkar](tracked-links.md)
* [Lär dig konfigurera alternativ för URL-spårning](url-tracking.md)
* [Lär dig hur du lägger till anpassningsfält](personalization-fields.md)

