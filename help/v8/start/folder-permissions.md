---
title: Bevilja och begränsa behörigheter för Campaign-mappar
description: Lär dig hur du tilldelar eller begränsar behörigheter till mappar
feature: Permissions
role: User, Admin
level: Beginner
source-git-commit: 857445d7d7d8080e479bdc596fb3162c2b4a2b6b
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Hantera mappbehörigheter{#manage-folder-permissions}

## Begränsa åtkomst till en mapp{#restrict-access-to-a-folder}

Använd behörigheter i mappar för att ordna och styra åtkomsten till Campaign-data.

Mapphantering beskrivs i [den här sidan](../audiences/folders-and-views.md).

Följ stegen nedan om du vill redigera behörigheter i en viss Campaign-mapp:

1. Högerklicka på mappen och välj **[!UICONTROL Properties...]**.
1. Bläddra till **[!UICONTROL Security]** för att visa behörigheter i den här mappen.

   ![](assets/folder-permissions.png)

* Till **auktorisera en grupp eller en operator** klickar du på **[!UICONTROL Add]** och välj den grupp eller operator som ska tilldelas behörigheter för den här mappen.
* Till **förbjuda en grupp eller en operatör**, klicka **[!UICONTROL Delete]** och välj den grupp eller operator som ska ta bort behörigheten för den här mappen.
* Till **markera de rättigheter som tilldelats en grupp eller en operator**, markerar gruppen eller operatorn, markerar de åtkomsträttigheter som du vill ge och avmarkerar de andra.

## Sprid behörigheter {#propagate-permissions}

Om du vill sprida auktoriseringar och åtkomsträttigheter väljer du **[!UICONTROL Propagate]** i mappegenskaperna.

Behörigheterna som definieras i det här fönstret kommer sedan att tillämpas på alla undermappar i den aktuella noden. Du kan alltid överlagra dessa behörigheter för var och en av undermapparna.

>[!NOTE]
>
>Avmarkerar **[!UICONTROL Propagate]** för en mapp inte rensar det för undermapparna: Du måste rensa det explicit för var och en av undermapparna.

## Ge åtkomst till alla operatorer {#grant-access-to-all-operators}

I **[!UICONTROL Security]** väljer du **[!UICONTROL System folder]** för att ge åtkomst till alla operatorer, oavsett deras behörigheter.

Om det här alternativet är avmarkerat måste du uttryckligen lägga till operatorn (eller deras grupp) i listan över auktoriseringar som de ska ha åtkomst till.
