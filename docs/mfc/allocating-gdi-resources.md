---
title: Alokowanie zasobów GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 672a9a2ce103ae7f53f61ae955f77276eb1d2945
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509275"
---
# <a name="allocating-gdi-resources"></a>Alokowanie zasobów GDI

W tym artykule wyjaśniono, jak przydzielić i cofnąć alokację obiektów interfejsu urządzenia graficznego (GDI) systemu Windows, które są konieczne do drukowania.

> [!NOTE]
>  Aby uzyskać więcej informacji, zobacz [dokumentację zestawu GDI+ SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

Załóżmy, że należy użyć niektórych czcionek, piór lub innych obiektów GDI do drukowania, ale nie do wyświetlania ekranu. Ze względu na wymaganą pamięć można przydzielić te obiekty podczas uruchamiania aplikacji. Gdy aplikacja nie drukuje dokumentu, pamięć może być wymagana do innych celów. Lepiej jest przydzielać je podczas rozpoczynania drukowania, a następnie usuwać je po zakończeniu drukowania.

Aby przydzielić te obiekty GDI, Zastąp funkcję elementu członkowskiego [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) . Ta funkcja jest odpowiednio odpowiednia dla tego celu z dwóch powodów: struktura wywołuje tę funkcję raz na początku każdego zadania drukowania i, w przeciwieństwie do [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting), ta funkcja ma dostęp do obiektu przerzutowania reprezentującego urządzenie drukarki [](../mfc/reference/cdc-class.md) kierowc. Te obiekty można przechowywać do użycia podczas zadania drukowania przez definiowanie zmiennych składowych w klasie widoku, które wskazują na obiekty GDI (na przykład `CFont *` członkowie itd.).

Aby użyć utworzonych obiektów GDI, zaznacz je w kontekście urządzenia drukarki w funkcji składowej. [](../mfc/reference/cview-class.md#onprint) Jeśli potrzebujesz różnych obiektów GDI dla różnych stron dokumentu, możesz przeanalizować `m_nCurPage` element członkowski struktury [CPrintInfo](../mfc/reference/cprintinfo-structure.md) i odpowiednio wybrać obiekt GDI. Jeśli potrzebujesz obiektu GDI dla kilku kolejnych stron, system Windows wymaga, aby wybrać go do kontekstu urządzenia przy każdym `OnPrint` wywołaniu.

Aby cofnąć alokację tych obiektów GDI, Zastąp funkcję elementu członkowskiego [OnEndPrinting](../mfc/reference/cview-class.md#onendprinting) . Struktura wywołuje tę funkcję na końcu każdego zadania drukowania, co daje możliwość cofnięcia alokacji specyficznych dla drukowania obiektów GDI, zanim aplikacja powróci do innych zadań.

## <a name="see-also"></a>Zobacz także

[Drukowanie](../mfc/printing.md)<br/>
[Jak jest wykonywane drukowanie domyślne](../mfc/how-default-printing-is-done.md)
