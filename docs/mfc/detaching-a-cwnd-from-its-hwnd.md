---
title: Odłączanie obiektu CWnd od jego właściwości HWND
ms.date: 11/04/2016
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: f7a6f97ba9f1dd3a928a5450c1a899ce09a4ac5f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446960"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odłączanie obiektu CWnd od jego właściwości HWND

Jeśli zachodzi potrzeba obejścia relacji obiektu`HWND`, MFC udostępnia kolejną `CWnd` funkcji członkowskiej, [Odłącz](../mfc/reference/cwnd-class.md#detach), która rozłącza obiekt C++ Window z okna systemu Windows. Zapobiega to zniszczeniu okna systemu Windows, gdy obiekt zostanie zniszczony.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Tworzenie okien](../mfc/creating-windows.md)

- [Sekwencja niszczenia okna](../mfc/window-destruction-sequence.md)

- [Przydzielanie i cofanie alokacji pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Zobacz też

[Obiekty okna](../mfc/window-objects.md)
