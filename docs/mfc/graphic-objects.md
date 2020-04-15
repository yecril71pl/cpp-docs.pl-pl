---
title: Obiekty graficzne
ms.date: 11/04/2016
f1_keywords:
- HRGN
- HFONT
- HBITMAP
helpviewer_keywords:
- CRgn class [MFC], HRGN handle type
- HPEN [MFC]
- objects [MFC], graphic
- palettes [MFC], creating in device context
- pens [MFC], creating in device context
- bitmaps [MFC], creating in device contexts
- palette objects [MFC]
- memory [MFC], display contexts
- MFC, graphic objects
- regions [MFC], creating in device context
- CPen class [MFC], HPEN handle type
- GDI objects [MFC]
- HRGN [MFC]
- graphic objects [MFC]
- GDI objects [MFC], graphic-object classes
- CFont class [MFC], HFONT handle type
- HFONT and class CFont [MFC]
- HBITMAP and class CBitmap [MFC]
- fonts [MFC], creating in device context
- images [MFC], graphic objects [MFC]
- CBitmap class [MFC], HBITMAP handle type
- HPALETTE and class CPalette [MFC]
- CBrush class [MFC], HBRUSH handle type
- objects [MFC], graphic objects
- drawing [MFC], in device contexts
- device contexts [MFC], graphic objects [MFC]
- brushes [MFC], creating in device context
- region objects [MFC]
- pen objects [MFC]
- GDI [MFC], graphic-object classes
- graphic objects [MFC], creating in device context
- HBRUSH and class CBrush [MFC]
- painting and device context [MFC]
- CPalette class [MFC], HPALETTE handle type
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
ms.openlocfilehash: 0201e53114b71c02877762f89cc65fc46d17700c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370527"
---
# <a name="graphic-objects"></a>Obiekty graficzne

System Windows udostępnia wiele narzędzi do rysowania do użycia w kontekstach urządzeń. Zapewnia pióra do rysowania linii, pędzle do wypełniania wnętrz i czcionki do rysowania tekstu. MFC udostępnia klasy obiektów graficznych równoważne narzędziom do rysowania w systemie Windows. W poniższej tabeli przedstawiono dostępne klasy i równoważne typy uchwytów interfejsu urządzenia graficznego systemu Windows (GDI).

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [dokumentację GDI+ SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

W tym artykule wyjaśniono użycie tych klas obiektów graficznych:

### <a name="classes-for-windows-gdi-objects"></a>Klasy obiektów GDI systemu Windows

|Klasa|Typ uchwytu systemu Windows|
|-----------|-------------------------|
|[Cpen](../mfc/reference/cpen-class.md)|`HPEN`|
|[Cbrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[Cfont](../mfc/reference/cfont-class.md)|**HFONT ( HFONT )**|
|[Cbitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[Cpalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[Crgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
> Klasa [CImage](../atl-mfc-shared/reference/cimage-class.md) zapewnia rozszerzoną obsługę mapy bitowej.

Każda klasa obiektów graficznych w bibliotece klas ma konstruktor, który umożliwia tworzenie obiektów graficznych tej klasy, `CreatePen`które następnie należy zainicjować za pomocą odpowiedniej funkcji tworzenia, takiej jak .

Każda klasa obiektów graficznych w bibliotece klas ma operator rzutowany, który będzie rzutował obiekt MFC do skojarzonego uchwytu systemu Windows. Wynikowy uchwyt jest prawidłowy, dopóki skojarzony obiekt go nie odłączy. Użyj funkcji `Detach` elementu członkowskiego obiektu, aby odłączyć uchwyt.

Następujący kod rzutuje `CPen` obiekt do dojścia systemu Windows:

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Aby utworzyć obiekt graficzny w kontekście urządzenia

1. Zdefiniuj obiekt graficzny w ramce stosu. Inicjuj obiekt za pomocą funkcji `CreatePen`tworzenia specyficznej dla typu, takiej jak . Alternatywnie zainicjować obiekt w konstruktorze. Zobacz omówienie [jednoetapowego i dwuetapowego tworzenia](../mfc/one-stage-and-two-stage-construction-of-objects.md), który zawiera przykładowy kod.

1. [Zaznacz obiekt w bieżącym kontekście urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md), zapisując stary obiekt graficzny, który został wybrany wcześniej.

1. Po zakończeniu pracy z bieżącym obiektem graficznym zaznacz stary obiekt graficzny z powrotem w kontekście urządzenia, aby przywrócić jego stan.

1. Zezwalaj na automatyczne usunięcie obiektu graficznego przydzielonego ramką po zamknięciu zakresu.

> [!NOTE]
> Jeśli obiekt graficzny będzie wielokrotnie używany, możesz go przydzielić raz i wybrać w kontekście urządzenia za każdym razem, gdy jest potrzebny. Pamiętaj, aby usunąć taki obiekt, gdy nie jest już potrzebny.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Jedno- i dwuetapowa konstrukcja obiektów graficznych](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Przykład konstruowania pióra w jednym i dwóch etapach](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Wybieranie obiektu graficznego do kontekstu urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Konteksty urządzeń](../mfc/device-contexts.md)

## <a name="see-also"></a>Zobacz też

[Obiekty okien](../mfc/window-objects.md)
