---
title: Alokowanie zasobów GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: f0cadac5320a8c6e91eb3b1989d1fb3c0c701eb0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623232"
---
# <a name="allocating-gdi-resources"></a>Alokowanie zasobów GDI

W tym artykule wyjaśniono, jak przydzielić i cofnąć alokację obiektów interfejsu urządzenia graficznego (GDI) systemu Windows, które są konieczne do drukowania.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [dokumentację zestawu GDI+ SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

Załóżmy, że należy użyć niektórych czcionek, piór lub innych obiektów GDI do drukowania, ale nie do wyświetlania ekranu. Ze względu na wymaganą pamięć można przydzielić te obiekty podczas uruchamiania aplikacji. Gdy aplikacja nie drukuje dokumentu, pamięć może być wymagana do innych celów. Lepiej jest przydzielać je podczas rozpoczynania drukowania, a następnie usuwać je po zakończeniu drukowania.

Aby przydzielić te obiekty GDI, Zastąp funkcję elementu członkowskiego [OnBeginPrinting](reference/cview-class.md#onbeginprinting) . Ta funkcja jest odpowiednio odpowiednia dla tego celu z dwóch powodów: struktura wywołuje tę funkcję raz na początku każdego zadania drukowania i, w przeciwieństwie do [OnPreparePrinting](reference/cview-class.md#onprepareprinting), ta funkcja ma dostęp [do obiektu](reference/cdc-class.md) przerzutowania reprezentującego sterownik urządzenia drukarki. Te obiekty można przechowywać do użycia podczas zadania drukowania przez definiowanie zmiennych składowych w klasie widoku, które wskazują na obiekty GDI (na przykład członkowie itd `CFont *` .).

Aby użyć utworzonych obiektów GDI, zaznacz je w kontekście urządzenia drukarki w [funkcji składowej](reference/cview-class.md#onprint) . Jeśli potrzebujesz różnych obiektów GDI dla różnych stron dokumentu, możesz przeanalizować `m_nCurPage` element członkowski struktury [CPrintInfo](reference/cprintinfo-structure.md) i odpowiednio wybrać obiekt GDI. Jeśli potrzebujesz obiektu GDI dla kilku kolejnych stron, system Windows wymaga, aby wybrać go do kontekstu urządzenia przy każdym `OnPrint` wywołaniu.

Aby cofnąć alokację tych obiektów GDI, Zastąp funkcję elementu członkowskiego [OnEndPrinting](reference/cview-class.md#onendprinting) . Struktura wywołuje tę funkcję na końcu każdego zadania drukowania, co daje możliwość cofnięcia alokacji specyficznych dla drukowania obiektów GDI, zanim aplikacja powróci do innych zadań.

## <a name="see-also"></a>Zobacz też

[Drukowanie](printing.md)<br/>
[Jak jest wykonywane drukowanie domyślne](how-default-printing-is-done.md)
