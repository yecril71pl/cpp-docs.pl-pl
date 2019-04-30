---
title: Arkusze właściwości i strony właściwości w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: fa8ee3518ad2b32e0eace77f0961eb86ccde1822
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391377"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Arkusze właściwości i strony właściwości w MFC

Arkusz właściwości, znane również jako zakładki okna dialogowego, to okno dialogowe, który zawiera strony właściwości. Każdą stronę właściwości zależy od zasobu szablonu okna dialogowego i zawiera formanty. Ujęte na stronie z kartą u góry. Karta nazwy strony i wskazuje jej przeznaczenie. Użytkownicy, kliknij kartę w arkuszu właściwości, aby wybrać zestaw formantów.

Umożliwia grupowanie formantów w arkuszu właściwości w zrozumiałej zestawów stron. Arkusz właściwości zawartej zwykle znajduje się kilka kontrolek własne. Te mają zastosowanie do wszystkich stron.

Arkusze właściwości są oparte na klasie [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Strony właściwości są oparte na klasie [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Arkusz właściwości jest specjalnym rodzajem okno dialogowe, które jest zazwyczaj używana do modyfikowania atrybutów zewnętrznego obiektu, takie jak bieżące zaznaczenie w widoku. Arkusz właściwości ma trzy główne części: okno dialogowe zawierające jeden lub więcej stron właściwości wyświetlanych pojedynczo, a karta u góry każdej strony, które użytkownik klika, aby wybrać tę stronę. Arkusze właściwości są przydatne w sytuacjach, w którym znajduje się kilka grup podobne ustawienia lub opcje, aby zmienić. Arkusz właściwości grupy informacje w sposób łatwy do zrozumienia sposób.

> [!NOTE]
>  Gdy próbujesz Pokaż arkusz właściwości, za pomocą `CPropertySheet::DoModal`, system może wygenerować wyjątku pierwszej szansy. Ten wyjątek występuje, ponieważ system próbuje zmienić [Style okna ramowego](../mfc/reference/styles-used-by-mfc.md#window-styles) obiektu, zanim obiekt został utworzony. Aby uzyskać więcej informacji na temat tego wyjątku, a także sposobu uniknięcia wyświetlania go lub go obsłużyć, zobacz [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Zobacz także

[Arkusze właściwości](../mfc/property-sheets-mfc.md)
