---
title: Bevilja och begränsa behörigheter för Campaign-mappar
description: Lär dig hur du tilldelar eller begränsar behörigheter till mappar
feature: Permissions
role: User, Admin
level: Beginner
exl-id: 5bd8dbba-7a06-4737-bc5a-60354f91c709
source-git-commit: 0513b9f65e9431f5207b384a0e2d8c5aeb8e209f
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Hantera mappbehörigheter{#manage-folder-permissions}

## Begränsa åtkomst till en mapp{#restrict-access-to-a-folder}

Använd behörigheter i mappar för att ordna och styra åtkomsten till Campaign-data.

Mapphantering beskrivs på [den här sidan](../audiences/folders-and-views.md).

Följ stegen nedan om du vill redigera behörigheter i en viss Campaign-mapp:

1. Högerklicka på mappen och välj **[!UICONTROL Properties...]**.
1. Bläddra till fliken **[!UICONTROL Security]** om du vill visa behörigheter för den här mappen.

   ![](assets/folder-permissions.png)

* Om du vill **auktorisera en grupp eller en operator** klickar du på knappen **[!UICONTROL Add]** och väljer gruppen eller operatorn för att tilldela behörigheter för den här mappen.
* Om du vill **förbjuda en grupp eller en operator** klickar du på **[!UICONTROL Delete]** och väljer den grupp eller operator som du vill ta bort behörigheten för den här mappen.
* Om du vill **markera de rättigheter som tilldelats en grupp eller en operator** markerar du gruppen eller operatorn, markerar de rättigheter som du vill ge och avmarkerar de andra.

## Sprid behörigheter {#propagate-permissions}

Om du vill sprida auktoriseringar och åtkomsträttigheter väljer du alternativet **[!UICONTROL Propagate]** i mappegenskaperna.

Behörigheterna som definieras i det här fönstret kommer sedan att tillämpas på alla undermappar i den aktuella noden. Du kan alltid överlagra dessa behörigheter för var och en av undermapparna.

>[!NOTE]
>
>Om du avmarkerar alternativet **[!UICONTROL Propagate]** för en mapp tas det inte bort för undermapparna: du måste avmarkera det explicit för var och en av undermapparna.

## Ge åtkomst till alla operatorer {#grant-access-to-all-operators}

På fliken **[!UICONTROL Security]** väljer du **[!UICONTROL System folder]** för att tillåta åtkomst till alla operatorer, oavsett deras behörigheter.

Om det här alternativet är avmarkerat måste du uttryckligen lägga till operatorn (eller deras grupp) i listan över auktoriseringar som de ska ha åtkomst till.
