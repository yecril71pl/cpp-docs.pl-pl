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
ms.openlocfilehash: 4abc2764abd0f31b83253f37b8cb459be638ae5a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508536"
---
# <a name="graphic-objects"></a>Obiekty graficzne

System Windows udostępnia różnorodne narzędzia do rysowania, które mogą być używane w kontekstach urządzeń. Udostępnia pióra do rysowania linii, pędzli do wypełnienia wnętrza oraz czcionek do rysowania tekstu. MFC oferuje klasy obiektów graficznych równoważne narzędziom do rysowania w systemie Windows. W poniższej tabeli przedstawiono dostępne klasy i równoważne typy uchwytów interfejsu urządzenia graficznego (GDI) systemu Windows.

> [!NOTE]
>  Aby uzyskać więcej informacji, zobacz [dokumentację zestawu GDI+ SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

W tym artykule opisano sposób użycia tych klas obiektów graficznych:

### <a name="classes-for-windows-gdi-objects"></a>Klasy dla obiektów GDI systemu Windows

|Class|Typ uchwytu systemu Windows|
|-----------|-------------------------|
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
>  Klasa [funkcji CImage](../atl-mfc-shared/reference/cimage-class.md) zapewnia obsługę ulepszonej mapy bitowej.

Każda klasa obiektu graficznego w bibliotece klas ma Konstruktor, który umożliwia tworzenie obiektów graficznych tej klasy, które należy następnie zainicjować przy użyciu odpowiedniej funkcji tworzenia, takiej jak `CreatePen`.

Każda klasa obiektu graficznego w bibliotece klas ma operator rzutowania, który będzie rzutować obiekt MFC do skojarzonego dojścia systemu Windows. Wyniki dojścia są prawidłowe do momentu odłączenia skojarzonego obiektu. Użyj funkcji `Detach` składowej obiektu, aby odłączyć dojście.

Poniższy kod rzutuje `CPen` obiekt do dojścia systemu Windows:

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Aby utworzyć obiekt graficzny w kontekście urządzenia

1. Zdefiniuj obiekt graficzny w ramce stosu. Zainicjuj obiekt za pomocą funkcji tworzenia specyficznej dla typu, takiej `CreatePen`jak. Alternatywnie można zainicjować obiekt w konstruktorze. Zapoznaj się z omówieniem [tworzenia jednego etapu i](../mfc/one-stage-and-two-stage-construction-of-objects.md)dwuetapowego, który zawiera przykładowy kod.

1. [Zaznacz obiekt w bieżącym kontekście urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md)i Zapisz stary obiekt graficzny, który został wybrany wcześniej.

1. Po zakończeniu z bieżącym obiektem graficznym, wybierz stary obiekt graficzny z powrotem do kontekstu urządzenia, aby przywrócić jego stan.

1. Zezwalaj na automatyczne usuwanie obiektu graficznego przydzieloną ramką po zakończeniu zakresu.

> [!NOTE]
>  Jeśli będziesz używać obiektu graficznego wielokrotnie, możesz przydzielić go raz i wybrać go w kontekście urządzenia zawsze wtedy, gdy jest to potrzebne. Pamiętaj, aby usunąć taki obiekt, gdy nie jest już potrzebny.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Jednoetapowa i dwuetapowa konstrukcja obiektów graficznych](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Przykład konstruowania pióra na jednym i dwóch etapach](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Wybieranie obiektu graficznego do kontekstu urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Konteksty urządzenia](../mfc/device-contexts.md)

## <a name="see-also"></a>Zobacz także

[Obiekty okna](../mfc/window-objects.md)
