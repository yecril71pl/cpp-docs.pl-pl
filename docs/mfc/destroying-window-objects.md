---
title: Niszczenie obiektów okien
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 363ff2a4cee48b1660de87714d73c93e795017cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488815"
---
# <a name="destroying-window-objects"></a>Niszczenie obiektów okien

Należy uważać za pomocą okien podrzędnych do zniszczenia obiektu języka C++ w oknie po użytkownik z oknem. Jeśli te obiekty nie są niszczone, aplikacja nie zostanie odzyskana ich pamięci. Na szczęście szablon zarządza zniszczenie okna, a także tworzenie okien ramowych, widoków i okien dialogowych. Jeśli tworzysz dodatkowe okna, ponosisz odpowiedzialność za zniszczenie ich.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)

- [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)

- [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Ogólna sekwencja tworzenia okna](../mfc/general-window-creation-sequence.md)

- [Niszczenie okien ramowych](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Zobacz też

[Obiekty okna](../mfc/window-objects.md)

