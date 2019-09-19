---
title: ON_UPDATE_COMMAND_UI — Makro
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 2a3f097a44e96fc470719ce636cc1b73e676fb38
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095843"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI — Makro

Aby połączyć obiekt interfejsu użytkownika z programem obsługi aktualizacji polecenia w obiekcie docelowym polecenia, Otwórz **Widok klasy**, a następnie kliknij prawym przyciskiem myszy klasę, do której zostanie dodana procedura obsługi, a następnie wybierz polecenie **Kreator klas**. Znajdź identyfikator obiektu użytkownika na liście po lewej stronie, a następnie wybierz **UPDATE_COMMAND_UI** w prawym okienku, a następnie kliknij przycisk **Dodaj procedurę obsługi**. Spowoduje to utworzenie funkcji obsługi w klasie i dodanie odpowiedniej pozycji do mapy komunikatów. Aby uzyskać więcej informacji [, zobacz Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md) . Możesz określić dodatkowe komunikaty do obsłużenia w okienku **komunikaty** .

Na przykład aby zaktualizować polecenie Wyczyść wszystko w menu Edycja programu, użyj **kreatora klas** , aby dodać wpis mapy komunikatów w wybranej klasie, deklarację funkcji dla programu obsługi aktualizacji polecenia o nazwie `OnUpdateEditClearAll` w deklaracji klasy i pustej Szablon funkcji w pliku implementacji klasy. Prototyp funkcji wygląda następująco:

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

Podobnie jak w przypadku wszystkich programów obsługi, deklaracja funkcji pokazuje słowo kluczowe **afx_msg** . Podobnie jak w przypadku wszystkich programów obsługi aktualizacji, przyjmuje jeden argument, wskaźnik do `CCmdUI` obiektu.

## <a name="see-also"></a>Zobacz także

[Instrukcje: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)
