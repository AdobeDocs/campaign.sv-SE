---
title: Kom igång med behörigheter i Campaign v8
description: Lär dig steg för att definiera behörigheter i Campaign v8
feature: Permissions
role: User, Admin
level: Beginner
exl-id: 3d61abac-03df-42d3-a950-37e41a5a7756
source-git-commit: 290f4e9a0d13ef49caacb7a128ccc266bafd5e69
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 2%

---

# Kom igång med behörigheter{#gs-permissions}

Med Adobe Campaign kan du definiera och hantera de behörigheter som tilldelats användare. Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar:

* Tillgång till vissa funktioner
* Åtkomst till vissa data
* Åtkomst till vissa åtgärder (skapa, ändra, ta bort)

Dessa behörigheter definieras genom att användargruppbehörigheter, namngivna rättigheter och behörigheter kombineras i mappar.

I Adobe Campaign är **operatorer** och **operatorgrupper** representerar användarroller. En operator är en Adobe Campaign-användare som har behörighet att logga in och utföra åtgärder. Användare skapas i Admin Console. Behörigheterna gäller för användarprofiler eller användargrupper. Det finns två typer av behörigheter du kan ge:

* Du kan definiera grupper av operatorer som du tilldelar rättigheter till och sedan associera operatorerna med en eller flera grupper. På så sätt kan du återanvända behörigheter och göra användarprofilerna mer enhetliga. Det underlättar även hantering och underhåll av användarprofiler.
* Du kan tilldela namngivna rättigheter direkt till användare, i vissa fall för att överlagra rättigheterna som tilldelats via grupper.

## Viktiga steg för att bevilja behörigheter{#key-steps-permissions}

Som produktadministratör kan du bevilja behörigheter till användarna i din organisation. Behörigheter ges via Adobe Admin Console och Campaign Client Console. Användare loggar in på Adobe Campaign med sin Adobe ID. Lär dig hur du ansluter till Adobe Campaign i [den här sidan](connect.md).

Viktiga steg är:

* **Steg 1**: Definiera operatörsgrupper och tilldela dem behörigheter i Campaign Client Console. [Läs mer](manage-permissions.md#create-product-profile).
Observera att du även kan använda inbyggda operatorgrupper som utgångspunkt. Dessa standardgrupper, och deras behörigheter, listas i [det här avsnittet](manage-permissions.md#ootb-productprofiles).
* **Steg 2**: Skapa produktprofiler i Admin Console som matchar de grupperna. [Läs mer](manage-permissions.md#create-product-profile).
Du kan börja med de inbyggda produktprofilerna. [Läs mer](manage-permissions.md#ootb-productprofiles).
* **Steg 3**: Skapa användare i Admin Console och tilldela dem till en produktprofil. [Läs mer](manage-permissions.md#add-users).
* **Steg 4** (valfritt): Tilldela behörigheter för mappar. [Läs mer](manage-permissions.md#ootb-productprofiles).

## Om Admin Console{#gs-admin-console}

Adobe Admin Console är en central plats för att hantera berättiganden för Adobe i hela organisationen. Det är endast tillgängligt för produktadministratörer.

Använd Admin Console för att lägga till användare, skapa och tilldela produktprofiler (som är grupper med användarroller).

Lär dig hur du lägger till användare i [den här sidan](manage-permissions.md#add-users).

## Om produktprofiler{#ootb-product-profiles}

Produktprofiler är grupper av produkter och tjänster som du kan tilldela användare. I Adobe Experience Cloud baseras behörigheter på en produkts profil, inte på användaren. Du kan dock delegera administrativa behörigheter till specifika användare.

I Admin Console, alla Adobe Experience Cloud **produktprofil** för Campaign är associerat med en **operatorgrupp** i Campaign Client Console.

Lär dig hur du skapar och tilldelar produktprofiler i [den här sidan](manage-permissions.md#create-a-product-profile).

## Namngivna rättigheter för kampanj{#named-rights}

Som medlem i en produktprofil (dvs. operatörsgrupp) har en användare behörighet att utföra åtgärder som kallas namngivna rättigheter och har läs- och/eller skrivåtkomst till data. En operator kan vara medlem i flera operatorgrupper: behörigheter och åtkomstbehörigheter är additiva.

Läs mer om namngivna rättigheter i [det här avsnittet](manage-permissions.md#use-named-rights).
