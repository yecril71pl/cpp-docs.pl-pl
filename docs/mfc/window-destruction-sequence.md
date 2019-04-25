---
title: Sekwencja likwidacji okna
ms.date: 11/04/2016
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
ms.openlocfilehash: d4592e6ac0077d6bc335b50f2d67b140402b4fe2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167650"
---
# <a name="window-destruction-sequence"></a>Sekwencja likwidacji okna

W ramach MFC, gdy użytkownik zamknie okno ramowe domyślny okna [OnClose](../mfc/reference/cwnd-class.md#onclose) obsługi zdarzeń wywołuje [destroywindow —](../mfc/reference/cwnd-class.md#destroywindow). Jest ostatni funkcja elementu członkowskiego, wywoływana, gdy okno Windows zostanie zniszczony [onncdestroy —](../mfc/reference/cwnd-class.md#onncdestroy), który wykonuje niektóre oczyszczania wywołuje [domyślne](../mfc/reference/cwnd-class.md#default) element członkowski funkcji do wykonywania oczyszczania Windows i na koniec wywołania Funkcja wirtualna elementu członkowskiego [postncdestroy —](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) implementacji `PostNcDestroy` usuwa obiekt okna języka C++.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)

- [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Zobacz także

[Niszczenie obiektów okien](../mfc/destroying-window-objects.md)
