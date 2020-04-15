---
title: Alokowanie zasobów GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 149aefeade6f99c294b12bfb294cdf1addb9e5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370852"
---
# <a name="allocating-gdi-resources"></a>Alokowanie zasobów GDI

W tym artykule wyjaśniono, jak przydzielić i zmienić alokację obiektów interfejsu urządzenia graficznego systemu Windows (GDI) potrzebnych do drukowania.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [dokumentację GDI+ SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

Załóżmy, że do drukowania należy używać niektórych czcionek, piór lub innych obiektów GDI, ale nie do wyświetlania na ekranie. Ze względu na pamięć, które wymagają, jest nieefektywne przydzielić te obiekty podczas uruchamiania aplikacji. Gdy aplikacja nie drukuje dokumentu, ta pamięć może być potrzebna do innych celów. Lepiej jest przydzielić je po rozpoczęciu drukowania, a następnie usunąć je po zakończeniu drukowania.

Aby przydzielić te obiekty GDI, należy zastąpić [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) funkcji elementu członkowskiego. Ta funkcja jest dobrze nadaje się do tego celu z dwóch powodów: framework wywołuje tę funkcję raz na początku każdego zadania drukowania i, w przeciwieństwie do [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting), funkcja ta ma dostęp do obiektu [CDC](../mfc/reference/cdc-class.md) reprezentującego sterownik urządzenia drukarki. Obiekty te można przechowywać do użycia podczas zadania drukowania, definiując zmienne członkowskie w `CFont *` klasie widoku, które wskazują obiekty GDI (na przykład elementy członkowskie itd.).

Aby użyć utworzonych obiektów GDI, zaznacz je w kontekście urządzenia drukarki w funkcji elementu członkowskiego [OnPrint.](../mfc/reference/cview-class.md#onprint) Jeśli potrzebujesz różnych obiektów GDI dla różnych stron dokumentu, można zbadać `m_nCurPage` element członkowski [CPrintInfo](../mfc/reference/cprintinfo-structure.md) struktury i odpowiednio wybrać obiekt GDI. Jeśli potrzebujesz obiektu GDI dla kilku kolejnych stron, system Windows wymaga, aby wybrać go w kontekście urządzenia za każdym razem `OnPrint` jest wywoływana.

Aby zdyskcesizależnić te obiekty GDI, należy zastąpić [onendprinting](../mfc/reference/cview-class.md#onendprinting) funkcji elementu członkowskiego. Struktura wywołuje tę funkcję na końcu każdego zadania drukowania, co daje możliwość deallocate drukowania specyficzne dla obiektów GDI, zanim aplikacja powróci do innych zadań.

## <a name="see-also"></a>Zobacz też

[Drukowanie](../mfc/printing.md)<br/>
[Jak jest wykonywane drukowanie domyślne](../mfc/how-default-printing-is-done.md)
