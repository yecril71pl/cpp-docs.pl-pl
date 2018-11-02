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
ms.openlocfilehash: 4c4f9a96725e76ff25e21f7923e1b45a6e380ac5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612761"
---
# <a name="graphic-objects"></a>Obiekty graficzne

Windows oferuje szereg narzędzi do użycia w kontekstach urządzenia do rysowania. Zawiera pióra, aby rysować linie, pędzle do wypełnienia wnętrza i czcionek, aby rysować tekst. Biblioteka MFC zawiera klasy obiektów grafiki jest równoważne z narzędzi do rysowania w Windows. W poniższej tabeli przedstawiono dostępne klasy i równoważne grafiki Windows typ dojścia interface (GDI) urządzenia.

> [!NOTE]
>  Aby uzyskać więcej informacji, zobacz dokumentację zestawu SDK interfejsu GDI + w: [ https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).

W tym artykule opisano korzystanie z tych klas obiektów grafiki:

### <a name="classes-for-windows-gdi-objects"></a>Klasy Windows Obiekty GDI

|Class|Windows obsługi typu|
|-----------|-------------------------|
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
>  Klasa [CImage](../atl-mfc-shared/reference/cimage-class.md) zapewnia obsługę rozszerzonych mapy bitowej.

Każda klasa obiekt graficzny w bibliotece klas ma konstruktora, który pozwala na tworzenie obiektów graficznych tej klasy, które należy następnie zainicjować za pomocą funkcji tworzenia odpowiednie, takich jak `CreatePen`.

Każdej klasy obiektów grafiki w bibliotece klas zawiera operator rzutowania, który będzie rzutować obiekt MFC skojarzone uchwyt Windows. Wynikowy uchwyt jest prawidłowy, dopóki skojarzonego obiektu odłączy ją. Użyj obiektu `Detach` funkcja elementu członkowskiego, aby odłączyć uchwytu.

Poniższy kod rzutowania `CPen` obiektu do uchwytu Windows:

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Aby utworzyć obiekt graficzny w kontekście urządzenia

1. Zdefiniuj obiekt graficzny na ramce stosu. Inicjują obiekt za pomocą funkcji tworzenia określonego typu, takie jak `CreatePen`. Alternatywnie można zainicjować obiektu w konstruktorze. Zobacz Omówienie [tworzenia jedno- i dwuetapowa](../mfc/one-stage-and-two-stage-construction-of-objects.md), który zawiera przykładowy kod.

1. [Wybierz obiekt do bieżącego kontekstu urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md), zapisywanie stary obiekt graficzny, który został wybrany przed.

1. Po zakończeniu z bieżącym obiektem grafiki wybierz pozycję starego obiektu graficznego do kontekstu urządzenia, aby przywrócić jego stan.

1. Zezwalaj na przydzielone ramki obiektu graficznego do były automatycznie usuwane, gdy zakres jest został zakończony.

> [!NOTE]
>  Jeśli będzie używany obiekt graficzny wielokrotnie, można przydzielić ją jeden raz i zaznacz go do kontekstu urządzenia za każdym razem, gdy jest to konieczne. Pamiętaj usunąć takiego obiektu, gdy nie są już potrzebne.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Jedno- i dwuetapowa konstrukcja obiektów graficznych](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Przykład konstruowanie pióra w jedno i dwa etapy](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Wybieranie obiektu graficznego do kontekstu urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Konteksty urządzenia](../mfc/device-contexts.md)

## <a name="see-also"></a>Zobacz też

[Obiekty okna](../mfc/window-objects.md)

