---
title: Alokowanie i dealokowanie pamięci okna
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: 60f99c01c7a311c31602269b49efaf434d16827a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394705"
---
# <a name="allocating-and-deallocating-window-memory"></a>Alokowanie i dealokowanie pamięci okna

Nie używaj C++ **Usuń** operator można zniszczyć okna ramki lub widoku. Zamiast tego należy wywołać `CWnd` funkcja elementu członkowskiego `DestroyWindow`. Okna ramowe, dlatego powinna zostać przydzielona na stosie za pomocą operatora **nowe**. Należy zachować ostrożność podczas przydzielania okien ramowych na ramce stosu lub globalnie. Inne okna powinna zostać przydzielona w ramce stosu, jeśli to możliwe.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien](../mfc/creating-windows.md)

- [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)

- [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Zobacz także

[Niszczenie obiektów okien](../mfc/destroying-window-objects.md)
