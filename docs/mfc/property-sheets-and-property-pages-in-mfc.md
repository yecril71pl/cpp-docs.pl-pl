---
title: Arkusze właściwości i strony właściwości w MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f35282ce46aff3a3f0fba5fca505653cd892a392
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430050"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Arkusze właściwości i strony właściwości w MFC

Arkusz właściwości, znane również jako zakładki okna dialogowego, to okno dialogowe, który zawiera strony właściwości. Każdą stronę właściwości zależy od zasobu szablonu okna dialogowego i zawiera formanty. Ujęte na stronie z kartą u góry. Karta nazwy strony i wskazuje jej przeznaczenie. Użytkownicy, kliknij kartę w arkuszu właściwości, aby wybrać zestaw formantów.

Umożliwia grupowanie formantów w arkuszu właściwości w zrozumiałej zestawów stron. Arkusz właściwości zawartej zwykle znajduje się kilka kontrolek własne. Te mają zastosowanie do wszystkich stron.

Arkusze właściwości są oparte na klasie [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Strony właściwości są oparte na klasie [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Arkusz właściwości jest specjalnym rodzajem okno dialogowe, które jest zazwyczaj używana do modyfikowania atrybutów zewnętrznego obiektu, takie jak bieżące zaznaczenie w widoku. Arkusz właściwości ma trzy główne części: okno dialogowe zawierające jeden lub więcej stron właściwości wyświetlanych pojedynczo, a karta u góry każdej strony, które użytkownik klika, aby wybrać tę stronę. Arkusze właściwości są przydatne w sytuacjach, w którym znajduje się kilka grup podobne ustawienia lub opcje, aby zmienić. Arkusz właściwości grupy informacje w sposób łatwy do zrozumienia sposób.

> [!NOTE]
>  Gdy próbujesz Pokaż arkusz właściwości, za pomocą `CPropertySheet::DoModal`, system może wygenerować wyjątku pierwszej szansy. Ten wyjątek występuje, ponieważ system próbuje zmienić [Style okna ramowego](../mfc/reference/styles-used-by-mfc.md#window-styles) obiektu, zanim obiekt został utworzony. Aby uzyskać więcej informacji na temat tego wyjątku, a także sposobu uniknięcia wyświetlania go lub go obsłużyć, zobacz [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](../mfc/property-sheets-mfc.md)

