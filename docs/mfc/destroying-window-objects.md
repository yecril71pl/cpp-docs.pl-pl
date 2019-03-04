---
title: Likwidowanie obiektów okien
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: f50d198f9868a70d25370f6c1399b66efaa5490b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289848"
---
# <a name="destroying-window-objects"></a>Likwidowanie obiektów okien

Należy uważać za pomocą okien podrzędnych do zniszczenia obiektu języka C++ w oknie po użytkownik z oknem. Jeśli te obiekty nie są niszczone, aplikacja nie zostanie odzyskana ich pamięci. Na szczęście szablon zarządza zniszczenie okna, a także tworzenie okien ramowych, widoków i okien dialogowych. Jeśli tworzysz dodatkowe okna, ponosisz odpowiedzialność za zniszczenie ich.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)

- [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)

- [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Ogólna sekwencja tworzenia okna](../mfc/general-window-creation-sequence.md)

- [Niszczenie okien ramowych](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Zobacz także

[Obiekty okna](../mfc/window-objects.md)
