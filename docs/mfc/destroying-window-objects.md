---
title: Niszczenie obiektów okien | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 704122f028cd744f0ce064f0153825830144d5b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401644"
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

