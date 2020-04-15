---
title: Arkusze właściwości i strony właściwości w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 10fb34c79745e672d30dd2d3c3b97d457583f795
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371171"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Arkusze właściwości i strony właściwości w MFC

Arkusz właściwości, znany również jako okno dialogowe karty, to okno dialogowe zawierające strony właściwości. Każda strona właściwości jest oparta na zasobie szablonu okna dialogowego i zawiera kontrolki. Jest on ujęty na stronie z zakładką u góry. Karta nazywa stronę i wskazuje jej przeznaczenie. Użytkownicy klikają kartę w arkuszu właściwości, aby wybrać zestaw kontrolek.

Strony służy do grupowanie formantów w arkuszu właściwości w miarodajne zestawy. Arkusz właściwości zawarte zazwyczaj ma kilka formantów własnych. Dotyczą one wszystkich stron.

Arkusze właściwości są oparte na klasie [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Strony właściwości są oparte na klasie [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Arkusz właściwości jest specjalnym rodzajem okna dialogowego, które jest zwykle używane do modyfikowania atrybutów niektórych obiektów zewnętrznych, takich jak bieżące zaznaczenie w widoku. Arkusz właściwości zawiera trzy główne części: okno dialogowe zawierające, jedną lub więcej stron właściwości wyświetlanych po jednym naraz oraz kartę u góry każdej strony, którą użytkownik kliknie, aby zaznaczyć tę stronę. Arkusze właściwości są przydatne w sytuacjach, gdy masz kilka podobnych grup ustawień lub opcji do zmiany. Arkusz właściwości grupuje informacje w łatwo zrozumiały sposób.

> [!NOTE]
> Podczas próby wyświetlenia arkusza właściwości `CPropertySheet::DoModal`przy użyciu systemu może wygenerować wyjątek pierwszej szansy. Ten wyjątek występuje, ponieważ system próbuje zmienić [style okna](../mfc/reference/styles-used-by-mfc.md#window-styles) obiektu przed utworzeniem obiektu. Aby uzyskać więcej informacji na temat tego wyjątku, a także jak go uniknąć lub obsłużyć, zobacz [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](../mfc/property-sheets-mfc.md)
