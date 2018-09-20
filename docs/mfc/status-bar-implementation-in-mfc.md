---
title: Implementacja paska stanu w MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COldStatusBar
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e593227daabb2d2c25d593cfb58ef23ba7855be7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436718"
---
# <a name="status-bar-implementation-in-mfc"></a>Implementacja paska stanu w MFC

A [CStatusBar](../mfc/reference/cstatusbar-class.md) obiekt jest pasek sterowania z wiersza tekstu wyjściowego okienka. Okienka danych wyjściowych są często używane jako wiersz wiadomości, a wskaźniki stanu. Przykłady obejmują linie komunikat pomocy menu krótko opisano wybrane polecenie i wskaźniki, pokazujące stan SCROLL LOCK, NUM LOCK i innych kluczy.

Począwszy od wersji 4.0 MFC, paski stanu są implementowane za pomocą klasy [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), która hermetyzuje stan paska wspólnej kontroli. W celu zapewnienia zgodności z poprzednimi wersjami MFC zachowuje starsze implementacja paska stanu w klasie `COldStatusBar`. W tym artykule opisano dokumentacji dla wcześniejszych wersji MFC `COldStatusBar` w obszarze `CStatusBar`.

[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), funkcją składową nowe 4.0 MFC, pozwala na korzystanie z zalet obsługi Windows formantu typowego paska dostosowań i dodatkowe funkcje stanu. `CStatusBar` Funkcje Członkowskie zapewniają większość funkcji wspólnych formantów Windows; Jednak jeśli wywołasz `GetStatusBarCtrl`, Twoje paski stanu można nadać jeszcze więcej właściwości paska stanu. Gdy wywołujesz `GetStatusBarCtrl`, to zostanie zwrócona odwołanie do `CStatusBarCtrl` obiektu. Za pomocą tego odwołania do manipulowania formantu paska stanu.

Na poniższej ilustracji przedstawiono pasek stanu, który wyświetla kilka wskaźniki.

![Pasek stanu](../mfc/media/vc37dy1.gif "vc37dy1") paska stanu

Pasek narzędzi, np. obiekt pasek stanu jest osadzony w jej nadrzędnej ramki okna i jest tworzony automatycznie, gdy okno ramowe jest konstruowany. Na pasku stanu, podobnie jak wszystkie paski sterowania, jest niszczony, automatycznie także kiedy niszczony jest nadrzędnej ramki.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Aktualizowanie tekstu w okienku paska stanu](../mfc/updating-the-text-of-a-status-bar-pane.md)

- Klasy MFC [CStatusBar](../mfc/reference/cstatusbar-class.md) i [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [Paski sterowania](../mfc/control-bars.md)

- [Paski dialogowe](../mfc/dialog-bars.md)

- [Paski narzędzi (MFC — implementacja paska narzędzi)](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>Zobacz też

[Paski stanu](../mfc/status-bars.md)

