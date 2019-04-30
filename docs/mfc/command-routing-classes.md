---
title: Klasy routingu poleceń
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: 264e931ba0468cdc44f27c55e5d259948c5392b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406057"
---
# <a name="command-routing-classes"></a>Klasy routingu poleceń

Jako użytkownik wchodzi w interakcję z aplikacją, wybierając menu i przycisków paska sterowania myszą, aplikacja wysyła komunikaty z obiektu dotyczy interfejsu użytkownika do odpowiedniego obiektu elemencie docelowym polecenia. Elemencie docelowym polecenia klasy pochodne `CCmdTarget` obejmują [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), i klas pochodnych je. Platforma obsługuje polecenie automatycznego routingu, aby polecenia mogą być obsługiwane przez najbardziej odpowiedni obiekt aktualnie aktywne w aplikacji.

Obiekt klasy `CCmdUI` jest przekazywany do polecenia update swoje cele poleceń interfejsu użytkownika ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) programów obsługi, aby możliwe było zaktualizować stan interfejsu użytkownika dla określonego polecenia (na przykład w celu wyboru lub usuń Sprawdzanie z elementów menu). Wywołanie funkcji elementu członkowskiego `CCmdUI` obiekt, aby zaktualizować stan obiektów interfejsu użytkownika. Ten proces jest taki sam, czy obiekt interfejsu użytkownika skojarzony z określonym poleceniem jest element menu lub przycisku lub obu.

[CCmdTarget](../mfc/reference/ccmdtarget-class.md)<br/>
Służy jako klasa bazowa dla wszystkich klas obiektów, które może odbierać i odpowiadać na komunikaty.

[CCmdUI](../mfc/reference/ccmdui-class.md)<br/>
Udostępnia interfejs programistyczny dla aktualizowanie obiektów interfejsu użytkownika, np. w menu i przycisków paska sterowania. Obiekt docelowy polecenia umożliwia, wyłączenie, sprawdza i/lub czyści obiekt interfejsu użytkownika z tym obiektem.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
