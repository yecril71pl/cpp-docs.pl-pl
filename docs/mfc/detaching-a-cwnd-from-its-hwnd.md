---
title: Odłączanie obiektu CWnd od jego właściwości HWND
ms.date: 11/04/2016
f1_keywords:
- CWnd
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: 259af94958f88643e9c3ce725b25c4e92cc38226
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271128"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odłączanie obiektu CWnd od jego właściwości HWND

Jeśli potrzebujesz obejście obiekt -`HWND` relacji, biblioteka MFC zawiera inny `CWnd` funkcja elementu członkowskiego [Odłącz](../mfc/reference/cwnd-class.md#detach), który odłącza obiektu okna języka C++ z poziomu okna Windows. Zapobiega to zniszczenie okna Windows, kiedy niszczony jest obiekt destruktor.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien](../mfc/creating-windows.md)

- [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)

- [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Zobacz także

[Obiekty okna](../mfc/window-objects.md)
