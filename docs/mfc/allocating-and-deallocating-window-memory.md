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
ms.openlocfilehash: 33d471b41c8f1fd670e25626049ecd9b06b034e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195203"
---
# <a name="allocating-and-deallocating-window-memory"></a>Alokowanie i dealokowanie pamięci okna

Nie używaj operatora C++, **`delete`** aby zniszczyć okno lub widok ramki. Zamiast tego należy wywołać `CWnd` funkcję członkowską `DestroyWindow` . W związku z tym należy przydzielyć okna ramowe do sterty z operatorem **`new`** . Należy zachować ostrożność podczas alokowania okien ramowych w ramce stosu lub globalnie. W miarę możliwości można przydzielać inne okna na ramkę stosu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Tworzenie okien](creating-windows.md)

- [Sekwencja niszczenia okna](window-destruction-sequence.md)

- [Odłączanie obiektu CWnd od jego właściwości HWND](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Zobacz także

[Niszczenie obiektów okien](destroying-window-objects.md)
