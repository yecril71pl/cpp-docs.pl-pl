---
title: Odłączanie obiektu CWnd od jego właściwości HWND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWnd
dev_langs:
- C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c69703d8c528d82a696fc94be76ac4a569628b4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392650"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odłączanie obiektu CWnd od jego właściwości HWND

Jeśli potrzebujesz obejście obiekt -`HWND` relacji, biblioteka MFC zawiera inny `CWnd` funkcja elementu członkowskiego [Odłącz](../mfc/reference/cwnd-class.md#detach), który odłącza obiektu okna języka C++ z poziomu okna Windows. Zapobiega to zniszczenie okna Windows, kiedy niszczony jest obiekt destruktor.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien](../mfc/creating-windows.md)

- [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)

- [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Zobacz też

[Obiekty okna](../mfc/window-objects.md)

