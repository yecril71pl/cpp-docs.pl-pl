---
title: ON_UPDATE_COMMAND_UI — Makro
ms.date: 11/04/2016
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: d0487f6a69d144e46adab496f3fd21696b5b434b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594111"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI — Makro

Użyj **właściwości** okna, aby połączyć obiekt interfejsu użytkownika do obsługi aktualizacji poleceń w obiekcie docelowym polecenia. Zostanie automatycznie połączyć Identyfikatora obiektu interfejsu użytkownika do ON_UPDATE_COMMAND_UI — makro i Utwórz procedurę obsługi w obiekcie, który będzie obsługiwać aktualizacji. Zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md) Aby uzyskać więcej informacji.

Na przykład, aby zaktualizować wyczyść wszystkie polecenia w menu Edycja programu, użyj **właściwości** okno, aby dodać wpis mapy komunikatów w wybranej klasy deklarację funkcji obsługi aktualizacji poleceń o nazwie `OnUpdateEditClearAll` w klasie Deklaracja i szablonem funkcji empty w pliku implementacji klasy. Prototyp funkcji wygląda następująco:

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

Całej obsługi, pokazuje funkcji, takich jak **afx_msg** — słowo kluczowe. Jak zaktualizować wszystkie programy obsługi, zajmuje jeden argument, wskaźnik do `CCmdUI` obiektu.

## <a name="see-also"></a>Zobacz też

[Instrukcje: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

