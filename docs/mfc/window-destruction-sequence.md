---
title: Sekwencja likwidacji okna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04ef1aa9dadbbe965ab17945da681a0e1189c404
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446654"
---
# <a name="window-destruction-sequence"></a>Sekwencja likwidacji okna

W ramach MFC, gdy użytkownik zamknie okno ramowe domyślny okna [OnClose](../mfc/reference/cwnd-class.md#onclose) obsługi zdarzeń wywołuje [destroywindow —](../mfc/reference/cwnd-class.md#destroywindow). Jest ostatni funkcja elementu członkowskiego, wywoływana, gdy okno Windows zostanie zniszczony [onncdestroy —](../mfc/reference/cwnd-class.md#onncdestroy), który wykonuje niektóre oczyszczania wywołuje [domyślne](../mfc/reference/cwnd-class.md#default) element członkowski funkcji do wykonywania oczyszczania Windows i na koniec wywołania Funkcja wirtualna elementu członkowskiego [postncdestroy —](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) implementacji `PostNcDestroy` usuwa obiekt okna języka C++.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)

- [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Zobacz też

[Niszczenie obiektów okien](../mfc/destroying-window-objects.md)

