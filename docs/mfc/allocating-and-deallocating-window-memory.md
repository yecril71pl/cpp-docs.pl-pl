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
ms.openlocfilehash: 02546559183d0e14973bc2e5ccb26a4570a39b1e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623269"
---
# <a name="allocating-and-deallocating-window-memory"></a>Alokowanie i dealokowanie pamięci okna

Nie używaj operatora **delete** języka C++, aby zniszczyć okno lub widok ramki. Zamiast tego należy wywołać `CWnd` funkcję członkowską `DestroyWindow` . W związku z tym, powinny być przydzielane na stercie z użyciem operatora **New**. Należy zachować ostrożność podczas alokowania okien ramowych w ramce stosu lub globalnie. W miarę możliwości można przydzielać inne okna na ramkę stosu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Tworzenie okien](creating-windows.md)

- [Sekwencja niszczenia okna](window-destruction-sequence.md)

- [Odłączanie elementu CWnd od jego elementu HWND](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Zobacz też

[Likwidowanie obiektów okien](destroying-window-objects.md)
