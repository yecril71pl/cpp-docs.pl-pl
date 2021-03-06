---
title: Obiekty interfejsu użytkownika i identyfikatory poleceń
ms.date: 11/19/2018
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
ms.openlocfilehash: 54372facc51062add122c1db2e01e3081127512e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180618"
---
# <a name="user-interface-objects-and-command-ids"></a>Obiekty interfejsu użytkownika i identyfikatory poleceń

Elementy menu, przyciski paska narzędzi i klawisze skrótów są "obiekty interfejsu użytkownika" może generować poleceń. Każdy obiekt interfejsu użytkownika ma identyfikator. Obiekt interfejsu użytkownika można skojarzyć za pomocą polecenia, przypisując ten sam identyfikator obiektu i polecenia. Jak wyjaśniono w [wiadomości](../mfc/messages.md), polecenia są implementowane jako specjalne wiadomości. Na rysunku "Poleceń w ramach" poniżej pokazano, jak szablon zarządza poleceń. Gdy obiekt interfejsu użytkownika generuje polecenia, takie jak `ID_EDIT_CLEAR_ALL`, jednym z obiektów w aplikacji obsługuje polecenie — na rysunku poniżej obiektu dokumentu `OnEditClearAll` funkcja jest wywoływana za pomocą mapy komunikatów dokumentu.

![Polecenia w strukturze](../mfc/media/vc385p1.gif "polecenia w strukturze") <br/>
Polecenia w strukturze

Na rysunku "Polecenie aktualizacji w programie Framework" poniżej pokazano, jak MFC aktualizuje obiektów interfejsu użytkownika, takich jak elementy menu i przycisków na pasku narzędzi. Zanim rozwinięta menu lub podczas wykonywania pętli bezczynności w przypadku przycisków paska narzędzi, MFC kieruje polecenia update. Na poniższej ilustracji, obiekt dokumentu wywołuje jej procedura obsługi polecenia aktualizacji `OnUpdateEditClearAll`, aby włączyć lub wyłączyć obiektu interfejsu użytkownika.

![Polecenie aktualizacji w ramach](../mfc/media/vc385p2.png "polecenia aktualizacji w strukturze") <br/>
Polecenie aktualizacji w strukturze

## <a name="see-also"></a>Zobacz także

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)
