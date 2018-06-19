---
title: Obiekty graficzne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- HRGN
- HFONT
- HBITMAP
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52b8c6c5b6d27bdf4ce4c9ad46a75c21b9f47333
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349785"
---
# <a name="graphic-objects"></a>Obiekty graficzne
System Windows udostępnia wiele narzędzi do użycia w kontekstach urządzenia do rysowania. Zapewnia on pióra do rysowania linii, pędzle wnętrza wypełnienia i czcionek do rysowania tekstu. MFC udostępnia klasy obiektów grafiki odpowiednikiem narzędzi do rysowania w systemie Windows. Poniższej tabeli przedstawiono dostępne klasy i równoważne grafiki Windows typ dojścia urządzenia interfejsu (GDI).  
  
> [!NOTE]
>  Aby uzyskać więcej informacji, zobacz dokumentację interfejsu GDI + SDK w: [ http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).  
  
 W tym artykule opisano korzystanie z tych klas obiektów grafiki:  
  
### <a name="classes-for-windows-gdi-objects"></a>Klasy dla systemu Windows Obiekty GDI  
  
|Class|Typ dojścia systemu Windows|  
|-----------|-------------------------|  
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|  
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|  
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|  
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|  
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|  
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|  
  
> [!NOTE]
>  Klasa [CImage](../atl-mfc-shared/reference/cimage-class.md) zapewnia obsługę rozszerzonych mapy bitowej.  
  
 Każdej klasy obiektów grafiki w bibliotece klas ma konstruktora, który pozwala na tworzenie obiektów graficznych dla tej klasy, które należy następnie zainicjować funkcją Utwórz odpowiednie, takich jak `CreatePen`.  
  
 Każdej klasy obiektów grafiki w bibliotece klas ma operator rzutowania, który będzie rzutować obiekt MFC skojarzone uchwytów okien. Wynikowa dojścia jest prawidłowa, dopóki skojarzonego obiektu odłącza go. Użyj obiektu **Detach** funkcji członkowskiej można odłączyć dojście.  
  
 Poniższy kod rzutowania `CPen` obiekt do obsługi systemu Windows:  
  
 [!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]  
  
#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Aby utworzyć obiekt graficzny kontekstu urządzenia  
  
1.  Należy zdefiniować obiektu graficznego w ramce stosu. Takie jak zainicjować obiektu za pomocą funkcji tworzenia określonego typu `CreatePen`. Można również zainicjować obiektu w konstruktorze. Zawiera omówienie [tworzenia jedno- i dwuetapowa](../mfc/one-stage-and-two-stage-construction-of-objects.md), który zawiera przykładowy kod.  
  
2.  [Wybierz obiekt do bieżącego kontekstu urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md), zapisywanie stary obiekt graficzny, który został wybrany przed.  
  
3.  Po zakończeniu bieżącego obiektu graficznego, wybierz starego obiektu graficznego do kontekstu urządzenia w celu przywrócenia jego stanu.  
  
4.  Zezwalaj na obiekt graficzny przydzielone ramki mają zostać usunięte automatycznie, gdy zakresu jest zakończone.  
  
> [!NOTE]
>  Jeśli będziesz używać obiektu graficznego wielokrotnie, można po jego przydziału i zaznacz go do kontekstu urządzenia za każdym razem, gdy jest to potrzebne. Pamiętaj usunąć takiego obiektu, gdy nie są już potrzebne.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Jedno- i dwuetapowa konstrukcja obiektów graficznych](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Przykład konstruowania pióra w jedno i dwóch etapach](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Wybieranie obiektu graficznego do kontekstu urządzenia](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [Konteksty urządzenia](../mfc/device-contexts.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty okna](../mfc/window-objects.md)

