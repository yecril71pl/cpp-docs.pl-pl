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
ms.openlocfilehash: 2e0484698654cd14f22a92be76a80f71c0f9adf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621843"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odłączanie obiektu CWnd od jego właściwości HWND

Jeśli zachodzi potrzeba obejścia `HWND` relacji między obiektem, MFC udostępnia kolejną `CWnd` funkcję członkowską, [Odłącz](reference/cwnd-class.md#detach), która rozłącza obiekt okna języka C++ z okna systemu Windows. Zapobiega to zniszczeniu okna systemu Windows, gdy obiekt zostanie zniszczony.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Tworzenie okien](creating-windows.md)

- [Sekwencja niszczenia okna](window-destruction-sequence.md)

- [Przydzielanie i cofanie alokacji pamięci okna](allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Zobacz też

[Obiekty okien](window-objects.md)
