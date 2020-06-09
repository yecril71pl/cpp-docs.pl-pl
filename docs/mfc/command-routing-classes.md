---
title: Klasy routingu poleceń
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: d7ff275d373cf50ab8ebe52ed454bd25cd473e11
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624824"
---
# <a name="command-routing-classes"></a>Klasy routingu poleceń

Gdy użytkownik współdziała z aplikacją, wybierając menu lub przyciski paska sterowania z myszą, aplikacja wysyła komunikaty z obiektu interfejsu użytkownika, których to dotyczy, do odpowiedniego obiektu docelowego polecenia. Klasy docelowe poleceń, z `CCmdTarget` których pochodzą [CWinApp](reference/cwinapp-class.md), [CWnd](reference/cwnd-class.md), [CDocTemplate](reference/cdoctemplate-class.md), [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md)i klasy pochodne. Platforma obsługuje automatyczne kierowanie poleceń, aby polecenia mogły być obsługiwane przez najbardziej odpowiedni obiekt aktualnie aktywny w aplikacji.

Obiekt klasy `CCmdUI` jest przesyłany do programów obsługi interfejsu użytkownika poleceń aktualizacji "[ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)", aby umożliwić zaktualizowanie stanu interfejsu użytkownika dla określonego polecenia (na przykład w celu sprawdzenia lub usunięcia zaznaczenia z elementów menu). Wywołujesz funkcje członkowskie obiektu, `CCmdUI` Aby zaktualizować stan obiektu interfejsu użytkownika. Ten proces jest taki sam, niezależnie od tego, czy obiekt interfejsu użytkownika skojarzony z określonym poleceniem jest elementem menu, czy przyciskiem.

[CCmdTarget](reference/ccmdtarget-class.md)<br/>
Służy jako klasa bazowa dla wszystkich klas obiektów, które mogą odbierać wiadomości i odpowiadać na nie.

[CCmdUI](reference/ccmdui-class.md)<br/>
Udostępnia interfejs programistyczny do aktualizowania obiektów interfejsu użytkownika, takich jak elementy menu lub przyciski paska sterowania. Obiekt docelowy polecenia umożliwia, wyłącza, sprawdza i/lub czyści obiekt interfejsu użytkownika z tym obiektem.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
